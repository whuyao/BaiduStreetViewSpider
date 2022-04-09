# 百度街景爬虫

　　该项目用于根据指定的wgs84经纬度坐标获取对应位置的百度地图的街景图像。

## 内容

该文件夹主要包含一个用于获取街景的脚本文件和一个输出目录。

+ baiduStreetViewSpider.py：该脚本为获取街景的主要程序，输入为存有wgs84坐标系下经纬度信息的csv文件。

+ dir文件夹：存有脚本的输入文件以及输出的街景图像和爬取失败的信息。该文件夹主要包括以下内容：
  1. point_coordinate_50、point_coordinate_100与point_coordinate_intersect分别为缺失街景的路网50米加密点、100米加密点以及道路交点的经纬度信息。
  2. error文件为对应的爬取失败的点的信息。
  3. images文件夹下存放爬取成功的街景图像。

## 环境依赖

　　该脚本在python3环境下运行，需要导入re、os、json、requests、time、glob、csv、traceback这几种库，其中除了requests库是第三方库以外，其余均是python内置模块，无需额外安装。

　　关于requests库，版本为2.26.0，安装方式为：

``` python
  pip install requests
```

## 注意事项

1. 利用arcgis或QGIS提取需要街景数据的经纬度信息，以csv文件存储。
2. 代码第102行read_fn变量值为存有经纬度信息的csv文件名。
3. 第103行error_fn变量值为保存爬取失败的信息文件名。
4. 代码第105行wgs_x、wgs_y分别为存储经纬度的列表，其中data变量的第二个维度代表csv文件中经纬度所在的列索引。
5. 若报错提示为连接的主机没有反应，则需要将第158行的睡眠时间适当延长，为3的倍数即可。
6. 街景文件命名方式为：经度 纬度 角度 俯仰角，若爬取成功，每个点会爬取0度、90度、180度和270度的街景图。
7. wgs84坐标在程序中会利用wgs2bd09mc函数自动转化为百度的坐标，无需额外操作。

## 参考文献
[1] Yao, Y., Liang, Z., Yuan, Z., Liu, P., Bie, Y., Zhang, J., ... & Guan, Q. (2019). A human-machine adversarial scoring framework for urban perception assessment using street-view images. International Journal of Geographical Information Science, 33(12), 2363-2384.

[2] Helbich, M., Yao, Y., Liu, Y., Zhang, J., Liu, P., & Wang, R. (2019). Using deep learning to examine street view green and blue spaces and their associations with geriatric depression in Beijing, China. Environment international, 126, 107-117.

[3] Yao, Y., Wang, J., Hong, Y., Qian, C., Guan, Q., Liang, X., ... & Zhang, J. (2021). Discovering the homogeneous geographic domain of human perceptions from street view images. Landscape and Urban Planning, 212, 104125.

[4] Yao, Y., Zhang, J., Qian, C., Wang, Y., Ren, S., Yuan, Z., & Guan, Q. (2021). Delineating urban job-housing patterns at a parcel scale with street view imagery. International Journal of Geographical Information Science, 35(10), 1927-1950.




# Baidu Street View Spider

This project is used to get the street view image of Baidu map at the corresponding location based on the specified wgs84 latitude and longitude coordinates.

## Contents

This folder mainly contains a script file for getting street view and an output directory.

+ baiduStreetViewSpider.py: this script is the main program to get the street view, the input is a csv file with the latitude and longitude information in wgs84 coordinate system.

+ dir folder: the input files of the script and the output street view images and crawl failure information. This folder contains mainly the following files:
  1. point_coordinate_50, point_coordinate_100 and point_coordinate_intersect are the latitude and longitude information of the missing 50m encrypted points, 100m encrypted points and road intersections of the road network respectively.
  2. the error file is the information of the corresponding failed points.
  3. images folder will save the images of successfully crawled street view.

## Environment dependency

　　The script runs in python3 environment, and needs to import re, os, json, requests, time, glob, csv, traceback libraries, among which all are built-in python modules except requests library which is a third-party library, no additional installation is needed.

　　Regarding the requests library, the version is 2.26.0, and the installation method is

``` python
  pip install requests
```

## Tips

1. Using arcgis or QGIS to extract the latitude and longitude information of street view data, and store it in csv file. 2.
2. line 102 contains the read_fn variable, which is the name of the csv file with the latitude and longitude information.  
3. error_fn variable (line 103) is the filename of the csv file with the latitude and longitude information.
4. line 105 of the code wgs_x and wgs_y are the list of latitude and longitude respectively, where the second dimension of the data variable represents the column index of the latitude and longitude in the csv file.
5. If the error is reported as no response from the connected host, you need to extend the sleep time in line 158 to a multiple of 3 appropriately.
6. the street view file is named as follows: longitude latitude angle pitch angle, if the crawl is successful, each point will crawl 0 degree, 90 degree, 180 degree and 270 degree street view.
7. wgs84 coordinates will be automatically converted to Baidu's coordinates in the program using the wgs2bd09mc function, no additional operation is needed.

## References
[1] Yao, Y., Liang, Z., Yuan, Z., Liu, P., Bie, Y., Zhang, J., ... & Guan, Q. (2019). A human-machine adversarial scoring framework for urban perception assessment using street-view images. International Journal of Geographical Information Science, 33(12), 2363-2384.

[2] Helbich, M., Yao, Y., Liu, Y., Zhang, J., Liu, P., & Wang, R. (2019). Using deep learning to examine street view green and blue spaces and their associations with geriatric depression in Beijing, China. Environment international, 126, 107-117.

[3] Yao, Y., Wang, J., Hong, Y., Qian, C., Guan, Q., Liang, X., ... & Zhang, J. (2021). Discovering the homogeneous geographic domain of human perceptions from street view images. Landscape and Urban Planning, 212, 104125.

[4] Yao, Y., Zhang, J., Qian, C., Wang, Y., Ren, S., Yuan, Z., & Guan, Q. (2021). Delineating urban job-housing patterns at a parcel scale with street view imagery. International Journal of Geographical Information Science, 35(10), 1927-1950.

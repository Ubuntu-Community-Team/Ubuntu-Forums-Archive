---
title: "Difference between Ubuntu Printing and Linux Mint Printing"
date: 2015-10-22
forum: Desktop Environments
---

### Post by davidvan on 2015-10-22
Hello everyone, 

I'm trying to understand the difference between Ubuntu's Print configuration and Linux Mint's Print Configuration. 
I have a canon MP4700 series wired Network printer. I followed the instructions to install the Canon Software:

1 Have GDebi installed
2 Right click on "cndrvcups-common_2.90-1_amd64.deb" package. Select "Open With GDebi Package Installer"
3 Click on "Install Package"
4 When installation is finished click on "Close" button. Close the "Package Installer - cndrvups-common" window
5 Right click on "cndrvcups-ufr2-us_2.90-1_amd64.deb" package. Select "Open With GDebi Package Installer" option
6 Click on "Install Package"
7 When installation is finished click on "Close" button. Close the "Package Installer - cndrvups-ufr2-us" window
   Note: To satisfy all dependencies it is important to first install cndrvcups-common_2.90-1_amd64.deb" then second install "cndrvcups-ufr2-us_2.90-1_amd64.deb".
8 Using your favourite internet browser such as*?IceWeasel go to*[http://localhost:631/admin](http://localhost:631/admin)
9 Click on "Add Printer" button
10 If the browser asks for your username and password enter your Debian Root username and password
11 Under "Local Printers" select the appropriate printer model
12 Click on "Continue" button
13 On the next page leave default settings as is for "Name", "Description", "Location". Unless you know what you're doing.
14 Click on "Continue" button
15 On the next page, under "Model" the appropriate printer model should be automatically selected. If not select the appropriate model.
16 Click on "Add Printer" button
17 On the next page under "General" section select your preferred settings. If unsure leave default settings.


When I follow this process under Linux Mint this works. Under Ubuntu the printing hangs. 

Any help would be appreciated. 

Thanks
Dave

---


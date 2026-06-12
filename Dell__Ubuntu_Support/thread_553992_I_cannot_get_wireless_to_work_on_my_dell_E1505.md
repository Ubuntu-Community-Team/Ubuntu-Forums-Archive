---
title: "I cannot get wireless to work on my dell E1505"
date: 2007-09-18
forum: Dell  Ubuntu Support
---

### Post by mrorellana on 2007-09-18
hello everyone i am new to linux and ive been trying to get wireless internet to work. i tried going to different forums and tried learning from other peoples questions. unfortunately i have had no luck so i decided to start fresh and reinstall ubuntu 7.04. 
so if someone can help me out and tell me the steps to making it work. im sorry if i sound a little desperate but ive worked on it for hours and i cannot get it to work.
i have a dell E1505 with a dell wireless 1390 wlan mini-pci card made by broadcom 

thanks

---

### Post by girishkolari on 2007-09-18
I had problem in wireless with Dell Inspiron 640m.
You can find solution what I found here in the link [http://girishkolari.blogspot.com/2007/08/ndiswrapper-for-dell-inspiron-640m.html]("http://girishkolari.blogspot.com/2007/08/ndiswrapper-for-dell-inspiron-640m.html")

---

### Post by Ek0nomik on 2007-09-19
Hopefully this will offer some insight:  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by cool_arrow on 2007-09-19
I'll bet you have a broadcom chipset.  Use ndiswrapper and this driver:
[http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=LATITUDE%20D510&servicetag=&os=WW1&osl=RU&deviceid=8043&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=LATITUDE%20D510&servicetag=&os=WW1&osl=RU&deviceid=8043&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136)

This worked for my Dell Vostro 1000 which has the 1390 chipset.  One thing to be aware of: if your computer has a function key combo which toggles the wifi off and on make sure that this is on.  On my machine I discovered that this was one of the problems (as well as using the wrong drivers).   Once I had this driver I installed ndiswrapper and did the following as root:

1. blacklist the bcm43xx driver that tries to load:
sudo gedit /etc/modprobe.d/blacklist (this will open up the blacklist file)
look at the format of the other entries and type "blacklist bcm43xx" and save the file.

2. extract the driver from the R151517 file you downloaded:
unzip -a R151517.EXE  (navigate to where R151517 is saved)

3. go into the directory you just extracted and move the bcmwl5.inf and bcmwl5.sys files from the driver directory to your desktop.

4. open a terminal and type:
"sudo rmmod ndiswrapper" (removes previosly loaded ndiswrapper module -skip if you haven't loaded ndiswrapper)
 
5. type:
sudo ndiswrapper -i /home/robert/Desktop/bcmwl5.inf
(this loads the driver.  your username will likely be different)

6. type:
sudo ndiswrapper -m  (you'll likely get some alias message)
sudo modprobe ndiswrapper

7. (assuming you have gnome like me) go to your System menu and click network.  select "wireless connection" and then properties.  Make sure that enable roaming mode is selected.

8. close everything and reboot your machine at this point.  after reboot click on the network icon in the upper right corner and you should see a dropdown list of available networks.  select the one you want and enter your passphrase etc.  An applet may start that will ask if prompt you to save this on a keyring of some sort.  Do it and then you just have to enter your user password and your wifi passphrase  will be given to the network you connecting to automatically.

Hope this is useful.

---


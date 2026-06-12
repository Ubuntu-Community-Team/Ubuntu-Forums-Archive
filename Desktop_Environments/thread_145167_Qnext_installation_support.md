---
title: "Qnext installation support"
date: 2006-03-15
forum: Desktop Environments
---

### Post by khalidmian on 2006-03-15
I am able to download the qnext client for linux and uncompress the product tar or whatever file it is to create a folder by the name of qnext in which there is an exe file for the client. My question is concerned with the appropriate way for installing the qnext client such that i can run it via an icon rather then go into the folder and then run the client. Any help suggestions would be nice. And yes i have tried to create a shortcut of the exe file and tried to run the client via the shortcut created but to no avail

---

### Post by Turtle.net on 2006-03-16
Hello,
First of all for those who don't know what qnext is [http://qnext.com]("http://qnext.com")
and from PCMag > Think of Qnext as the Swiss Army knife of Internet communication tools. With this slick suite of applications (available free from the Qnext Web site), you can send and receive instant messages, set up group IM chats, initiate audio chats, start a video conference, and take part in online gaming. You can also send and receive large numbers of files and photos, and even log on to a distant machine and do full-screen remote control (much as you could with a remote-control program such as [GoToMyPC]("http://www.pcmag.com/article2/0,1895,1090087,00.asp")). 
To install that it's simple.
Download qnext at [http://qnext.com/download_linux.php]("http://qnext.com/download_linux.php")
Then uncompress the archive  ```
$ bunzip2 qnextsetup.tar.bz2
$ tar -xf qnextsetup.tar
``` Then you can launch it simply by
```
$ cd qnext
$ ./qnext
``` 
Then to create a launcher (that's maybe not the nicest way but ...)
```
$ gedit qnext_launch.sh
``` That will create a text file, just write :
> #!/bin/bash

cd <where you uncompressed qnext>/qnext
./qnext Then ```
$ sudo cp qnext_launch.sh /usr/bin
``` and ```
$sudo chmod +xxx /usr/bin/qnext_launch.sh
``` 
If you want to create a launcher from the gnome-panel simply type qnext_launch.sh in the command line.

Et voilà \\:D/

Enjoy

---

### Post by Barbar89 on 2006-06-06
I installed qnext this way but it crashs when the main interface starts! Where's my problem? Is my computer too slow?

CPU: AMD Duron 800 Mhz
RAM: 1024 MB

---

### Post by Turtle.net on 2006-06-06
You should try to launch qnext in a terminal to see what is the error.

---

### Post by cfgtech on 2006-09-17
The same thing happens to me.It launches I log in then
the interface locks up on the main screen.Looks like a cool program.
I will have to go to Sun to fnid out more on this issue..

---


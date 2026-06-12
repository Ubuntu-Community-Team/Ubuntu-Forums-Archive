---
title: "Shrinking Man Diet Software"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by srtraveler on 2007-05-15
I would like to have a diet tracking software package on the Ubuntu side of my confuser. I have used Nutribase for years and really like it but it is only partially available with the Wine access. I am getting tired of restarting the Windows partition (long wait) just for Itunes and Nutribase. So I found Shrinking Man and it looks good but the message pasted below appears in the download instructions. I have gotten things bunged up in the past--not with Ubuntu but the other OS--when I have downloaded a lot of things I didn't understand in order to access something that was not perfected, or whatever. Any advice or help including recommending other programs of this type would be appreciated. BTW, this was found on [http://debain.org/software/shrinkingman/](http://debain.org/software/shrinkingman/). Thanks.

Before You Download

In order to be able to install Skrinking Man, you will need other software installed on your computer. Please make sure that the following packages do already exist:

    * Python 2.4 or greater
    * pyxml 0.8 or greater
    * pygtk 2.8.0 or greater
    * pygnome 2.8 or greater

---

### Post by mbradlcu on 2007-05-18
Hi there,
the packages that are needed may already be installed. The easy way to tell is use synaptic but if you want to use the command line as sudo -s do
dpkg -l |grep python
dpkg -l |grep python |grep xml
dpkg -l |grep python |grep gtk
dpkg -l |grep python |grep gnome

if you see "ii" the package in installed.

I just installed it (guess now all my buddies will know why I'm so skinny ; )
let me know if you need any help with it.
Matt

---


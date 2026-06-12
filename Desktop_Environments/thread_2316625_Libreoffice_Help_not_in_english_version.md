---
title: "Libreoffice Help not in english version?"
date: 2016-03-09
forum: Desktop Environments
---

### Post by eightbits2010 on 2016-03-09
Ubuntu 15.04

Using Libreoffice:
Version: 4.4.6.3
Build ID: 40m0(Build:3)
Locale: en_US.UTF-8


While accessing the help menu in Libreoffice Writer I get a Swedish menu. Some of it is in English. Is this a setting issue or do I need to re-install Libreoffice or just re-install the Writer?
I was accessing help in order to print a envelope.

Thanks for any assistant, I was concerned tat this is not yhe correct version I should be using.

---

### Post by goofprog on 2016-03-09
Honestly, I would just grab a book from the public library on Libreoffice (openoffice) 
You just have to find the "page size" of the envelope and use that.  Just go to the main web site and download the help file in english as another solution.

---

### Post by deadflowr on 2016-03-09
Well, what version, or where did you get the version in use?
And which language is preferred?

Also [Ubuntu 15.04 has met it's demise]("http://fridge.ubuntu.com/2016/02/05/ubuntu-15-04-vivid-vervet-end-of-life-reached-on-february-4-2016/")

---

### Post by ajgreeny on 2016-03-09
Run command ```
sudo apt-get install libreoffice-help-en-gb
``` or -us at the end of package name if in USA and needing the US English version.

You may find you have other unwanted help versions installed which you can find with ```
dpkg --list libreoffice-help*
``` Those in lines starting with ii are installed and you can remove any others you do not want with the appropriate **sudo apt-get remove packagename** command.

---


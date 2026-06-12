---
title: "Trying to install e17 from e17.dunnewind.net from local drive"
date: 2008-01-24
forum: Desktop Environments
---

### Post by Toxicio on 2008-01-24
Hello! I have only dial-up Internet connection at home, so I cannot use apt-get to install e17 from [http://e17.dunnewind.net](http://e17.dunnewind.net). On other hand, at work I have relatively good Internet connection, but I cannot install Gutsy here (This computer is used by other people, and, alas, they won't be glad to see Ubuntu instead of Windows. Moreover, I'm not an admin on this machine and cannot install it in a dual boot). So, my idea was to download complete [http://e17.dunnewind.net](http://e17.dunnewind.net) using Teleport Pro (excluding files *amd64*; *feisty*; *dapper*; *.orig.tar.gz; *.orig.tgz, I need only i386 deb packages for Gutsy) and then install it from my local hard drive at home. I've done this with wxWidgets and thought that everything will be alright. But sudo apt-get install e17 (after appending repo to sources.list, apt-key add, of course) results with the following message (translated from russian):

Err file: gutsy/e17 libevas0 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-eet 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-png 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-jpeg 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-engine-software-generic 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-engine-buffer 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-saver-eet 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-saver-jpeg 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-saver-png 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-engine-software-x11 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libexml1 0.1.1+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 emodule-winselector 0.16.999.041+cvs20071216-1gutsy1
  File not found
Err file: gutsy/e17 emodule-wlan 0.16.999.041+cvs20071216-1gutsy1
  File not found
Err file: gutsy/e17 emodules-all 0.16.999.041+cvs20071216-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-tiff 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-gif 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-xpm 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-svg 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loaders-all 0.9.9.041+cvs20071214-1gutsy1
  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-eet_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-png_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-jpeg_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-engine-software-generic_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-engine-buffer_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-saver-eet_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-saver-jpeg_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-saver-png_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-engine-software-x11_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/exml/libexml1_0.1.1+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/emodules/emodule-winselector_0.16.999.041+cvs20071216-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/emodules/emodule-wlan_0.16.999.041+cvs20071216-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/emodules/emodules-all_0.16.999.041+cvs20071216-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-tiff_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-gif_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-xpm_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-svg_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loaders-all_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found

I thought this files just wasn't retrieved by Teleport Pro, but it appears that it is indeed missing
on server! Maybe I'm doing wrong something (I use GNU/Linux only for a 2 months)... Please, help! Sorry for a long post. It is my first serious post in forum ;)

---

### Post by Kris001 on 2008-01-24
Ok, I also don't know Linux very good, I'll just have a try :)

Can't you just click on the files you downloaded? Won't they install then?

---

### Post by smartboyathome on 2008-01-24
> **Toxicio said:**
> Hello! I have only dial-up Internet connection at home, so I cannot use apt-get to install e17 from [http://e17.dunnewind.net](http://e17.dunnewind.net). On other hand, at work I have relatively good Internet connection, but I cannot install Gutsy here (This computer is used by other people, and, alas, they won't be glad to see Ubuntu instead of Windows. Moreover, I'm not an admin on this machine and cannot install it in a dual boot). So, my idea was to download complete [http://e17.dunnewind.net](http://e17.dunnewind.net) using Teleport Pro (excluding files *amd64*; *feisty*; *dapper*; *.orig.tar.gz; *.orig.tgz, I need only i386 deb packages for Gutsy) and then install it from my local hard drive at home. I've done this with wxWidgets and thought that everything will be alright. But sudo apt-get install e17 (after appending repo to sources.list, apt-key add, of course) results with the following message (translated from russian):

Err file: gutsy/e17 libevas0 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-eet 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-png 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-jpeg 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-engine-software-generic 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-engine-buffer 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-saver-eet 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-saver-jpeg 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-saver-png 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-engine-software-x11 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libexml1 0.1.1+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 emodule-winselector 0.16.999.041+cvs20071216-1gutsy1
  File not found
Err file: gutsy/e17 emodule-wlan 0.16.999.041+cvs20071216-1gutsy1
  File not found
Err file: gutsy/e17 emodules-all 0.16.999.041+cvs20071216-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-tiff 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-gif 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-xpm 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loader-svg 0.9.9.041+cvs20071214-1gutsy1
  File not found
Err file: gutsy/e17 libevas0-loaders-all 0.9.9.041+cvs20071214-1gutsy1
  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-eet_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-png_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-jpeg_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-engine-software-generic_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-engine-buffer_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-saver-eet_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-saver-jpeg_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-saver-png_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-engine-software-x11_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/exml/libexml1_0.1.1+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/emodules/emodule-winselector_0.16.999.041+cvs20071216-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/emodules/emodule-wlan_0.16.999.041+cvs20071216-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/emodules/emodules-all_0.16.999.041+cvs20071216-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-tiff_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-gif_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-xpm_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loader-svg_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found
Cannot download file:///home/toxicio/locrep/E17/repo/dunnewind/e17.dunnewind.net/ubuntu/pool/e17/e/evas/libevas0-loaders-all_0.9.9.041+cvs20071214-1gutsy1_i386.deb  File not found

I thought this files just wasn't retrieved by Teleport Pro, but it appears that it is indeed missing
on server! Maybe I'm doing wrong something (I use GNU/Linux only for a 2 months)... Please, help! Sorry for a long post. It is my first serious post in forum ;)

You might want to bring them to your computer, use [APTonCD]("http://aptoncd.sourceforge.net/") to put the files on a repository CD. This might help you.

---

### Post by jacksaff on 2008-01-24
Did you apt-get update?

---

### Post by Toxicio on 2008-01-26
2 Kris001:
I thought as well, too, but I cannot find such files at my local folder!

2 smartboyathome:
Thanks for the link, I really think this program will be useful for me! I'll try it. Local repo (using string like deb file:///... in sources.list) worked well for wxWidgets, but maybe with this program things would be much easier...

2 jacksaff:
Yes. Maybe I need also upgrading (apt-get upgrade as I remember) my system, but I think it will be a lot of traffic, so it is not for my home PC :-(

Thanks for help, everyone! Maybe APTonCD will help, I will try it. A word from maintainers of a e17.dunnewind.net would be HIGHLY appreciated! Maybe I should try installing cvs system. I am not very familiar with it, I heard the word "CVS" for the first time, to be honest ;-) Right now I don't want to have the newest version of e17, I just want to have some working version, new or (relatively :-) ) old...

---


---
title: "Dreamweaver CS4 / Fireworks CS3 - Use on Ubuntu 9.10"
date: 2010-02-19
forum: Desktop Environments
---

### Post by francescogondolin on 2010-02-19
**[SIZE=4]How to install Dreamweaver CS4 and Fireworks CS3 on Ubuntu 9.10[/SIZE]**


[SIZE=3]Hi Everyone, It's the first post I make here. I completly switched to Ubuntu some weeks ago and I like it, the only problem untill some minutes ago was Fireworks (I work as web designer from time to time) something that cannot easly be replaced. I post here the solutions I've found and tried:

**Index**
- Dreamweaver CS4
- Firefox CS3
- Flash....
- Virtual Machine (Get Windows on Ubuntu and then install Macromedia and everything else)


**Install Dreamweaver CS4**
I looked on Google and I've found this guide works perfectly:
 
[http://aminesoft.wordpress.com/2009/08/18/install-dreamweaver-cs4-in-ubuntu-and-debian/ ]("http://aminesoft.wordpress.com/2009/08/18/install-dreamweaver-cs4-in-ubuntu-and-debian/")

on my Ubuntu 9.10 (with Dreamweaver CS4 , V10.0 , Built 4117) works very well. I just copy and paste the guide to make things easier 

-----------------------------------------------------------------
[/SIZE][FONT=arial]Build world-class websites and applications with one of the industry&#8217;s  leading web authoring tools. **Adobe Dreamweaver CS4 **software is ideal for web designers, web developers, and visual designers. Manipulate pixel-level designs in Design view, or craft complex code in Code view while working in the real browser environment of Live View. There is no linux version for Dreamweaver, but   there are many open source alternative for this  product like[ Kompozer]("http://www.unixmen.com/linux-tutorials/307-kompozer-easy-and-powerfull-web-builder-for-linux"), bluefish &#8230;.[/FONT]
 [FONT=arial]Now  we  will  try  to  run it   under  Linux (ubuntu or  debian)[/FONT]
 [FONT=arial]you   should   have  installed  CS4 under  windows  because  we  need  this  directory  to  complete  the  installtion[/FONT]
 [FONT=arial]now  we  need  to download  some  packages to  help  us . :[/FONT]
 [FONT=arial]1- Install wine
[/FONT]
 [FONT=arial]**[COLOR=#003300]$sudo apt-get install wine winecfg[/COLOR]**[/FONT] [FONT=arial]now  we  begin to  copy  folder from windows  to  ubuntu .[/FONT]
 [FONT=arial]2-navigate to *C:\Program Files*. Copy the whole &#8216;*Adobe*&#8216; folder to Ubuntu */home/username/.wine/drive_c/Program Files* folder.[/FONT]
 [FONT=arial]3- copy  *C:\Documents and Settings\your-windows-user-name\Application Data  to *[I]/home/username/.wine/drive_c/windows/profiles/All Users/Application Data/
[/I][/FONT]
 [FONT=arial]*4-copy **C:\Program Files\Common Files  to **/home/username/.wine/drive_c/Program Files/Common Files*[/FONT]
 [FONT=arial]*5- **copy  C:\WINDOWS\system32  to **/home/username/.wine/drive_c/windows/system32*[/FONT]
 [FONT=arial]*6-copy   Winsxs  from   C:\windows    to *[I]/home/username/.wine/drive_c/windows/  (this folder is  verry  important)
[/I][/FONT]
 [FONT=arial][I]7-  import   the  registery to  wine
[/I][/FONT]
 [FONT=arial][I]from windows  for  to   start and  Run (regedit)
[/I][/FONT]
 [FONT=arial]*go  to **HKEY_LOCAL_MACHINE-> SOFTWARE->Adobe->Dreamweaver  ; *Right click on the &#8216;*Dreamweaver*&#8216; folder and select &#8216;*Export&#8217;*. Save the file as [I]dreamweaver.reg and  copy  this  file  to  ubuntu  home  directory  and  you  need  to  coinvet the  registery  file   to   ASII  file   (recode)
[/I][/FONT]
 [FONT=arial][COLOR=#003300]**$sudo   apt-get  install  recode **[/COLOR][/FONT] [FONT=arial]* recode is  :   (*Conversion between character sets and surfaces)[/FONT]
 **[COLOR=#003300][FONT=arial]$recode ucs-2..ascii dreamweaver.reg[/FONT][/COLOR]** [COLOR=#003300]**[FONT=arial]$wine regedit dreamweaver.reg[/FONT]**[/COLOR] [FONT=arial]
[/FONT]
 [FONT=arial]*Now *you have successfully copied  all  needed files  to  run   your  installation succefully.[/FONT]
 [FONT=arial]lets  give  a  test :[/FONT]
 [COLOR=#003300]**[FONT=arial]$cd /home/username[/FONT]**[/COLOR] [FONT=arial][COLOR=#003300]**$cd .wine/drive_c/Program\ Files/Adobe/Adobe\ Dreamweaver\ CS4/**[/COLOR][/FONT] [FONT=arial] [COLOR=#003300]**$wine Dreamweaver.exe**[/COLOR][/FONT] [FONT=arial]Should  be  lunching   the  programe  now.[/FONT]
[SIZE=3]-----------------------------------------------------------------


So with this you should have a working DCS4, at least I have


[/SIZE][SIZE=3]**Install Fireworks CS3**[/SIZE]
[SIZE=3]
I've followed the procedure also for my Fireworks CS4 didn't work, it were loading but giving me two errors:

- Parameter is incorrect.....
- Error 147:30

I've found out that it's something related both with the language but also with the expiration date. After a while I gave up and I've found 3 solutions:

_Solution 1 (The one I adopted)_

There's a file on internet torrents called "Adobe Fireworks CS3 Portable". If you have the license for CS3, as I have, there's nothing bad in finding the torrent and downloading it.

It's a single file, a single EXE, you just copy it in your Wine and open with Wine, it works perfectly.

[/SIZE][SIZE=3]
_Solution 2 (I tried it but then I deleted everything)_[/SIZE]
[SIZE=3]
The second solution is to download VirtualBox, install XP and then you can make what you want.I tried it, it works BUT
to use 10 GB of space for just a software it's too much for my taste

_Solution 3_

Find on this page
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=665](http://appdb.winehq.org/objectManager.php?sClass=application&iId=665)

the Wine version and the Firework version that fit together.


**Installing Flash**

The same as for Fireworks:
- Virtualbox
- Portable version of the file
- Wine 



[B]Virtual BOX
[/B]
I discovered a nice feature of Virtual Box: you can save the virtual machine on an external harddrive. So now that I've got 1 Terabyte HD, I just moved all my macromedia software and officethe VBOX. For the installation just google "Vbox ubuntu" and you will get the instruction. Just an information: if your external harddrive is FAT 32 or something else **I would format it with NTFS fylesystem, otherwise you will get problems with filesize limits!!!**





[/SIZE]

---

### Post by issachan on 2010-03-27
Thank you for posting this! :D

I have been searching everywhere for instructions for 9.10. I have finally gotten Dreamweaver CS4 to work!

I followed the steps and tried to run it but it kept getting the Error 147:20. I then followed your next piece of advice and downloaded a portable Dreamweaver CS4 .exe file. I installed it with wine and it seems to work ok, although it's a little glitchy. I then added the portable .exe file version to the wine menu and now it works! The process doesn't work for Photoshop, but I'm going to try to use Gimpshop (free alternate to Photoshop).

---

### Post by francescogondolin on 2010-03-28
Good :). I always find good answer on this forum so when I can I will post usefull stuff too!

---

### Post by HomeSlixe on 2010-06-14
Have any of you come across a problem with loading, saving or accessing anything from the local files pane, or when trying to open a file anywhere on your disk and .wine folder?
I keep getting an access denied promt, and it is very frustrating. Thanks in advance to any one who has a solution!

---

### Post by HomeSlixe on 2010-06-15
basically I cannot navigate site management... drag and drop into site management returns an access denied prompt... any one else have this happen to them?

---


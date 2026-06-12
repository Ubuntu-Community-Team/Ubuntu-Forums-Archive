---
title: "Error with Wubi 9.04 Installer"
date: 2009-04-23
forum: General Help
---

### Post by adjohnson916 on 2009-04-23
I'm trying to install the new Wubi 9.04 on Windows XP SP3, and I get this error right when I run it before the installer dialog even loads. No matter which option I click, the same pop up reappears immediately, over and over and over and over until I logoff or restart.

I'd really like to get a fresh Jaunty Jackalope install working through Wubi, anyone able to help?

[IMG]http://i43.tinypic.com/35cev54.jpg[/IMG]
[http://i43.tinypic.com/35cev54.jpg](http://i43.tinypic.com/35cev54.jpg)

---

### Post by JustinBailey on 2009-04-24
I'm having a similar problem. 

But I'm on Vista, and the message reads: 

"04-24 14:59 ERROR  TaskList: writelines() argument must be a sequence of strings"

And then the installation stops.

I'd like to have this problem corrected ASAP.

For now I'll have to be content with installing Intrepid and upgrading to Jaunty...

=<

---

### Post by jsowoc on 2009-04-24
I was getting a similar problem when writing a file to a USB key. The way I got around it was to ftp the file and check the md5sum. Are you trying to install off a CD, USB-key, or ISO image? I suggest putting wubi.exe and the .iso file in the same directory on the hard drive, and then starting wubi.exe.

---

### Post by JustinBailey on 2009-04-24
> **jsowoc said:**
> I was getting a similar problem when writing a file to a USB key. The way I got around it was to ftp the file and check the md5sum. Are you trying to install off a CD, USB-key, or ISO image? I suggest putting wubi.exe and the .iso file in the same directory on the hard drive, and then starting wubi.exe.

Somehow, Wubi looks for CD on the drives, or images. And if it cannot find them, it downloads an iso from the Internet. But this Jaunty Wubi is not downloading anything from the Internet, and it is directly looking for the CD/iso with no other choice for search. 

Looks like I'm gonna have to download an .iso from the Internet 

=<

---

### Post by tusuka on 2009-04-24
I'm also having the same problem even I downloaded the "ubuntu-9.04-desktop-amd64.iso" 4 times :)

---

### Post by jsowoc on 2009-04-24
You need to download the .iso anyway at one point or another. I suggest getting the torrent (it's the fastest). You can download the wubi.exe and put it in the same directory as the .iso, and it should find it.

If you are able to describe how to reproduce the error, then maybe it's a Wubi bug that should be reported.

---

### Post by m_2009 on 2009-04-24
I found that running the wubi included in the Jaunty CD to be rather buggy, and I experienced both the error messages included above.

I managed to get wubi to work by doing the following:

1) Make sure you have uninstalled the "failed" attempt of the wubi installation, it will be listed in Add/Remove programs in windows control panel (called Programs And Features in vista), it seems even if the installation fails it doesnt delete the c:\ubuntu folder or any of the other files it half coped, so running the uninstaller in Add/Remove programs will help, 

2) Download the ubuntu jaunty ISO image from the server, but keep the ISO file and dont bother burning it to a CD.

Download a seperate version of Wubi.exe. There is a seperate version of wubi that can be downloaded from the ubuntu download page. Goto the following link

[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)

Scroll right down to the bottom of the page and you will see Wubi.exe

[http://releases.ubuntu.com/jaunty/wubi.exe](http://releases.ubuntu.com/jaunty/wubi.exe) (Direct Link)

This version of wubi is build 129, the version included on the Jaunty final release cd/ISO is only build 128.

3) Empty your Temp folder in windows. In windows XP this will be at "C:\Documents and Settings\(User Name)\Local Settings\Temp"
and for Vista "C:\Users\(User Name)\AppData\Local\Temp"
The wubi installer seems to leave some files hanging around in ehre too, so removing them helped me.

4) Reboot computer

5) Run the wubi.exe which you downloaded seperately, making sure the ubuntu ISO you downloaded is located in the same folder as wubi.exe

This seemed to work for me and jaunty installed without any problems in wubi.

---

### Post by GimmeCoffe on 2009-04-26
> **adjohnson916 said:**
> I'm trying to install the new Wubi 9.04 on Windows XP SP3, and I get this error right when I run it before the installer dialog even loads. No matter which option I click, the same pop up reappears immediately, over and over and over and over until I logoff or restart.

I'd really like to get a fresh Jaunty Jackalope install working through Wubi, anyone able to help?

[IMG]http://i43.tinypic.com/35cev54.jpg[/IMG]
[http://i43.tinypic.com/35cev54.jpg](http://i43.tinypic.com/35cev54.jpg)

I had the same problem.  I kept pressing cancel and eventually the installation dialog showed up.:)

---


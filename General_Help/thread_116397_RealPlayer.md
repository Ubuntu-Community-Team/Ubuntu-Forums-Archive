---
title: "RealPlayer"
date: 2006-01-12
forum: General Help
---

### Post by KhanArash on 2006-01-12
I have installed and running ubuntu 5.10.
I have been trying and trying to install the realone but i cant make it work, and I would ask you if you could help me to install and make it work?

---

### Post by gosh on 2006-01-12
Did you try and install it using synaptic?
What went wrong during your efforts?

---

### Post by hillbilly on 2006-01-12
[QUOTE=KhanArash]I have installed and running ubuntu 5.10.
I have been trying and trying to install the realone but i cant make it work, and I would ask you if you could help me to install and make it work?[/QUOTE]

I guess this might not be relevant, but you can play rm files with mplayer.

---

### Post by KhanArash on 2006-01-12
I tried to instal it with  synaptic! but I didnt find how!:confused:

---

### Post by healychan on 2006-01-12
It is so easy to install Realplayer. Open a firefox browser, click the Firefox bookmark on the tools bar. On that page, you should see a link about getting latest plugin. Follow that link and read the instruction carefully. The whole process take no more than 10 mins.:)

---

### Post by KhanArash on 2006-01-12
I have downloaded and installed realplayer, but in the end I get the "Failstatus 1"...and the program doesn't start.And I installed the realplayer with using synaptic and add aplication!
CAn someone please help me to fix it?!

---

### Post by KhanArash on 2006-01-12
[QUOTE=healychan]It is so easy to install Realplayer. Open a firefox browser, click the Firefox bookmark on the tools bar. On that page, you should see a link about getting lastest plugin. Follow that link and read the instruction carefully. The whole process take no more than 10 mins.:)[/QUOTE]


I can see many bookmarks but none of them is getting lastest plugin...:confused:

---

### Post by healychan on 2006-01-12
[QUOTE=KhanArash]I can see many bookmarks but none of them is getting lastest plugin...:confused:[/QUOTE]

Click the "getting start" bookmark which located on the tools bar, a html page comes up, find "latest plugin" there, not the tools bar..

And sorry about the typing mistake "lastest", it should be "latest".

---

### Post by coolworld on 2006-01-12
Installed RealPlayer successfully, I just downloaded the bin file from their site and follow their instruction. I can't install it to my desired directory thou (still new will ubuntu.:eek: )

I can run RealPlayer inside the directory where it is install. My question is, is RealPlayer for Linux does not support 3gp files and how do I create a shortcut to be put in the luncher?

---

### Post by KhanArash on 2006-01-13
[QUOTE=coolworld]Installed RealPlayer successfully, I just downloaded the bin file from their site and follow their instruction. I can't install it to my desired directory thou (still new will ubuntu.:eek: )

I can run RealPlayer inside the directory where it is install. My question is, is RealPlayer for Linux does not support 3gp files and how do I create a shortcut to be put in the luncher?[/QUOTE]

Cam the .bin file work in the ubuntu 5.10?òr do I need to download the RPM file?

---

### Post by healychan on 2006-01-13
[QUOTE=coolworld]Installed RealPlayer successfully, I just downloaded the bin file from their site and follow their instruction. I can't install it to my desired directory thou (still new will ubuntu.:eek: )[/QUOTE]
What is your desired directory??? Is that directory owned by root so you cannot write to it???? If it is, use "sudo ./xxxx.bin"

[QUOTE=coolworld]I can run RealPlayer inside the directory where it is install. My question is, is RealPlayer for Linux does not support 3gp files and how do I create a shortcut to be put in the luncher?[/QUOTE]
You should read the Realplayer web site and see what format are supported by Realplayer. I read it once but I don't think I saw something like 3pg.

---

### Post by healychan on 2006-01-13
[QUOTE=KhanArash]Cam the .bin file work in the ubuntu 5.10?òr do I need to download the RPM file?[/QUOTE]
You need the .bin file instead of .rpm file.

Download that file. Then type "sudo ./xxxxx.bin" to start the installer.
I suggest that you install Realplayer in this directory "/usr/lib"

Again, the whole process should take no more than 10 mins, from download to finish install.

---

### Post by coolworld on 2006-01-14
[QUOTE=KhanArash]Cam the .bin file work in the ubuntu 5.10?òr do I need to download the RPM file?[/QUOTE]

I downloaded the .bin file and simply follow the instruction posted in the RealPlayer site. Can't make the RPM file work.

---

### Post by coolworld on 2006-01-14
[QUOTE=healychan]What is your desired directory??? Is that directory owned by root so you cannot write to it???? If it is, use "sudo ./xxxx.bin"[/QUOTE]
Hmmm....not on my desktop. :D

[QUOTE=healychan]
You should read the Realplayer web site and see what format are supported by Realplayer. I read it once but I don't think I saw something like 3pg.[/QUOTE]
I read it after installing and found out that it doesn't suppot 3gp format.

---

### Post by cjazz on 2006-01-14
FYI, to install RealPlayer 10 via apt-get or Synaptic, you need a supporting repository enabled. Adding either

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

or

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

to your /etc/apt/sources.list file should do it.

---

### Post by Perfect Storm on 2006-01-14
```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

then:
```
sudo apt-get update
sudo apt-get install realplay

```

---


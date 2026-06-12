---
title: "[SOLVED] windows command prompt emulator for ubuntu"
date: 2008-12-23
forum: General Help
---

### Post by nmpach on 2008-12-23
I have a project to write a script for a doctors office that will back up the docs server files onto another machine with an external hard drive at the doctor's house. The two machines will be on separate networks. Now, I wish to God above that the server and backup machine ran os x or linux so I could use a bash shell script, but they both run windows and as much as I've pushed there'll be no changing that. They don't want to download any existing software either - I've written for them in the past and things have gone well enough. A big problem with this is that I don't have a windows machine at home. I run ubuntu - obviously... posting on Ubuntu forums - and I was wondering if anybody knew of any free/opensource software that I could use to emulate the windows command prompt on Ubuntu for development purposes only because I plan on using a .bat file to accomplish this task. With that said, all help appreciated,

nmpach

---

### Post by Titan8990 on 2008-12-23
Cygwin emulates a BASH shell for windows: [http://www.cygwin.com/](http://www.cygwin.com/)


Delta Copy is rsync for windows: [http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

It's FOSS and you can use it to send the backups across the internet but it will be unencrypted (rsh).

---

### Post by dcstar on 2008-12-23
> **nmpach said:**
> I have a project to write a script for a doctors office that will back up the docs server files onto another machine with an external hard drive at the doctor's house. The two machines will be on separate networks. Now, I wish to God above that the server and backup machine ran os x or linux so I could use a bash shell script, but they both run windows and as much as I've pushed there'll be no changing that. They don't want to download any existing software either - I've written for them in the past and things have gone well enough. A big problem with this is that I don't have a windows machine at home. I run ubuntu - obviously... posting on Ubuntu forums - and I was wondering if anybody knew of any free/opensource software that I could use to emulate the windows command prompt on Ubuntu for development purposes only because I plan on using a .bat file to accomplish this task. With that said, all help appreciated,

nmpach

Wine.

---

### Post by 2hot6ft2 on 2008-12-23
Notepad in wine then all you have to do is change the extension from a txt to a bat file.

---

### Post by Coder543 on 2008-12-23
Look, people. You are not helping.

This person wants to be able to write and test batch files under ubuntu so that he can provide a working batch file for the doc. He doesn't need notepad. He can't install existing software on their machines. He has to be able to debug it on his machine. I don't know how to do this, but I would recommend getting them perl, or something of the likes. Then you can write it on ubuntu and run it on windows.

---

### Post by Patrick793 on 2008-12-23
Install Wine and create the batch file with whatever you want to. Then once it's made, right click it and select "Open With > Wine Windows Program Loader".

The batch file will run using Wine, just like it would on Windows.

---

### Post by nmpach on 2008-12-24
I'm going to install wine now. Also, I don't know Perl but that gave me the idea that maybe I could do this in PHP, with which I'm more than comfortable... Ideas, ideas...

... And guys. wow. I've posted at a lot of forums, but in my 17 years of life I have never gotten so many replies so fast. You guys are great. I know where to go if I have any other issues. All help appreciated,

nmpach

edit
=====

I have wine installed; it has it's own tab under the applications drop down menu and I can browse the file system, use notepad, etc. However, there is no "Wine Windows Program Loader" application when I browse for it after choosing "open with ..."

---

### Post by dcstar on 2008-12-24
> **nmpach said:**
> 
.......
I have wine installed; it has it's own tab under the applications drop down menu and I can browse the file system, use notepad, etc. However, there is no "Wine Windows Program Loader" application when I browse for it after choosing "open with ..."

As with every Windows system, you run "command" or "cmd" to open a command box.

---

### Post by nmpach on 2008-12-24
perfect dcstar. wine works great and within a couple hours of posting my initial problem, it has been solved and I'm now developing. Thanks again to everyone who posted,

nmpach

---

### Post by dcstar on 2008-12-24
> **nmpach said:**
> perfect dcstar. wine works great and within a couple hours of posting my initial problem, it has been solved and I'm now developing. Thanks again to everyone who posted,

nmpach

Please read the lines at the end of this post.

---

### Post by beacha on 2012-09-04
Boot to an ubuntu installation disk and click try ubuntu. You might not have the option to try ubuntu, or you don't have the disk. Just download the iso from http://www.ubuntu.com/. Use that to burn a disk. You'll see a screen like ubuntu. click Dash Home and type in terminal. Click on terminal and use it to execute your commands. This will not harm your computer. Although this will not work if you want to use this from windows. You can still save the batch file (or whatever they call it in linux) to your hard drive.

---


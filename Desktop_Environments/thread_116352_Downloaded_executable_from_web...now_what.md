---
title: "Downloaded executable from web...now what?"
date: 2006-01-12
forum: Desktop Environments
---

### Post by Autolycus on 2006-01-12
Howdy..

I downloaded a program from the web....came as a tar....extracted it...it is now an .exe file (in a folder with other necessary files)...

Where do I put it, how do I put it there, and how can I access it via menu?

---

### Post by kaamos on 2006-01-12
Can you tell us what the program is?

---

### Post by aysiu on 2006-01-12
Please mention the name of the program.
If you do, it'll help in four major ways:

1. If there's a native Linux version of the program that's as good as or better than the .exe program you're trying to run, we can recommend you use that instead.

2. Only some Windows programs will run under Wine; others need something like Crossover Office or VMWare. We won't be able to tell you which you need... unless you tell us the name of the program.

3. If it's not an .exe, but it's actually a native Linux program (the mention of "tar" clued me that it may be), then you may be better off installing it through Synaptic Package Manager.

4. If your problem gets solved, someone else who may have the same question can search for the name of the program and find this thread... and have her problem solved as well.

---

### Post by Autolycus on 2006-01-12
PC-Mac-Net Fileshare 5.1.0   (from LavaSoftware.com).

It allows file transfer from computer to computer. I have copies on my Mac and on my Wintel computer...makes file transfer easy..

---

### Post by Mr_Grieves on 2006-01-12
Read the programs documentation? Check the softwares website for installation instructions? Check for a README file in the programs directory? Use google? Double click on the program and see what happens? Use a terminal and execute it?

Have abit of imagnination :)

To access it via a menu, right click on the toolbar/menu and there should be an option to create a new shortcut.
But who knows.. what might be done automaticly in an installation of the software. If there is something more that you must do, exept for extracting it from it's archive.

---

### Post by aysiu on 2006-01-12
[QUOTE=Autolycus]PC-Mac-Net Fileshare 5.1.0   (from LavaSoftware.com).

It allows file transfer from computer to computer. I have copies on my Mac and on my Wintel computer...makes file transfer easy..[/QUOTE] That's weird. I just downloaded the Linux version, extracted it, and there's almost nothing in there... no README file, no instructions...

There's just a file called *PC-Mac-Net_FileShare_Lin_Lite* and two folders full of auxiliary files (picture files and such).

You know, I share files between Ubuntu and my wife's Mac OS X Powerbook all the time, and I don't use any separately downloaded program for that. I just open Nautilus and type smb:// and then IP address for her computer.

---

### Post by Autolycus on 2006-01-12
There is one folder named "Data", one folder named "User_Manual", html based, and the program...mine is named: PC-Mac-Net_Fileshare_Lin"

under properties it says it is executable...

I guess an email to lavasoftware is in order...

or..

I could set up a FTP server on ubuntu.....easy to do?

---

### Post by kaamos on 2006-01-12
For the ftp: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by Ampersand on 2006-01-12
To set up an ftp server, just install vsftpd (from apt/synaptic), and put the files you want to share in /home/ftp.

You'll have to edit /etc/vsftpd.conf , but the configuration file is fairly intuitive.

---

### Post by Autolycus on 2006-01-12
i'll try setting up ftp..

thanx for all help

---


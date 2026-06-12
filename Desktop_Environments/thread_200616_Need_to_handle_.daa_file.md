---
title: "Need to handle .daa file"
date: 2006-06-20
forum: Desktop Environments
---

### Post by jc87 on 2006-06-20
I have a **.daa** file in Ubuntu , i searched a while and discovered this kind of file is similar to an ISO,  and seems to be only support by a windows program called POWER-ISO.

I´ve been trying to find apps that would convert it to an ISO or let me reproduce it in some kind of way  , but so far i hadn´t had any kind of luck with that!

Does anyone know a solution for my problem? i already searched at google , synaptic , wikipedia , etc... but so far no luck.

---

### Post by ape on 2006-06-20
The only thing I can think of would be to install wine, download the shareware version of power-iso, and see if the program runs under wine well enough to open the .daa file and save it off in another format.

---

### Post by ashmew2 on 2007-01-30
[http://www.poweriso.com/poweriso-1.1.tar.gz](http://www.poweriso.com/poweriso-1.1.tar.gz) <-Power ISO for Linux

---

### Post by ohmyiv on 2007-03-27
sorry if this is a silly question...but, how do i get it to work?

---

### Post by FRealmS on 2007-03-28
...extract it!!!

in terminal type:

> poweriso -?

> 
PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

Usage:    poweriso <command> [parameters] [-switches]

<Commands>

 list <image file> <directory>    List files and directories in image file.
     Example:  List all files and directories in root direcory of /home/sam/test.iso .
     Command:  poweriso list /home/sam/test.iso / -r

 extract <image file> <dir/file name>   Extract files/directories from image file.
     Example:  Extract all files and directories in root direcory of /home/sam/test.iso
               to /home/sam/test recursively.
     Command:  poweriso extract /home/sam/test.iso / -od /home/sam/test

 [COLOR="Red"]convert <image file>    Convert image file to other format.
     Example:  Convert /home/sam/test.daa to standard iso file 
     Command:  poweriso convert /home/sam/test.daa -o /home/sam/test.iso -ot iso[/COLOR]

<Switches>

 -r             List or extract recursively.
 -o             Specify output image file name.
 -od            Specify output folder.
 -ot <iso|daa|bin>    Specify output image file type. If not specified, 
                the image type will be determined by file name suffix.
 -volsize <n>   Split output image file to multiple volumes, and set volume
                size to <n>. Example: -volsize 100M
 -setpassword <password>   Set password for output image file. 
                Example: -setpassword 12345678


---

### Post by ohmyiv on 2007-03-28
thanks! works perfectly..so far!

---


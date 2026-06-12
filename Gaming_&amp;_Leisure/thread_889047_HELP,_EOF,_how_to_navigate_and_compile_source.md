---
title: "HELP, EOF, how to navigate and compile source"
date: 2008-08-13
forum: Gaming &amp; Leisure
---

### Post by Keatoru on 2008-08-13
I downloaded the lastest EOF, a Frets on Fire song editor, and the only thing i could find to dl was the source. so i did, i saw a thread asking how to compile this before but i still don't understand. a reply to it had said to navigate to the src file.....thats the first problem...how...i open my terminal and it says "*name*@*name*-desktop:~$" I have the the src and bin folder extracted to the desktop in the folder eof132linux. the sources are in eof132linux/src. how do i get there. i tried:
```
folder eof132linux
type() \cd/home/*name*/desktop/eof132linux/src
cd ./home/*name*/desktop/wof132linux/src
cd eof132linux/src
cd eof132linux/src/
cd /eof132linux/src
cd /eof132linux/src/
cd root/home/*name*/desktop/eof132linux/src
```
none of them worked...
obviously i'm new to linux OS.

I'm running the lastest Ubuntu if it matters.. and when it comes to the compiling i have liballegro and build-essentials packages installed.

*name* = my computer username

*SORRY IF THIS IS THE WORNG SECTION FOR THIS!*

---

### Post by binbash on 2008-08-13
i couldn't find the link at google.Can you please link to the source code so i can help?

---

### Post by Keatoru on 2008-08-13
you can find the source here:
```
http://fretsonfire.wikidot.com/eof
```
when you go there go to the links section and then go to project site.

---

### Post by binbash on 2008-08-13
you will build via  : 

make -f makefile.linux

this command at src folder.

But you need to install Allegro first ;) 

[http://alleg.sourceforge.net/](http://alleg.sourceforge.net/)

Feel free to Pm me

---

### Post by Keatoru on 2008-08-16
.....seriouslly....did u even read my post...i already told you i had allegro..and that doesn't help me when i can't even get to the friggen directory i need to be in before i try compiling...

---

### Post by binbash on 2008-08-16
> **Keatoru said:**
> .....seriouslly....did u even read my post...i already told you i had allegro..and that doesn't help me when i can't even get to the friggen directory i need to be in before i try compiling...

yes i read your post.i do not know how you unzipped it.please use unzip command

-you will download the file
-unzip it via unzip
-go to the src directory

and you will do what i did at my previous reply.

PS : YOu will also need vorbis-tools and lame if you want to use import feature @ editor.

Sample : 

$cd
$mkdir eof123linux
$cd eof123linux
$wget -c [http://www.t3-i.com/ncdgames/eof132linux.zip](http://www.t3-i.com/ncdgames/eof132linux.zip)
$unzip eof132linux.zip
$cd src
$make -f makefile.linux

---


---
title: "Installing TuxCards"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jhuff on 2005-10-26
Has anyone successfully installed TuxCards in ubuntu 5.10?  I can not get [tuxcards_1.2-1_i386.deb]("http://www.tifskom.de/tux/1.2/debian/tuxcards_1.2-1_i386.deb") to install.

---

### Post by endersshadow on 2005-10-26
Just installed it successfully:

```
sudo dpkg -i tuxcards_1.2-1_i386.deb
```

That will install it.  Then, go to Applications>System Tools>Applications Menu Editor, and add the menu entry wherever you'd like.  The application can be found at /usr/local/bin/tuxcards

Have fun!

---

### Post by jhuff on 2005-10-26
I tried installing it and I get the following error when I try to run it:

jah@laptop:~$ sudo dpkg -i tuxcards_1.2-1_i386.deb
Password:
Selecting previously deselected package tuxcards.
(Reading database ... 65340 files and directories currently installed.)
Unpacking tuxcards (from tuxcards_1.2-1_i386.deb) ...
Setting up tuxcards (1.2-1) ...
jah@laptop:~$ tuxcards
**tuxcards: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory**

---

### Post by RikoW on 2005-10-26
[QUOTE=jhuff]
jah@laptop:~$ tuxcards
**tuxcards: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory**[/QUOTE]

Open *Synaptic*, hit the search button, search for *libstdc++5* and install it.
Do that for all other missing libraries which show up when you try to run tuxcards. Unfortunately, you have to do that lib by lib.

Good luck,

                      Riko

---

### Post by jhuff on 2005-10-26
[FONT=Verdana]Thanks,[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]Loading and installing *[SIZE=2]libstdc++5[/SIZE]* made TuxCards work.[/FONT]

---

### Post by dmBriarwood on 2005-11-07
I haven't had any luck installing Tuxcards on my Breezy Desktop - This is the result I get when running the line in a terminal:

$ sudo dpkg -i tuxcards_1.2-1_i386.deb
dpkg: error processing tuxcards_1.2-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 tuxcards_1.2-1_i386.deb
$

I'd appreciate any advice!
Thanks

---

### Post by RikoW on 2005-11-08
Sounds like you try to execute your *sudo dpkg* command not in the directory where the tuxcard deb is located.

It is probably in the Desktop or Documents directory if you downloaded it from the web.
So after starting your terminal window try:

```
cd ~/Desktop
ls

```

or

```
cd ~/Documents
ls

```

The ~ is a short form of /home/username. 
If you see the tuxcard .deb file appearing, execute your *sudo dpgk* command.

good luck,

             Riko

---

### Post by dmBriarwood on 2005-11-08
Thanks Riko, that did the trick!  Isn't it always the simple things we overlook?
dm

---

### Post by llew on 2006-03-25
Hi All,
can't get tuxcards to install.
dosn't seem to like 64bit?
 Can anyone help here with this .
thanks
llew


llew@ubuntu-spacelionm:~/Desktop$ sudo  dpkg -i tuxcards_1.2-1_i386.deb
dpkg: error processing tuxcards_1.2-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 tuxcards_1.2-1_i386.deb
llew@ubuntu-spacelionm:~/Desktop$

---

### Post by ubunta_pr0 on 2006-08-10
:-({|=

---

### Post by dimeotane on 2007-02-16
I've added the application to my gnome menu.. but I can't find the right icon  "tuxcards.xpm" 
any idea where that sucker is?

This is a minor detail, but most other .deb files manage to get the program entered into the menu with an icon automatically.  Perhaps thats an upcoming feature the programmer is working on ?!

---


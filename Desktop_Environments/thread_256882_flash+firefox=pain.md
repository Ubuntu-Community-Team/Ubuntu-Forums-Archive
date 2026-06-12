---
title: "flash+firefox=pain"
date: 2006-09-13
forum: Desktop Environments
---

### Post by jcrnan on 2006-09-13
So I have been having some problems with firefox latley and I tried to fix it again today. Flash isnt working properly as it crashed on any site that uses flash. 

I reinstalled java first and at first it seemed to work somewhat. gmail no longer crashed (altough it didnt use ajax properly). So I tried reinstalling firefox flash plugin but then the crashing returned. I then tried to install it manually but that had no effect.

Anyone know what is wrong? Im getting tired of this problem :/

errors:

When I try sudo update-flashplugin I get:
nan@THE-HOLY-LAPTOP:~$ sudo update-flashplugin
automatic installation failed due to network problems or upstream changes


And when I try to make it crash after opening it from terminal I get this error message on crash:
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
nan@THE-HOLY-LAPTOP:~$

---

### Post by chaosgeisterchen on 2006-09-13
I am using **flashplugin-nonfree** and it's working just fine.

Why not trying it out?

---

### Post by jcrnan on 2006-09-13
that is what Im using -_-

---

### Post by aysiu on 2006-09-13
I've **never** issued this command: ```
sudo update-flashplugin
``` All I've ever done is ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
``` and everything's worked...

---

### Post by jcrnan on 2006-09-13
ayusi: I did it because the customization guide said so. but it didnt work anyways tough.

---


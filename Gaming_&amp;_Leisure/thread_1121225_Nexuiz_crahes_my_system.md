---
title: "Nexuiz crahes my system"
date: 2009-04-09
forum: Gaming &amp; Leisure
---

### Post by Captain_Glen on 2009-04-09
Hi,

When I try to run Nexuiz my whole system crashes so badly I have to reboot.  I have a compaq presario c700.  I can play relatively new games under windows.  I am using compiz but I disable it and load metacity before I try to play games.

---

### Post by Polygon on 2009-04-09
do you have direct rendering?

type 'glxinfo | grep direct' into console and paste the output here

---

### Post by Captain_Glen on 2009-04-09
glen@glen-laptop:~$ glxinfo | grep direct
direct rendering: Yes
glen@glen-laptop:~$ 

I can play tux racer and torcs with no problems

---

### Post by Polygon on 2009-04-10
try playing it so it crashes your system, then look in your 'messages.log' file in system log viewer (system > administration > log viewer' and see if any interesting error messages come up

---

### Post by Captain_Glen on 2009-04-10
Nope no errors

---

### Post by detrate on 2009-04-10
There are actually 2 binary files that come with nexuiz (for your processor).  Assuming you're running the 686 version, nexuiz-linux-686-glx and nexuiz-linux-686-sdl.  I believe glx is the standard used one... you should try nexuiz-sdl and see if it runs better with your hardware.

Assuming you downloaded the Nexuiz 2.5 zip, it should be in your extracted directory root.

If this still fails, you can try running nexuiz with the -safe parameter from the terminal.

```
nexuiz-linux-686-glx -safe
```

for example

---

### Post by Captain_Glen on 2009-04-10
I downloaded nexuiz with Add/Remove Programs.  Should I uninstall it and download the zip archive?

---

### Post by detrate on 2009-04-10
Definitely, the one in the official Ubuntu repositories is old.

If you feel more comfortable having a package that installs itself automagically, you can use the one provided by getdeb.

[http://www.getdeb.net/app/Nexuiz](http://www.getdeb.net/app/Nexuiz)

---

### Post by Captain_Glen on 2009-04-25
Upgraded to Jaunty Jackalope and it works now :)

---

### Post by detrate on 2009-04-25
good to hear

---

### Post by andrux on 2009-04-26
I'm trying to play nexuiz on my laptop with an ati mobility radeon x1300 but after a few second it crashes. I tried to open the x64 version (intel core2duo) but it crashes the same. Any suggest?

---


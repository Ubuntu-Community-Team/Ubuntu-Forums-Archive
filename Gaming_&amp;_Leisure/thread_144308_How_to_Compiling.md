---
title: "How to: Compiling"
date: 2006-03-14
forum: Gaming &amp; Leisure
---

### Post by CameronCalver on 2006-03-14
Cameron,

Hey I am New to linux and i would like to know how to compile first i downloaded worms of prey from [http://wormsofprey.org/download.html](http://wormsofprey.org/download.html) and i have all these files and i dont no how to install them i think it is something to do with the makefile but im not sure so can some1 plz go to that website and see if they can do it and then tell me how thanks:confused:

---

### Post by encompass on 2006-03-14
first... take a look in the files for a INSTALL file or a README file and read the text on the details of the installation...
Next odds are you will need to compile the program... that is done buy first..
Make sure that you have all the install parts to make a compile...
> sudo apt-get install build-esentials
next ... just fallow waht it says to do in the readme...
something to do with make make install, that kind of stuff.  did you fine the readme file?

---

### Post by LivnLarge on 2006-03-14
> sudo apt-get install build-esentials

i think thats a type it should be sudo apt-get install build-essential

---

### Post by CameronCalver on 2006-03-15
when u say the right sudo........ where do i right it in jus in the terminal or do i type it in a file

---

### Post by CameronCalver on 2006-03-15
also i want to install wine from [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

i went into synaptic and  added deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ then wat do i do it says its installed but where is it???

---

### Post by CameronCalver on 2006-03-15
also i want to install wine from [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

i went into synaptic and  added deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ then wat do i do it says its installed but where is it???

---

### Post by bjweeks on 2006-03-15
> when u say the right sudo........ where do i right it in jus in the terminal or do i type it in a file

termal

> also i want to install wine from [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)


sudo apt-get install wine

---

### Post by CameronCalver on 2006-03-15
when i have downloaded it will it install itself and  when it has how will i get into the program

---

### Post by bjweeks on 2006-03-15
type wine in termal

---

### Post by CameronCalver on 2006-03-15
when i have downloaded it will it install itself and  when it has how will i get into the program

---

### Post by CameronCalver on 2006-03-15
Have a look at this and c if u know what went wrong

broadband@Bird2Fish:~$ sudo apt-get wine install
E: Invalid operation wine
broadband@Bird2Fish:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 12.5MB of archives.
After unpacking 48.6MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.9-winehq-2 [12.5MB]
Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.9-winehq-2
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.9-winehq-2_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.9-winehq-2_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
broadband@Bird2Fish:~$

---

### Post by handy on 2006-03-16
Hi Cameron,

You allready have Wine installed.

Just a helpful tip, it is not best practice to split your thread, i.e. Start out with one topic & then introduce new ones.  Yes I know we see it often, & many of us are guilty of it from time to time! 

Still...  You can overwhelm your helpers, & end up with less help...

---


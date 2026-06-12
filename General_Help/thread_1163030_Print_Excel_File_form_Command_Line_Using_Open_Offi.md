---
title: "Print Excel File form Command Line Using Open Office"
date: 2009-05-18
forum: General Help
---

### Post by jsdegard on 2009-05-18
Hello 

I found somewhere that I could print a ms excel file from the command line using openoffice, as follows:

soffice -p <filename>.xls

However, I get an error:

javaldx: Could not find a Java Runtime Environment!
/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display:
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)
Failed to open display

I am trying to do this remotely.  Can someone suggest what to do here, like where to get the java environment, or how to check if I have it, or if this will even work in my case.  I am using Hardy 8.04.  Thanks in advance,

Jeremy

---

### Post by philcamlin on 2009-05-18
why are you using it in command line ???
go to applications office spreadsheet and do it from there 
way easier

or are you using a text base

i dont understand what your trying to do

---

### Post by geirha on 2009-05-18
Try
```
oocalc -p file.xls
# or
ooffice -p file.xls
```

Ah, no wait. The problem is that it is unable to connect to an X-server. Do you have a running Xserver on the computer you are running that command on?

---

### Post by jsdegard on 2009-05-18
Honestly, I don't know what an X server is, but I don't think I am running one (never set one up).  I have heard you can run a 'fake' one with some command but I'm not sure how to do that either.  I am doing this from command line because I want to be able to print a web page and excel file simultaneously, client side.  I figured I could do a system call form one of my php pages, whatever that call may be, to print the excel file.  Something like:

<?
   system("soffice -p hello.xls");
?>

Thanks for your time

Jeremy

---

### Post by geirha on 2009-05-18
Well, it requires that you have a connection to an xserver. The most typical case for that is when you have logged in graphically in ubuntu. 

I don't see any reason why printing a spreadsheet would need X though, but the open office developers probably have a reason for it. You could try asking at openoffice's forums whether it's possible to print spreadsheets with openoffice on a headless server. [http://user.services.openoffice.org/](http://user.services.openoffice.org/)

You best bet though, is probably to find some way to convert the spreadsheet to ps or pdf using php. I've tried searching for it, but so far I've only found proprietary software solutions.

---


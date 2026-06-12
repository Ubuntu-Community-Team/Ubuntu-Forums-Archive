---
title: "Diablo"
date: 2006-01-16
forum: Gaming &amp; Leisure
---

### Post by tbobo05 on 2006-01-16
I am running Wine 20050310 (thats what appeared after running wine --version) and I am trying to install Diablo.  Once I reach a certain point in the installiation, it asks to put the Diablo cd into the drive.  I have the cd in the drive but it does not read it.  Is there any config. file that I need to edit to point to my CD drive?  Also, I managed to install the spawned version of Diablo but after it initally starting, it exits with a failed status of 5.  Any ideas on what this could be?  

PS.  I am running Breezy 5.10 with  2.6.12-9-386 kernel  with a S3 Inc. 86c368 [Trio 3D/2X] as my video.

---

### Post by akurashy on 2006-01-16
ok try this

go to your terminal and type
$ winecfg
Go to the Drivers tab
press Autodetect 
press ok and try again installing

---

### Post by tbobo05 on 2006-01-16
is winecfg in the default installation package for wine? i installed winesetuptk but that still doesnt help, is the winecfg under another package name?  i have the wine repos. enabled.

---

### Post by akurashy on 2006-01-16
oh no no when you install wine it includes it 

just go to terminal and follow what i said

---

### Post by tbobo05 on 2006-01-16
i tried and it said "winecfg: command not found"   i also tried to sudo it to no avail.  where would the "winecfg" command be located? i looked in my wine directories (in both my home directory and under /usr/shar) and also  in /sbin and /bin

---

### Post by akurashy on 2006-01-16
[quote=tbobo05]i tried and it said "winecfg: command not found"   i also tried to sudo it to no avail.  where would the "winecfg" command be located? i looked in my wine directories (in both my home directory and under /usr/shar) and also  in /sbin and /bin[/quote]

hmm...

try

/usr/bin/winecfg
/usr/local/bin/winecfg

---

### Post by tbobo05 on 2006-01-16
ok, so winecfg is in /usr/bin and i ran autodetect under devices, it labled "drive d:" as /media/cdrom but I am still getting the no cd error, is there any other places u know of that needs to point towards either "drive d:" or /media/cdrom?  would it be in any of the config files of the game itself? 


[EDIT] config files in game directory contain no links to cd.  

Is there a way to copy the cd to harddrive and then make winecfg point to it as the media drive? does anyone know if that would work?

---

### Post by akurashy on 2006-01-16
ahhh i don't know then :( wish there was other people that might know the problem

---

### Post by tbobo05 on 2006-01-16
well, im going to toy with it for a while.   thanks for all your help though, at least im one step closer.

---

### Post by akurashy on 2006-01-16
ok mate i hope this help

[http://appdb.winehq.org/appview.php?versionId=49](http://appdb.winehq.org/appview.php?versionId=49)

There are instructions and it seems you can run the cds 
I hope that helps 100%

---


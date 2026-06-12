---
title: "aMSN problems"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Dramist on 2006-08-31
hey,

I just installed a fresh copy of ubuntu. Infact this is my first time ever using linux. Well 2nd but i like to forget about my horrible experience with Suse (just awful).

Ok so i how do i get aMsn installed (im using 6.06 AMD64 version) and i've tried and tried and now i give up. How do i get it?

First off

What File do i download from [http://amsn.sourceforge.net](http://amsn.sourceforge.net)

And how do i install it.

I wouldnt be having trouble right now if gaim worked but MSN changed their protocol to intergrate YIM.

---

### Post by Anonii on 2006-08-31
Just type on the terminal:
*sudo apt-get install amsn*
and you will be asked for your root password and in a couple of minutes your amsn will be completed :)

Also, please read this:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Dramist on 2006-08-31
sudo: timestamp too far in the future: Aug 31 10:03:06 2006.

The Timezones are ****** in my installation..

I chose edmonton and it said -6:00 GMT so i looked until i could find one that was -7:00 so it should be 3:38 but it isnt changed on terminal.


Edit: I fixed the timestamp issues now i get a diff error.

E: Couldn't Find package amsn

---

### Post by Anonii on 2006-08-31
Ok I'll try to help you, never really got this problem but I have read about it:

1) Using the Adjust Time & Zone from the upper right corner clock, adjust the clock either to Aug 31 10:03:06 2006 or even later than this hour/date.

2) Use the following command:
*sudo -K*

3)Use Adjust Date & Time to set the date/time back to the correct values.

4) Then try the:
*sudo apt-get install amsn*
again.

Report back, please!

---

### Post by Dramist on 2006-08-31
I fixed the timestamp issues now i get a diff error.
(did the same thing but got it off google)

E: Couldn't Find package amsn

---

### Post by Anonii on 2006-08-31
> **Dramist said:**
> I fixed the timestamp issues now i get a diff error.
(did the same thing but got it off google)

E: Couldn't Find package amsn

Execute the following command on the terminal:
*sudo gedit /etc/apt/sources.list*

and add the following lines on the document that will appear:


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse



Now execute these commands:
*sudo apt-get update*
_sudo apt-get install amsn_


Report back, please.

EDIT: Sorry, small mistake with the links. Try again >:

---

### Post by Dramist on 2006-08-31
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yer been created or moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package sould be filed.
The following information may help resolve the situation:
  amsn: Depends: imlib1 but its not installable
        Depends: libpng10-0 but it is not installable
        Depends: tcltls but it is not going to be installed
E: Broken packages

EDIT: Ok read your edit and all is well now.

Thank you all.

---

### Post by Anonii on 2006-08-31
Yeah , sorry, I screwed up the links I gave you. Try with these new that I gave you. I, basicaly, gave you the links for the previous edition...

Try again with these: 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by Dramist on 2006-08-31
Thank you, it worked.

---

### Post by Anonii on 2006-08-31
Okay :)

Also, GAIM has MSN too, and I prefer it btw, but it doesnt support webcams.

Finally, be sure to read this:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by Dramist on 2006-08-31
as i stated above,

Msn doesnt work with Gaim, because of the protocol switch to intergrate Yahoo IM

---

### Post by ramcosca on 2006-09-09
I can use Gaim to enter MSN... heck, I'm using it right now... until I can get aMSN to work, that is.


[Edit] Ok, here's an error...
```
ramcosca@ramcosca-laptop:~$ sudo gedit /etc/apt/sources.list
ramcosca@ramcosca-laptop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Get:2 http://au.archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://au.archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://au.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://au.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/restricted Sources
Get:4 http://security.ubuntu.com dapper-security/universe Packages [16.4kB]
Hit http://au.archive.ubuntu.com dapper/main Packages
Hit http://au.archive.ubuntu.com dapper/restricted Packages
Get:5 http://security.ubuntu.com dapper-security/multiverse Packages [2043B]
Get:6 http://security.ubuntu.com dapper-security/universe Sources [2253B]
Get:7 http://security.ubuntu.com dapper-security/multiverse Sources [533B]
Hit http://au.archive.ubuntu.com dapper/main Sources
Hit http://au.archive.ubuntu.com dapper/restricted Sources
Hit http://au.archive.ubuntu.com dapper-updates/main Packages
Hit http://au.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://au.archive.ubuntu.com dapper-updates/main Sources
Hit http://au.archive.ubuntu.com dapper-updates/restricted Sources
Get:8 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:9 http://us.archive.ubuntu.com dapper Release [34.8kB]
Get:10 http://us.archive.ubuntu.com dapper/universe Packages [2458kB]
Get:11 http://us.archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Get:12 http://us.archive.ubuntu.com dapper/universe Sources [975kB]
Get:13 http://us.archive.ubuntu.com dapper/multiverse Sources [46.6kB]                                       sFetched 3631kB in 1m19s (45.8kB/s)
Reading package lists... Done
ramcosca@ramcosca-laptop:~$ sudo apt-get install amsn
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  docker imlib-base imlib11 libmad0 libssl0.9.7 libungif4g sox tcltls
Suggested packages:
  mozilla galeon konqueror imagemagick imlib-progs
The following NEW packages will be installed:
  amsn docker imlib-base imlib11 libmad0 libssl0.9.7 libungif4g sox tcltls
0 upgraded, 9 newly installed, 0 to remove and 170 not upgraded.
Need to get 5073kB of archives.
After unpacking 14.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com dapper/universe imlib-base 1.9.14-29ubuntu1 [23.3kB]
Get:2 http://au.archive.ubuntu.com dapper/main libungif4g 4.1.4-1 [57.2kB]
Get:3 http://us.archive.ubuntu.com dapper/universe imlib11 1.9.14-29ubuntu1 [82.2kB]
Get:4 http://au.archive.ubuntu.com dapper/main libmad0 0.15.1b-2.1 [76.9kB]
Get:5 http://us.archive.ubuntu.com dapper/universe sox 12.17.9-1 [293kB]
Get:6 http://us.archive.ubuntu.com dapper/universe docker 1.4-3 [11.1kB]
Get:7 http://us.archive.ubuntu.com dapper/universe libssl0.9.7 0.9.7g-5ubuntu1 [2176kB]
Get:8 http://us.archive.ubuntu.com dapper/universe tcltls 1.5.0-2 [66.3kB]
Get:9 http://us.archive.ubuntu.com dapper/universe amsn 0.95-1 [2287kB]
Fetched 5073kB in 1m50s (46.1kB/s)
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 15402 package `sgml-data':
 field name `"placement' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
ramcosca@ramcosca-laptop:~$

``` Help?

I've been having problems with my installs for a week. Have reinstalled Ubuntu five times between yesterday and today. Before I tried what was on this thread, the .deb file didn't want to install, saying it had a problem with tcltls... not even Synaptic wants to work correctly on my system!!! I downloaded the updates and it doesn't want to update the system!!!!

[Edit 2} Tried the .deb again... this time it starts isntalling and simply stops the process, leaving no traces behind. :cry:

---

### Post by v6ikek6rbes on 2006-09-09
mercury dmsn is also create
;)

---

### Post by ramcosca on 2006-09-11
I'm sorry, what?

---


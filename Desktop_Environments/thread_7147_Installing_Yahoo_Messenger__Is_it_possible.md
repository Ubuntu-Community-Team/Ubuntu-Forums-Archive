---
title: "Installing Yahoo Messenger:  Is it possible?"
date: 2004-12-04
forum: Desktop Environments
---

### Post by Cleffyowns on 2004-12-04
I went to the yahoo messenger for linux area, but found downloads for redhat, debian, and freebsd.  Are any of these distros close enough for me to use to download?  I tried freebsd, and followed the installation instructions, but I figured it wouldn't work, and I was right.

Any help would be appreciated.

P.S. I want Yahoo messenger, and I don't wish to use Gaim.

---

### Post by TravisNewman on 2004-12-04
Debian. Ubuntu is a debian based distribution. I downloaded the yahoo client for Debian ans installed with no problems, but alas, I hated it and went back to Gaim

---

### Post by Cleffyowns on 2004-12-04
[I]root@ubuntu:/home/warty # dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 59754 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger
root@ubuntu:/home/warty # cd ymessenger-installer
bash: cd: ymessenger-installer: No such file or directory
root@ubuntu:/home/warty #[/I]

Hmm...?

---

### Post by Rancoras on 2004-12-04
Did you try installing the missing packages?

---

### Post by Cleffyowns on 2004-12-04
I suppose I didn't.

How would I go along doing this?  I, uh, forget.

---

### Post by TravisNewman on 2004-12-04
Open synaptic, search for the packages, install :)

If you can't find some you may need to enable universe in the apt repositories. Check the HOWTO section for how to do this.

---

### Post by poofyhairguy on 2004-12-04
> **Cleffyowns][I]root@ubuntu:/home/warty # dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 59754 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0) said:**
> 

Hmm...?

This is why Apt-get should install ALL packages. That way there is never debendacy hell.

---

### Post by Marauder1 on 2004-12-05
[QUOTE=panickedthumb]Debian. Ubuntu is a debian based distribution. I downloaded the yahoo client for Debian ans installed with no problems, but alas, I hated it and went back to Gaim[/QUOTE]

Me too i use Gaim for Yahoo and others, best choice !!!

---

### Post by rikkulinux on 2004-12-06
[QUOTE=poofyhairguy]This is why Apt-get should install ALL packages. That way there is never debendacy hell.[/QUOTE]
[FONT=Book Antiqua]
... the reason I moved from Debian to Ubuntu...

-rikku
[/FONT]

---

### Post by jakeslife on 2005-01-10
I have tried to install the debian package from Yahoo and I get:

[I]jake@c66-235-34-80:~ $ sudo dpkg -i ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 90460 files and directories currently installed.)
Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger[/I]

I don't have libssl0.9.6 installed, I have 0.9.7. Any suggestions?

---

### Post by Shaggy on 2005-01-11
[QUOTE=poofyhairguy]This is why Apt-get should install ALL packages. That way there is never debendacy hell.[/QUOTE]
That's why aptitude was developed.

aptitude install --with-recommends, made my life easy especially since one of my computers is command prompt only with debian on it.

---

### Post by anishjohnabraham on 2005-03-03
when i installed yahoo messenger on my redhat linux it shows segmentation error 
plz tell me what to do?

---

### Post by bigzak on 2005-03-03
[QUOTE=poofyhairguy]This is why Apt-get should install ALL packages. That way there is never debendacy hell.[/QUOTE]
 apt is just a front end to dpkg. If you use dpkg directly like this it has no way of using apt's dependancies. That's the way it's designed, so that you can install using the apt repository if for most things, but can get 'down and dirty' and manually install outside the automatic deps reconciliation system using dpkg.

In this particular case, running:

apt-get install libgdk-pixbuf2 libglib1.2 libgtk1.2 libssl0.9.6

and then repeating the dpkg command should work

---

### Post by topman99 on 2005-10-18
[QUOTE=Cleffyowns][I]root@ubuntu:/home/warty # dpkg -i ymessenger_1.0.4_1_i386.deb
(Reading database ... 59754 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using ymessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 Hmm...?[/QUOTE]

For libgtk error mesages try this:

Running Synaptic
1. Click the K button on the menubar again.
2. Click System
3. Click Synaptic Package Manager

Installing the Missing Files with Synaptic
1. Click on search
2. On the search box type, libgtk
3. You will notice that synaptic performed a smart search. It displayed all the packages that contained the letters "libgtk".
4. Look for libgtk2.0-0
5. Select it.
6. Right click
7. Select mark for install
8. Then click the Apply button in the synaptic toolbar

For libssl0.9.6 error messages follow this step:

The key for this problem is to install this file again bcoz in libssl0.9.7 ymsenger is removed...

So download the file [http://packages.debian.org/oldstable/libs/libssl0.9.6](http://packages.debian.org/oldstable/libs/libssl0.9.6) then follow this step: 
Open Konsole( Terminal Program ) then type:
$sudo -s 
Type your password
#dpkg -i ymessenger 1.0.4_1

To run yahoo mesenger type:
#/usr/bin/ymessenger

i hope it can help...



:smile:

---

### Post by mzanfardino on 2006-11-14
I too was having trouble installing the Yahoo!Messenger.  It started out much the same as the first post with a litany of errors.  After reading through this thread, I managed to get so far as to reduce the dependancy error to xlibs.  However, no matter what I tried I couldn't find a way around it (yes, I even went to a debian oldsource library, but to no avail). 

Then I started hunting through previously uninstalled utilities and I came across a real bute: alien. **"alien is a program that converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. If you want to use a package from another linux distribution than the one you have installed on your system, you can use alien to convert it to your preferred package format and install it. It also supports LSB packages."** (man alien)

I installed alien, double checked that I had rpm installed, then downloaded the rpm version of yahoo!messenger and converted it to a deb file (*alien -c rh9.ymessenger-1.0.4-l.i386.rpm*).  This created a new deb file (_ymessage_1.0.4-2_i386.deb_) which I could then install with *dpkg -i ymessage_1.0.4-2_i386.deb*.  After that it was a simple matter to run *ymessage* and away I went!

Now, just for the helluv it, I tried to use rpm to install the original rpm, but as you might expect, this was pointless.  NOTE: I'm running Ubuntu 6.06 desktop.

My only disappointment (thus far)  with ymessenger is that it does not support SMS messages in the linux version.  Anyone have any suggestions for alternate IM tools that does support SMS messaging?

---

### Post by t1nt1n on 2006-12-17
HI, HERE IS HOW YOU INSTALL YAHOO-MESSENGER ON UBUNTU, WITHOUT GOING THROUGH ALL THAT DEPENDENCY HELL !   -
1. user$sudo apt-get install alien  #install's alien to convert rpm packages to .deb#
2. user$sudo apt-get install libgdk-pixbuf2  #a package needed by messenger#
3. Download the following - rh9.ymessenger-1.0.4-1.i386.rpm from here - [http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)
4. user$sudo alien -c rh9.ymessenger-1.0.4-1.i386.rpm  #converts it to a debian package#
6. user$sudo dpkg -i ymessenger-1.0.4-i386.deb  #installs the package#
8. user$ymessenger    #starts yahoo messenger#

---

### Post by kost@s on 2006-12-25
Hello everybody! i m trying to install yahoo messenger on Ubuntu 6.10 and I m getting the following  error.  

[HTML]root@Kostas-laptop:~# dpkg -i /home/kostas/Desktop/YahooMessenger_1.0.4_1_i386.deb
(Reading database ... 124219 files and directories currently installed.)
Preparing to replace ymessenger 1.0.4_1 (using .../YahooMessenger_1.0.4_1_i386.deb) ...
Unpacking replacement ymessenger ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger[/HTML]

I tried to locate xlibs package in the package manager and on the net but I cant find it anywhere. Can you plz gimme a hint? Thnx!

---

### Post by iamhugeinjapan on 2006-12-25
The official Yahoo Messenger for Linux is very very old and unmaintained. I really wish they would just take that page down or update it.

You will get more functionality from Gaim. You can also use GYachI if you require the more fancy Yahoo features.

---

### Post by kost@s on 2006-12-25
Thnx a lot for your answer! That s what I figured out as well...This page of yahoo messenger is not updated (just like the messenger) and it is more confusing than useful. I just thought to give it a try....So, I ll turn more to Gaim and GYachI (since trillian doesnt work on linux either).....

---

### Post by _hadi_ on 2007-05-08
Use this modified package it's good.
I'd installed in both on Edgy and Feisty :)

---

### Post by Shaggmire on 2007-06-26
yeah i have the same problem, and i cant find libssl0.9.6 anywhere, i have libssl0.9.7 and libssl0.9.8, but they dont work with yahoo messenger, and none of the mirrors [here]("http://packages.ubuntu.com/breezy/oldlibs/libssl0.9.6") work, i need help

---

### Post by dedy on 2007-12-27
> **t1nt1n said:**
> HI, HERE IS HOW YOU INSTALL YAHOO-MESSENGER ON UBUNTU, WITHOUT GOING THROUGH ALL THAT DEPENDENCY HELL !   -
1. user$sudo apt-get install alien  #install's alien to convert rpm packages to .deb#
2. user$sudo apt-get install libgdk-pixbuf2  #a package needed by messenger#
3. Download the following - rh9.ymessenger-1.0.4-1.i386.rpm from here - [http://messenger.yahoo.com/unix.php](http://messenger.yahoo.com/unix.php)
4. user$sudo alien -c rh9.ymessenger-1.0.4-1.i386.rpm  #converts it to a debian package#
6. user$sudo dpkg -i ymessenger-1.0.4-i386.deb  #installs the package#
8. user$ymessenger    #starts yahoo messenger#

Hi t1nt1n,

Thanks so much with your brilliant idea.
my yahoo messenger is work now in ubuntu gutsy 10.7.
I have been searching around to find xlibss for ymessenger-1.0.4-i386.deb.
Now my problem is solved, but when I restart my PC, I could not run yahoo messenger
in user level **again**. There is an error : 
[B]dedy@P4-XXX:~$ ymessenger #starts yahoo messenger#
Segmentation fault (core dumped)
dedy@P4-XXX:~$ [/B]

In **root level**, yahoo messenger **is running okey.**

What should I do?I am new in Linux environment.

Regards,
Dedy

---

### Post by dedy on 2007-12-27
try this :
[http://packages.debian.org/oldstable/libs/libssl0.9.6](http://packages.debian.org/oldstable/libs/libssl0.9.6)

---

### Post by jetta on 2007-12-27
> **Marauder1 said:**
> Me too i use Gaim for Yahoo and others, best choice !!!


I just use pidgin, that's all. Don't want to have headache..

---


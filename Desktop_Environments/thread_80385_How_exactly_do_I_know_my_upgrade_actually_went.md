---
title: "How exactly do I know my upgrade actually went?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Zarkoth on 2005-10-22
Well, i followed the directions off of another forum....I can provide the link later if needed, which said to go to your sources.list file and basically replace Hoary with Breezy...I did, and I also commented the backports and other extras for the time being, to less complicate things...I think, lol

So I did that and then re-booted and Software Updates had plenty of updates for me, but also said that it couldn't do certain packages, and I should use Synaptic or apt-get for them.  So I used Synaptics Smart Upgrade thinger, and that did its thing, and rebooted.  Nothing is different, and nothing is wrong.  The only thing that is different is there are not software updates to my knowledge currently awaiting me.


So what'd I do wrong? :)


P.S. - I did a system back-up beforehand, so if I did anything massively wrong, although I doubt that, I could restore

Thanks in advance for any help!

---

### Post by davmac on 2005-10-22
I'm not sure what you did wrong but I'll tell you what I did.

Start with the same as you, updated sources.list changing all hoary to breezy and commented out the backports. Then in a terminal ran

sudo apt-get update
sudo apt-get dist-upgrade

...and that was it.

Hope this helps,

Dave Mac

---

### Post by GeneralZod on 2005-10-22
Typing 
```

uname -a

```

will tell you the name of the kernel, at least (it should be 2.6.12 got Breezy; 2.6.10 for Hoary).

In KDE, the current version of KDE is accessible from every app; I'm not sure if GNOME has the same feature, though.

---

### Post by Zarkoth on 2005-10-22
Hmm.....I did the "uname -a" command, and I still have Hoary, which is odd.  If I run apt-get again, with update and dist-upgrade, is says everything's up to date.....

So how come I still have Hoary?

---

### Post by mit on 2005-10-22
What did you use to back up ubuntu and all your files?

---

### Post by Xian on 2005-10-22
Issue this command please:

```
$ cat /etc/issue
```

Here is my output:
```
$ cat /etc/issue
Ubuntu 5.10 "Breezy Badger" \n \l
```

---

### Post by Zarkoth on 2005-10-22
Xian - my output after using that command was 

```
zarkoth@ubuntu:~$ cat /etc/issue
Ubuntu 5.04 "Hoary Hedgehog" \n \l

```

and I used the method described in this thread to backup everything - 

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

---

### Post by Xian on 2005-10-22
Well, let's have a look at your source repos.
Post the output of an update and upgrade command:

$ sudo apt-get update
$ sudo apt-get dist-upgrade

---

### Post by Zarkoth on 2005-10-22
Yes, let's have a look, shall we?

```

zarkoth@ubuntu:~$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://archive.ubuntu.com breezy Release
Get:4 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://security.ubuntu.com breezy-security/multiverse Sources
Hit http://us.archive.ubuntu.com breezy/universe Sources
Fetched 19.8kB in 1s (10.7kB/s)
Reading package lists... Done

```

and....

```


zarkoth@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  3ddesktop dialog gnome-gv gstreamer0.8-mad gtkhtml3.6 guarddog kaffe
  kaffe-pthreads lesstif2 libcurl3 libfaad2-0 libgal2.4-0 libgal2.4-common
  libgtkhtml3.6-18 libneon23 libnetpbm10 libssl0.9.7 libsvga1 mplayer-386
  netpbm numlockx openoffice.org openoffice.org-bin openoffice.org-gtk-gnome
  openoffice.org-l10n-en sox supertux wget workman
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
zarkoth@ubuntu:~$


```

---

### Post by Xian on 2005-10-22
Looks proper to me. You have a few held back pkgs but nothing which is system imperative. For a full system upgrade that isn't very many. I'm not devel savvy on how an release upgrade impacts the naming of the machine, but you are certainly running a Breezy system.

As for the kernel issue, I would suspect this is something you would need to install manually in Synaptic. You probably have a kernel linked to an arch build (like 386, k7, and so on) that did not get updated properly.

---

### Post by Zarkoth on 2005-10-22
So if I'm certainly running Breezy now, what exactly are all the differences between the two?  It seems to look and act just like Hoary did....

---

### Post by kotatsu on 2005-10-22
Try running:
```
apt-get -f install
```
If you have something holding up packages that will probably work out the problems. When you can run:
```
apt-get install ubuntu-desktop linux-386
```
(or kubuntu-desktop if you use KDE) with your current sources and it doesn't install anything or say anything is held back or broken, the upgrade is complete. You'll probably want to use linux-686 or linux-k7 instead, though.

---

### Post by Zarkoth on 2005-10-23
Hmm....I guess I must be upgraded.....

```

zarkoth@ubuntu:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.

```

and....

```

zarkoth@ubuntu:~$ sudo apt-get install ubuntu-desktop linux-686
Reading package lists... Done
Building dependency tree... Done
Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-desktop has no installation candidate

```

I tried with linux-k7 as well, but I got the same results.

Is something wrong or am I just completely upgraded?

---

### Post by kotatsu on 2005-10-23
Looks like you're missing some sources. Here's my (working) sources.list file:

```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe
deb http://security.ubuntu.com/ubuntu breezy-security universe

#deb http://us.archive.ubuntu.com/ubuntu breezy multiverse
#deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse



#deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

#deb-src http://us.archive.ubuntu.com/ubuntu breezy universe
#deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe

#deb-src http://us.archive.ubuntu.com/ubuntu breezy multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

Just paste all that in and uncomment the extra repositories you want (I usually don't use deb-src or multiverse respositories).

---

### Post by Zarkoth on 2005-10-23
Alright, I backed up my existing sources and pasted in all that....
then I ran apt-get update, and apt-get -f install

here's what i got - 

```

zarkoth@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 740 not upgraded.

```

Then I did  that 'apt-get install ubuntu-desktop linux-686'

and got this - 

```

zarkoth@ubuntu:~$ sudo apt-get install ubuntu-desktop linux-686
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: bluez-pcmcia-support but it is not going to be instal led
                  Depends: bluez-pin but it is not going to be installed
                  Depends: bluez-utils but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: evolution-plugins but it is not going to be installed
                  Depends: firefox-gnome-support but it is not going to be insta lled
                  Depends: gnome-app-install but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: libgl1-mesa but it is not going to be installed
                  Depends: libpt-plugins-v4l but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: notification-daemon but it is not going to be install ed
                  Depends: openoffice.org2-gnome but it is not going to be insta lled
                  Depends: serpentine but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Broken packages

```

How do I get all those dependencies good-ified?

---

### Post by Zarkoth on 2005-10-23
Btw, I just remembered, isn't Synaptic supposed to help most dependency hellaciousness?  So i went and had Synaptic re-load the package info and hit smart upgrade, which is currently running, and since it has a very large list of things to do, i think it may be correct now......

Who knows, I'm kinda running headlong at anything that looks like it could turn out as progress, making a full-system backup is incredibly liberating!

I'll let you know what happens after Synaptic's done.

---

### Post by Zarkoth on 2005-10-24
And Synaptic's done...and there are a few signs that point to Breezy on my computer.  For one thing, both Hoary and Breezy show up on GRUB, I was a little amused at that, I haven't yet tried Hoary, so I wonder what would happen?

I also noticed the login splash screen was different, and looked kinda cool....

but while Synaptic was doing its thing, I got several errors, and quite a lot of times...

here's one, and often times this one happened several times in a row....

```

perl: warning: Falling back to the default locale ( “C” ).
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = ”en”,
	LC_ALL = 	(unset),
	LANG = “en.US.UTF-8”,
      are supported and installed on your system.

```

And another....

```

dpkg:  Warning - not able to delete old directory 'directory goes here' : Directory not empty

```

and this one....

```

Gdk – WARNING **;  locale not supported by C library.
	using the fallback 'C' locale at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 47

```

and finally, the last few lines that it ran through the terminal before finishing were....

```


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_3.2.1-1_i386.deb
  Error reading from server - read (104 Connection reset by peer) [IP: 130.239.18.137 80]

```

..Hmmm

I also noticed that I'm still using OOo 1.1....should it be version 2 by now?

---


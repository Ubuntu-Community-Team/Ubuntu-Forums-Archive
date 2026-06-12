---
title: "Taking the plunge."
date: 2007-12-11
forum: Debian
---

### Post by tekwerx on 2007-12-11
Hey all.  I'm kinda tired of being spoon-fed by Ubuntu, so Im going straight to the base - Debian.  I would like to install Sid, but I am unable to find Sid anywhere on a CD.  I'm finally going to go all out and learn how to do my own system, but I am unsure as to how to start.  I'd like to get Sid on here, but not too sure on how to go about doing that.  NetINST CD?  Do I need to install Etch or Leny then dist upgrade?  

Oh, and before anyone suggests Sidux - Ive tried it.  Every time I try to install the nvidia drivers, the whole system crashes.  Im using an old GeForce4 MX 420, so it shouldnt be too hard.  At any rate, Id like to start from scratch, so to speak.  Sorry to ramble.  Thanks in advance.

---

### Post by matthew on 2007-12-11
I'm sure someone will correct me if I am wrong, but to my knowledge there is no way to install Sid directly. I would suggest downloading the testing version, install that, then upgrade to Sid if that is what you want to run (but I don't recommend actually running Sid, it is unstable, sometimes highly unstable, and sometimes causes breakage).

For more:
[http://debian.org](http://debian.org)
[http://www.us.debian.org/distrib/](http://www.us.debian.org/distrib/)
[http://www.us.debian.org/releases/](http://www.us.debian.org/releases/)
[http://www.us.debian.org/releases/unstable/](http://www.us.debian.org/releases/unstable/)

EDIT: for info on how to install the testing version: [http://www.us.debian.org/devel/debian-installer/](http://www.us.debian.org/devel/debian-installer/)

---

### Post by CyberBob on 2007-12-11
Sid is always the unstable version of Debian by definition.  If you are looking for stability, your best bet is to install Etch (released as stable in April, 2007).  It is available as a Net install (a single CD will get you going).  I've even installed this distro from a few floppies! I have it running on two servers and it is rock solid.

---

### Post by Antman on 2007-12-12
> **tekwerx said:**
> 
Oh, and before anyone suggests Sidux - Ive tried it.  Every time I try to install the nvidia drivers, the whole system crashes.

hmmm... interesting. I'm curious how you installed the nVidia drivers?!? I have never had an issue using the 'smxi' script to install nvidia drivers in Sidux.

At any rate, as one poster already mentioned, you don't install sid (unless it's sidux), instead u just alter your sources.list to point to the unstable repos and then do a dist-upgrade (or in Sidux just run the 'smxi' script).

---

### Post by angryfirelord on 2007-12-12
> **tekwerx said:**
> Oh, and before anyone suggests Sidux - Ive tried it.  Every time I try to install the nvidia drivers, the whole system crashes.  Im using an old GeForce4 MX 420, so it shouldnt be too hard.
In the smxi script on the drivers installation, you must select the *older-nvidia-c* driver. The MX cards do not work with 100 series driver.

Currently, Sidux is the only active Debian Sid CD that I know of.

---

### Post by tturrisi on 2007-12-13
You CAN install Sid directly using the net-install.
See my guide here:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

---

### Post by tekwerx on 2007-12-13
> **tturrisi said:**
> You CAN install Sid directly using the net-install.
See my guide here:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

Rock on, thanks a ton!  I'm doing it now.  Let you know how it turns out!

---

### Post by tekwerx on 2007-12-13
I'm back!  I am now runing Sid!  IM UNSTABLE!  *cackle*  *eye twitch*

Sweet!  This isnt so tough to learn.  So far.  LOL

---

### Post by matthew on 2007-12-14
Cool. Let us know how it goes, and above all, have fun!

---

### Post by Antman on 2007-12-14
> **tturrisi said:**
> You CAN install Sid directly using the net-install.
See my guide here:
[http://members.cox.net/tonyt/d830](http://members.cox.net/tonyt/d830)

Oh yes.... good ole net-install. Thanks for the guide, I'll have to try it on my next debian build. :guitar:

---

### Post by tekwerx on 2007-12-14
> **matthew said:**
> Cool. Let us know how it goes, and above all, have fun!

I am having fun!  So far, no problems except for Compiz-Fusion.  I've got it working, but its acting oddly.  It acts jerky sometimes, sometimes I get a white screen, and when I open any dialogs (right click) or open any windows, theyre blank until I resize the window.  I dunno whats going on.  I've tried to find out, but no answers.  Anyone know?  Again, thanks...learning this is a blast, and plain ol Debian is way faster than anything else I've used yet.  

BTW, my wife says I need to go back to windows....lol.  Uh, no, dear.

---


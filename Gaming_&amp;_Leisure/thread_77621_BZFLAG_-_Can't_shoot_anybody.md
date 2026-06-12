---
title: "BZFLAG - Can't shoot anybody"
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by Bitchcassidy on 2005-10-17
Hi all!
I upgrade to breezy this week, but i have some problems with [B]Bzflag:
[/B]The game is launched without problem but i can't shoot anybody except myself :confused:

Others can kill me but me no.
Does someone have experienced this problem ??
 
Thanks in advance !

---

### Post by DariusTriplet on 2005-10-17
I've been having the same problem; unfortunately, I have no idea why it happens.

Since the game is at 2.0.4, and the apt-get version of it is 2.0.2, perhaps it's a version conflict?

---

### Post by Bitchcassidy on 2005-10-17
Hi, 

I think it's a version problem too, but I try the 2.02, 2.04 and cvs versions and all have the same error.
Argh !!!

---

### Post by dbh on 2005-10-22
I have the same problem. It started when I upgraded to Breezy a month or so ago. I've tried the Ubuntu package, and I've compiled 2.0.2 and 2.0.4 -- still can't shoot anybody.

---

### Post by Neeko on 2005-10-23
Check your lag (lagstats). There is a bug with one of the clients (2.0.2?) that produces enormous variance in lag (the plus/minus value after the lag time in ms). The latest version has fixed this, you'll need to download source.

---

### Post by dbh on 2005-10-28
[QUOTE=Neeko]Check your lag (lagstats). There is a bug with one of the clients (2.0.2?) that produces enormous variance in lag (the plus/minus value after the lag time in ms). The latest version has fixed this, you'll need to download source.[/QUOTE]

I'm using the 2.0.4 client compiled from source. And I do get wacky lagstats (e.g., 54 +/- 6042 ms).

---

### Post by henriquemaia on 2005-11-02
Having the same problem here. 

:cool: Even if I cannot solve this, at least I feel better now, as I was thinking there was some kind of problem with my brain and reflexes...

---

### Post by mencial on 2005-11-20
Hello to all.

This bug will be solved for Breezy when BZFlag 2.0.4 appears in Breezy Backports repository. Until then, you can use a temporary package I have built myself.

WARNING: This is my first .deb package. I have been playing successfully with it for some time, but I do not guarantee anything.

[http://librarian.launchpad.net/1137724/bzflag-2.0.4.20051017_2.0.4.20051017-1_i386.deb](http://librarian.launchpad.net/1137724/bzflag-2.0.4.20051017_2.0.4.20051017-1_i386.deb)

Here is the explanation of what I did:

[https://launchpad.net/distros/ubuntu/+source/bzflag/+bug/3610](https://launchpad.net/distros/ubuntu/+source/bzflag/+bug/3610)

To use it, you might have to uninstall Breezy's BZFlag; and when the official 2.0.4 appears in backports, uninstall my package.

---

### Post by zaddik01 on 2005-11-28
[QUOTE=henriquemaia]Having the same problem here. 

:cool: Even if I cannot solve this, at least I feel better now, as I was thinking there was some kind of problem with my brain and reflexes...[/QUOTE]
I am running AMD64 and I have the same problems. I have installed the 2.02 and 2.04 (backport). I have also built the packages myself from the csv and it still doesn't work. Is there any hope for this???

---

### Post by incompetence on 2005-12-22
Had the same problem.
It seem that gcc 4.0 is the culprit.
[http://my.bzflag.org/bb/viewtopic.php?t=6212](http://my.bzflag.org/bb/viewtopic.php?t=6212)
I tried that and now my bzflag works.
I open an bug in bugzilla.

---

### Post by linuxted on 2006-07-13
Just wanted to let you know that this bug appears to still be around in Dapper 64.  For Dapper 32 it doesn't seem to be a problem.  And the lag is humungous in the 64 version.

Hope it gets fixed someday

---


---
title: "Buying the Dell 1525N,  Upgrade Adivce"
date: 2008-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheRoamingLinux on 2008-06-16
I am buying the Dell 1525N.  It comes, of course, preloaded with Ubuntu 7.0 :)

Would I be better off using the computer with release 7.0. or is it a good idea to upgrade to the current release?

Would upgrading create a whole new set of issues?:confused:

---

### Post by Muflon on 2008-06-17
Hi TheRoamingLinux

I am running 8.10 on a Dell 1525 dual boot with Vista and verything works fine.

I don't think that upgrading would cause you any real issues but my expirience was with a fresh install.

Muflon

---

### Post by danbodoh on 2008-06-17
I think you should upgrade to 8.04, then turn on the hardy-updates software source and upgrade to that.

I had problems with Suspend/REsume on the 1525 on 7.10 that cleared up with 8.04.  Yesterday's release of the -19 kernel in hardy-updates now allows the 1525 to suspend/resume and retain ondemand cpufreq scaling.

And the ipod nano works in 8.04, but not in 7.10.

See [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04) for fixes to a few small things when doing the upgrade.

Dan Bodoh

---

### Post by fragos on 2008-06-17
Buying an Dell Linux model insures you have Linux compatable components. I did a clean install of 8.04 on my 1420n and everything worked well including all the problem areas I'd run into with 7.04 and 7.10. Compiz now works with the Intel video chip set and both susspend and hibernate function properly. You might however familiarize yourself with the shipped version of Ubuntu before installing 8.04. I also recommend the clean install since that can avoid the potential problems that arrise because of the complexity of the upgrade process.

---

### Post by bryncoles on 2008-06-18
i got a dell 1525 in the post yesterday, and upgraded through update manager. the only issue i had so far was the sound cut out, and if you actually read the instrutions on the website then its very easy to fix - just cut and paste some terminal commands. so i recommend the upgrade!

---

### Post by veritas366 on 2008-06-18
I started working at Dell a month and a half ago (one of the guys who answers the phone for people buying new systems) and so I subscribe to the dell linux email list, which I recommend.  Not real heavy traffic but dell engineers do answer.

Big issue with the upgrade seems to be wifi for some people and it seems specific to a particular kernel.  I know Dell will have their official upgrade cd eventually.  I'd say that if Gutsy is working for you, hang on for that unless you just like to tinker.  If so, then join the Dell email list:

[http://lists.us.dell.com/mailman/listinfo/linux-desktops](http://lists.us.dell.com/mailman/listinfo/linux-desktops)

or via sending an email with subject line "help" to:

[email]linux-desktops-request@dell.com[/email]

I admit I'm not monitoring the list in great detail so I'm honestly not sure how many of the problems were based on Dell systems installed with Ubuntu as OEM vs. people simply installing it on their own systems.

---

### Post by openprivacy on 2008-12-21
I bought the 1525N and suspend/hibernate (shutting down the disk, etc. when the lid is closed) has never worked.  I think the screen blanks (is this "standby"?) but disk activity is still occurring and one can e.g. ssh into the box when the lid is closed.

Also, just leaving the lid open for (say) an hour with no activity and the unit freezes and a reboot is necessary.

Both these problems occur with 8.04 (original OS) - should I upgrade to 8.10?  Or is there some other place that has answers to this question?

Other than these issues, it's a fine machine.

---

### Post by llamakc on 2008-12-21
Suspend works fine for me in 8.10 on my 1525.

---

### Post by Denny Johnson on 2008-12-21
openprivacy....are you aware of the setting adjustments at system/preferences/power mgmt?
GL

---


---
title: "For those who have ATI/fglrx and are interested in Gnome 3"
date: 2011-11-05
forum: Desktop Environments
---

### Post by typhoon_tip on 2011-11-05
Just a brief note to all of you that the newest 11.10 Catalyst + Driver from AMD website is still not working totally properly with Gnome 3. It is better tough, as the desktop now appear to be totally correct, but screen still flashing from time to time. It is also possible that some setting need to be adjusted, but I am not using Gnome 3 nor I intend to.

Performances in Unity tough seems to be slightly better, with higher frame rates on heavy load and less GPU usage at idle.

---

### Post by reloweb on 2011-11-15
I have the same problem! I hope they will fix this in the next version...

---

### Post by ratcheer on 2011-11-15
When will the new driver hit the repos? It was released early yesterday morning, but 30 hours later, it's still not there.

Tim

---

### Post by typhoon_tip on 2011-11-15
> **ratcheer said:**
> When will the new driver hit the repos? It was released early yesterday morning, but 30 hours later, it's still not there.

Tim

You mean in Ubuntu reps or AMD site ? In AMD site is there but somehow not displayed if you download trough their interface... I got the link from the wiki.

---

### Post by typhoon_tip on 2011-11-15
By the way, situation is getting out of hand seems:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

So many months, still not fixed. And also Gnome 3 developers, my God... they never contacted ATI up to November 2nd, 2011.

:confused::confused:

---

### Post by ratcheer on 2011-11-16
> **typhoon_tip said:**
> You mean in Ubuntu reps or AMD site ? In AMD site is there but somehow not displayed if you download trough their interface... I got the link from the wiki.

I mean the Ubuntu repos. I got this in the email from Ubuntu-changes two days ago, now:

> Date: Mon, 14 Nov 2011 06:18:40 -0000
From: Alberto Milone <[EMAIL="alberto.milone@canonical.com"]alberto.milone@canonical.com[/EMAIL]>
To: [EMAIL="oneiric-changes@lists.ubuntu.com"]oneiric-changes@lists.ubuntu.com[/EMAIL]
Subject: [ubuntu/oneiric-updates] fglrx-installer-updates
        2:8.902-0ubuntu0.1      (Accepted)
Message-ID: <[EMAIL="20111114061840.5731.97144.launchpad@wampee.canonical.com"]20111114061840.5731.97144.launchpad@wampee.canonical.com[/EMAIL]>
Content-Type: text/plain; charset="utf-8"

fglrx-installer-updates (2:8.902-0ubuntu0.1) oneiric-updates; urgency=low

  * New upstream release (11.10) (LP: #889041).
  * debian/[dkms.conf.in]("http://dkms.conf.in/"):
    - Drop the non-functional OBSOLETE_BY variable.
Also, on Phoronix, it says AMD has released catalyst 11.11.

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTc](http://www.phoronix.com/scan.php?page=news_item&px=MTAxNTc)

Tim

---

### Post by typhoon_tip on 2011-11-17
Uhm, they refer to the package "fglrx-installer-updates", which strangely need to be installed from Jockey as if it was a separate driver (it never worked for me when I tried...). I have long not been using repo drivers, and haven't tried to update the driver with those "post-release updates" stuff... :)

---

### Post by ratcheer on 2011-11-17
Maybe that's why I'm not getting the new driver. I have fglrx and fglrx-amdcccle installed via aptitude, and they usually just update by running aptitude update and aptitude safe-upgrade. Hmmm...

Tim

---

### Post by ratcheer on 2011-11-17
Ok, I broke down and did the manual fglrx installation. I carefully followed the instructions from earlier in this thread and, for the first time (for me), it worked. So, I am now up to Catalyst 11.11 and no longer need to worry about 11.10 getting to the repos.

Edit - Oops, wrong thread. The instructions were in [http://ubuntuforums.org/showthread.php?t=1873072](http://ubuntuforums.org/showthread.php?t=1873072)

The one thing out of the ordinary that I had to do was, when I purged fglrx at step 1, it also removed dkms. I then reinstalled dkms, successfully, and continued following the instructions.

Thanks,
Tim

---

### Post by typhoon_tip on 2011-11-18
> **ratcheer said:**
> The one thing out of the ordinary that I had to do was, when I purged fglrx at step 1, it also removed dkms. I then reinstalled dkms, successfully, and continued following the instructions.

Probably because you did not have any other special kernel module installed than FGLRX :)

By the way, those instructions are incomplete. It is much safer to use the complete set by restoring ATI stock driver and XORG before reinstalling over a new FGLRX (and a reboot between each install).

[http://ubuntuforums.org/showpost.php?p=11439757&postcount=2](http://ubuntuforums.org/showpost.php?p=11439757&postcount=2)

Not because is my message lolll, just because I did it so many times by today that I almost remember each command by memory !

---


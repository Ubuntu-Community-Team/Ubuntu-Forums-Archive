---
title: "How to lock down Gnome for guest users"
date: 2010-05-21
forum: Desktop Environments
---

### Post by meadmarc on 2010-05-21
Good evening!

I am volunteering to set up a computer lab for a small private school on an extremely limited budget.  I love Ubuntu for my home, and on my server at work, but have never used it in a school before.

I would like to "lock down" all the control panels, pretty much everything except for a few applications (open office, firefox, and some educational games, of course). I don't want the students (who will be automatically logged in as guests) to be able to make changes, or unintentionally mess things up.

Is there an easy way to do this?  

Alternatively, at the public school I work at, we use Windows (sigh) that has been "frozen" using a program called Deep Freeze (similar to windows "steady-state"), which causes any changes a user my make revert back to default when rebooted.  Is there a Linux equivalent?  That may work too!

---

### Post by Jakiejake on 2010-05-21
Try Edubuntu [http://edubuntu.org/](http://edubuntu.org/)
It is made for schools

---

### Post by bobzr on 2010-05-21
Sabayon should help : [http://live.gnome.org/Sabayon/](http://live.gnome.org/Sabayon/)
*Sabayon is geared towards anyone who has need of providing a standardized GNOME desktop to their end users. Teachers who administer labs, Libraries, and Businesses all have need to have a "locked down" desktop, and can make good use of Sabayon *

---

### Post by Jakiejake on 2010-05-21
> **bobzr said:**
> Sabayon should help : [http://live.gnome.org/Sabayon/](http://live.gnome.org/Sabayon/)
*Sabayon is geared towards anyone who has need of providing a standardized GNOME desktop to their end users. Teachers who administer labs, Libraries, and Businesses all have need to have a "locked down" desktop, and can make good use of Sabayon *

Edubuntu Is focused mainly on education
Saybon hogs all your ram and cpu and if you have a graphics card it will hog that too!
And Well you know what the school computers are like

---

### Post by meadmarc on 2010-05-22
Sabayon appears to be just what I am looking for, although the thin-client model offered by Edubuntu will also need some consideration.

I did not notice a difference in performance; the computers are about 5 years old, and have 1 GB of ram.  Really, them seem to do okay with it running, and I can switch back to a privileged user easily, which is nice.  

Are there other options that would be less RAM intensive if this does become a problem?

---

### Post by Jakiejake on 2010-05-23
> **meadmarc said:**
> Sabayon appears to be just what I am looking for, although the thin-client model offered by Edubuntu will also need some consideration.

I did not notice a difference in performance; the computers are about 5 years old, and have 1 GB of ram.  Really, them seem to do okay with it running, and I can switch back to a privileged user easily, which is nice.  

Are there other options that would be less RAM intensive if this does become a problem?

Try Edubuntu with a XFCE Interface [http://en.wikipedia.org/wiki/Xfce](http://en.wikipedia.org/wiki/Xfce)
Or xbuntu [http://www.xubuntu.org/](http://www.xubuntu.org/) (Ubuntu with Xfce interface) Great for old pc's or pc's with low specs

---

### Post by Jakiejake on 2010-05-23
Oh and don't forget the lightweight ubuntu [http://lubuntu.net/](http://lubuntu.net/) it uses LXDE

---

### Post by meadmarc on 2010-05-27
Okay-  

I have discovered the wonder of the thin client, and am now running Gnome over LTSP.

This may be off the radar of the point of this post, but I am now trying to minimize the image footprint to maximize the number of clients I can have.

But here goes:

1.  Does LXDE allow me to make menu profiles to keep kids out of things I don't want them to have?  (Does Sabayon work with it, or something similar?)

2.  Would that LXDE increase the number of clients I can connect in an appreciable way?

Thanks in advance!

---

### Post by pzkfw on 2010-05-27
Just a thought:

Most of the gnome's control panels/configuration editors are actually packages.  If you apt-get remove all the packages then they can't change anything unless they knew EXACTLY where to edit a file in the terminal which is highly unlikely.

---

### Post by meadmarc on 2010-05-27
Actually, I had begun thinking about that myself....  So I could uninstall anything I don't want them to have access to, and all the Admin items are password protected anyway.  

Actually, I could go over a lot of the packages and uninstall unnecessary processes and such to try to lighten the load.

And actually the lockdown editor lets me kill their command line access so that's one less risk (not much of one anyway, the school only goes as far as 6th grade!)

Thanks!

Know of any "dead weight" that I should look at?

Thanks!

---

### Post by Jakiejake on 2010-05-28
> **meadmarc said:**
> Actually, I had begun thinking about that myself....  So I could uninstall anything I don't want them to have access to, and all the Admin items are password protected anyway.  

Actually, I could go over a lot of the packages and uninstall unnecessary processes and such to try to lighten the load.

And actually the lockdown editor lets me kill their command line access so that's one less risk (not much of one anyway, the school only goes as far as 6th grade!)

Thanks!

Know of any "dead weight" that I should look at?

Thanks!

Aye I was doing CMD on windows at like grade 5 or earlier as far as I can remember

---

### Post by mike555 on 2010-05-28
You could shut down services you don't use in ;   System > Preferences > Startup apps .... things like Ubuntuone, brail, bluetooth, etc.

---

### Post by hok00age on 2010-08-13
> **meadmarc said:**
> Good evening!

I am volunteering to set up a computer lab for a small private school on an extremely limited budget.  I love Ubuntu for my home, and on my server at work, but have never used it in a school before.

I would like to "lock down" all the control panels, pretty much everything except for a few applications (open office, firefox, and some educational games, of course). I don't want the students (who will be automatically logged in as guests) to be able to make changes, or unintentionally mess things up.

Is there an easy way to do this?  

Alternatively, at the public school I work at, we use Windows (sigh) that has been "frozen" using a program called Deep Freeze (similar to windows "steady-state"), which causes any changes a user my make revert back to default when rebooted.  Is there a Linux equivalent?  That may work too!
Follow my thread:
[http://ubuntuforums.org/showthread.php?t=1550489](http://ubuntuforums.org/showthread.php?t=1550489)

---


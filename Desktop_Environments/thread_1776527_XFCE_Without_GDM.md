---
title: "XFCE Without GDM"
date: 2011-06-06
forum: Desktop Environments
---

### Post by CJxD on 2011-06-06
Hi there!

I'm making a Home Theatre OS, and I would like my XFCE ubuntu desktop to load up automatically without the use of GDM.
This is because once remastered, the GDM cannot automatically log in until it's been set up to again. And the fact I removed all the GNOME icons which took up 50MB of space, so now the GDM interface is all glitchy xD

So yeah, I've found several ways of doing that, but since none of them really date past 2006, a lot of the methods are obsolete.

It basically involves removing GDM, logging in (the login and password are both 'media'), then having an automatic login command to run 'startx'. I've removed GDM on my test environment, and so far managed get in manually by logging in and typing startx.

(On that note, do I even need a username and password? Can't I just use the password only for su?)

---

### Post by Copper Bezel on 2011-06-06
Stupid question, I guess, but can't you just edit /etc/gdm/custom.conf with 

> AutomaticLogin=[you]
AutomaticLoginEnable=True 

?

---

### Post by CJxD on 2011-06-06
> **Copper Bezel said:**
> Stupid question, I guess, but can't you just edit /etc/gdm/custom.conf with 

 

?

Even if that file existed for me, it doesn't work because if the user name changes (which it does for every fresh install), it'd need to be reconfigured; and if somebody somehow manages to log out, they're going to have a hard time typing the password with a remote if they have no keyboard to hand.

---

### Post by Copper Bezel on 2011-06-07
Oh, I see. You're remastering and distributing this, then. I don't have any experience with this - obviously, Ubuntu (Gnome) offers this option in the Ubiquity installer, but I don't know how that's managed.

---

### Post by ojdon on 2011-06-07
What version of GDM are you using by the way? GDM Version 3.0.2 automatic login function doesn't work if that's you're having a problem with.

Open up Synaptic and search for the "GDM" package then downgrade it to version 2.3.2 this should allow you to automatically log into XFCE session.

EDIT: Nevermind thought you were having an issue with GDM.

---

### Post by kerry_s on 2011-06-07
lubuntu would be better, less gnome apps, no gdm(lxdm is used), session start up apps are very easy to tweak, it's faster than xfce, etc...

is there a particular reason you want xfce(xubuntu)?

[http://lubuntu.net/](http://lubuntu.net/)

---


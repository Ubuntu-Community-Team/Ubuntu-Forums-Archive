---
title: "How can I remove everything except a terminal, apt-get &amp; networking from Ubuntu 8.10?"
date: 2009-01-15
forum: General Help
---

### Post by Panarchy on 2009-01-15
Hi

Been looking into this for a while now (especially on IRC).

I have been creating and recreating my linux distrbituion for quite some time now ,(well not compared to other distro's... maybe been working on it for 1-2 months), and I am about to recreate it from scratch (clean Ubuntu installation) for the 7th or 8th time.

To make this as minimal as possible, I would like to remove everything from it, except for the following;

[LIST=1]
[*]GNOME
[*]Ubuntu icons for GNOME
[*]DPKG
[*]Apt-Get (think the real name is Aptitude?)
[*]Network Capabilites (for access to internet)
[*]Generic Drivers
[*]manpages (unless this can installed via apt-get)
[*]GNOME Terminal Emulator
[/LIST]

Please tell me what to do in order to limit my Ubuntu installation in the above way.

Thanks in advance,

Panarchy

PS: Have been recommended debootstrap in the past. Do you think it's a good idea? If so, how do I use it?

---

### Post by utnubuuser on 2009-01-15
Go to the Library and borrow some Gnu/linux books.  Read them. 
Try "The Linux Cookbook", or "Ubuntu unleashed". - They're very comprehensive.
If your local libray doesn't have any recent editions, they can probably order them in.

---

### Post by Bucky Ball on 2009-01-15
You could load server edition which would be close then add gnome to that. Or try the mini-ubuntu from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

... then add what you need.

---

### Post by Panarchy on 2009-01-15
Thanks BuckyBall, though I've had a few problems with that in the past... mainly to do with my internet not working (stuffing up at apt)

Sure, I'll give server edition a go.

Thanks

PS: Any other recommendations would still be helpful, just-in-case

---

### Post by todak on 2009-01-15
Have a look here: [http://uck.sourceforge.net/](http://uck.sourceforge.net/) and see if this may be helpful to you.  Be sure to click the **Documentation** link on the left and peruse the guides. They are rather comprehensive.

---

### Post by hyper_ch on 2009-01-15
alternate install cd, there are various install optiones there like a minimal system - although I have not used it.

---

### Post by cdwillis on 2009-01-15
The quickest and easiest way I think would be just to use the minimal installation disk:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It would be better than going through dependency hell uninstalling everything.

---


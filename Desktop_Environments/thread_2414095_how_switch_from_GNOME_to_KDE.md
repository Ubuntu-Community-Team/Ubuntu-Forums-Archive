---
title: "how switch from GNOME to KDE ?"
date: 2019-03-05
forum: Desktop Environments
---

### Post by anderbuntu on 2019-03-05
Hi

I have 18.10 Ubuntu and I've  just installed KDE, however I havent  found how to switch to KDE.
When I logged off / ON > there is no option to choose, still starting GNOME...

Any advice ?

A.

---

### Post by monkeybrain20122 on 2019-03-05
Make a clean install of kubuntu. Mixing DE is a bad idea in general.

---

### Post by anderbuntu on 2019-03-05
Hmm, so there is no cfg file to change desktop ?

---

### Post by #&amp;thj^% on 2019-03-05
As you wish: [https://linuxconfig.org/how-to-install-kde-plasma-desktop-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-kde-plasma-desktop-on-ubuntu-18-04-bionic-beaver-linux)
Two DE environments can have some side effects.

---

### Post by CatKiller on 2019-03-05
> **anderbuntu said:**
> Hmm, so there is no cfg file to change desktop ?

How the session options are presented depends on the Display Manager: the thing that creates the login screen and launches the session when you log in. There are a bajillion of those. Ubuntu used to use LightDM, which seemed fine when I used it. I believe the current default after Ubuntu switched away from Unity to Gnome is GDM, which has some issues. I think Kubuntu uses SDDM. You can use whichever desktop manager you like, and it's possible to change the functionality with theming.

The main downside to having two desktop environments installed is that you get two of a whole bunch of things. You'll have Kate and Gedit, and Dolphin and Nautilus, and Discover and Software Centre, and two sets of system settings that may or may not actually do what you think they'll do. It gets confusing.

My recommendation would be to try Kubuntu from a live session. And then install Kubuntu.

---

### Post by anderbuntu on 2019-03-08
Thanks its working now

---


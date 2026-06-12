---
title: "Appearance changes on high CPU"
date: 2008-12-03
forum: Desktop Environments
---

### Post by Yoshanuikabundi on 2008-12-03
Hi,

I've been using Ubuntu for a couple of years now, and recently I've come across a problem. I'm currently on Intrepid, and occasionally when my CPU maxes out everything locks up for a bit (surprise, surprise), and then Gnome's theme appears to change. Going into appearance options usually changes it back, but even when it doesn't it still shows my usual theme as the one selected. I have sometimes had to log out and back in to fix it, but I can usually fix it by simply opening an appearance window.

This happened occasionally in Hardy, but everything would return to usual after a couple of seconds.

It's not a huge problem, and I'm still enjoying Ubuntu more than Windows. It is a bit annoying however. Has anyone else had this problem, and is there a way around it?

Hope that made sense. Thanks,
 - Josh

---

### Post by Izek on 2008-12-03
Do you have ATI Graphics?

---

### Post by Yoshanuikabundi on 2008-12-04
No, Nvidia. I'm using the recommended driver from the automatic graphics driver installer.

EDIT: I also get the following error message occasionally when starting Appearance:

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

I get the gist of the message, but don't know how to diagnose it further or anything.

---

### Post by tonybeccar on 2008-12-27
Hi, I'm having the exactly same problem here. I have no idea how to solve it or know what is causing it.

I made a thread here: [http://ubuntuforums.org/showthread.php?p=6446294#post6446294](http://ubuntuforums.org/showthread.php?p=6446294#post6446294)

Well, I hope somebody would have a solution for this.

Good bye!

---

### Post by Yoshanuikabundi on 2008-12-31
I did some fiddling, and found a couple of things out.

The problem that's happening is that gnome-settings-daemon is crashing. I created a panel icon which simply runs that daemon, and so whenever it goes I can just click that icon.

I also found that the problem seems to come up only while Amarok is running. I switched to Exaile to reclaim some CPU powers, and haven't been afflicted since. I'm not sure if this is infallible, but it seems to be doing the trick. Those of you who are having the problem, try finding gnome-based alternatives to your KDE programs, especially Amarok. It's a bit odd, but who knows...

---

### Post by Rohan Kapoor on 2009-01-01
> **Yoshanuikabundi said:**
> I did some fiddling, and found a couple of things out.

The problem that's happening is that gnome-settings-daemon is crashing. I created a panel icon which simply runs that daemon, and so whenever it goes I can just click that icon.

I also found that the problem seems to come up only while Amarok is running. I switched to Exaile to reclaim some CPU powers, and haven't been afflicted since. I'm not sure if this is infallible, but it seems to be doing the trick. Those of you who are having the problem, try finding gnome-based alternatives to your KDE programs, especially Amarok. It's a bit odd, but who knows...

I just tried it on my virtual ubuntu in ubuntu which had the error, removing Amarok fixed the problem!

---

### Post by tonybeccar on 2009-02-04
Same problem here. The last time this error happened and I opened the appearance settings, Ubuntu told me that some KDE processes are in conflict. So, the only thing we have to do is to find that process that we know launches when Amarok does and try to find a solution.

In my opinion is some script/package/process that we mannualy installed that affects Amarok in some way because if you do a fresh install, you don't have this kind of problem.

I'll try to find this process or whatever, if I find a solution, I'll post it. Meanwhile please anyone that have a clue of how to fix this?

Bye!

---


---
title: "No &quot;Shutdown&quot; option under &quot;Leave&quot;"
date: 2009-11-26
forum: Desktop Environments
---

### Post by spencercarran on 2009-11-26
Kubuntu 9.10 KDE4.3. I actually had installed regular Ubuntu first and then added kubuntu-desktop on top of it. For some reason, when I click the K menu and go to "Leave" there is no option to shutdown. I can logout, lock screen, switch user, suspend, or hibernate, but I can't shut down. Anyone know why it's not showing the option to shut down, or how I can get it?

---

### Post by jacobs444 on 2009-11-26
I am not sure, but it seems like you have to logout, and shutdown from KDM. It used to do this to me alot.

---

### Post by spencercarran on 2009-11-26
> **jacobs444 said:**
> I am not sure, but it seems like you have to logout, and shutdown from KDM. It used to do this to me alot.

That's what I've been doing, but I'd much prefer to just shutdown from KDE.

---

### Post by Zorael on 2009-11-27
System Settings, Advanced tab, Sessions, *Offer shutdown option*.

---

### Post by lexfati on 2009-11-27
Or you can use KDM as your login manager,

```
Sudo apt-get install kdm
```

---

### Post by spencercarran on 2009-11-27
> **Zorael said:**
> System Settings, Advanced tab, Sessions, *Offer shutdown option*.

It was already checked. I unchecked it and rechecked it, no change.

---

### Post by Zorael on 2009-11-27
> **spencercarran said:**
> It was already checked. I unchecked it and rechecked it, no change.
Is X being started automatically upon boot, or are you starting it via startx? ([http://forum.kde.org/viewtopic.php?f=66&t=31708](http://forum.kde.org/viewtopic.php?f=66&t=31708))

edit: Nevermind, probably automatically since you mention kdm. Hm.

---

### Post by subodh.rohilla on 2010-02-08
I have the same problem and I have correctly fixed it.

Use command : sudo dpkg-reconfigure gdm
 and select kdm as default login manager and all will work fine.

---

### Post by spencercarran on 2010-02-08
> **subodh.rohilla said:**
> I have the same problem and I have correctly fixed it.

Use command : sudo dpkg-reconfigure gdm
 and select kdm as default login manager and all will work fine.

Thanks for the tip, but I've since migrated back to GNOME. It's a bit faster, and I tend to use more GTK apps than Qt anyways.

---


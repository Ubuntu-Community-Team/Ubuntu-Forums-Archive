---
title: "gnome starting with wrong theme"
date: 2011-05-21
forum: Desktop Environments
---

### Post by akos.maroy on 2011-05-21
I'm experiencing a strange phenomenon with gnome. On a regular basis, but not predictably, when I log in, a different theme is used than the one configured in System -> Appearance. If I log out and back again, sometimes the issue persists, but eventually my I will be able to log in seeing my preferred theme. this happens more often write after system boot than later.

I wonder if anyone else has experienced this before.

I wonder what could be the cause of this issue?

---

### Post by cbowman57 on 2011-05-21
> **akos.maroy said:**
> I'm experiencing a strange phenomenon with gnome. On a regular basis, but not predictably, when I log in, a different theme is used than the one configured in System -> Appearance. If I log out and back again, sometimes the issue persists, but eventually my I will be able to log in seeing my preferred theme. this happens more often write after system boot than later.

I wonder if anyone else has experienced this before.

I wonder what could be the cause of this issue?

It has something do with the system loading too fast.  Can't remember offhand but there is a file that needs a delay edited in.  This assumes that you're probably running some fast, late model hardware, maybe SSD?

---

### Post by akos.maroy on 2011-05-21
> **cbowman57 said:**
> It has something do with the system loading too fast.  Can't remember offhand but there is a file that needs a delay edited in.  This assumes that you're probably running some fast, late model hardware, maybe SSD?

yes, intel i7 & SSD.

hm, would make wonders if you'd remember the delay setting :)

---

### Post by satreth on 2011-05-21
Might be this [http://ubuntuforums.org/showpost.php?p=10404145&postcount=5]("http://ubuntuforums.org/showpost.php?p=10404145&postcount=5")

---

### Post by cbowman57 on 2011-05-21
> **akos.maroy said:**
> yes, intel i7 & SSD.

hm, would make wonders if you'd remember the delay setting :)

It doesn't say what file, but you can always do a text search.  Might be gdm-greeter configuration.

Kinda cool really, we finally have hardware available that is too fast for the operating systems. :)

Fixed by changing:

Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon

to this:

Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

to add a 2 second delay. To the startup file for Gnome-Settings-Daemon. And after rebooting, the theme is now properly applied.


[Launchpad link]("https://bugs.launchpad.net/system76/+bug/690273/comments/3")

Bingo, good call. Basically it involves editing /etc/xdg/autostart/gnome-settings-daemon.desktop and changing line 4 to:

---

### Post by akos.maroy on 2011-05-21
thanks - giving it a try!

---

### Post by fly2k on 2011-07-05
sleep 2 did not help for me :(

---

### Post by Krytarik on 2011-07-05
> **fly2k said:**
> sleep 2 did not help for me :(
Then just try a longer delay.

---

### Post by fly2k on 2011-07-08
> **Krytarik said:**
> Then just try a longer delay.
I am not sure my situation is the same cos my hardware is not too fast(Athlon 64 3700+, 2Gb, Radeon X850XL). How can I see any debug info while logging?

---


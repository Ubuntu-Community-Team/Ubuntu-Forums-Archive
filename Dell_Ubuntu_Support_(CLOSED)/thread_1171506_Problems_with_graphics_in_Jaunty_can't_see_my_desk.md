---
title: "Problems with graphics in Jaunty: can't see my desktop!"
date: 2009-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by a.hirsch on 2009-05-27
Hi all.
I am running a dell inspiron e1505 laptop with the following graphics controller:

Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I upgraded last night from intrepid to Jaunty, and once the install was complete, restarted my system. Everything was good until i logged in. Everything seemed to be loading properly until the Compiz Fusion splash popped up. Then everything turned black, with a few extremely pixelated lines to indicate where the menus are. by guessing where the right menu was, i was able to log on as a guest. While logged into that username, everything works properly, but i do not have access to the files i need, and I have restricted access to the menus, since i cannot log on as the administrator. So i'd like to resolve this problem and be able to use my main username.

Anyone able to help?

---

### Post by ugm6hr on 2009-05-27
I suspect you are a victim of the Intel Graphics driver problem.  See the Release Notes: [http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

I would suggest that removing compix might solve the current problem.

From Grub menu - boot into the Recovery Mode, and go to Terminal.

This should do it:

```
sudo apt-get remove compiz-core
sudo poweroff
```

Restart, and keep fingers crossed.

---

### Post by a.hirsch on 2009-05-28
thanks, that actually did help. i can use my desktop now! i just don't have the status bar on the bottom of my screen that lets me maximize the programs i've minimized.  guess that was some aspect of compiz. what other options are out there as far as window compositors, other than compiz?

---

### Post by a.hirsch on 2009-05-28
I ended up adding a new panel on the bottom, and a list of all the windows I have open to that. That should work for now, but I'd still like to find a new compositor. Just documenting this in case someone has similar problems...

---


---
title: "Menus deformed and warped in Unity and Gnome-Shell (Maverick)"
date: 2011-05-01
forum: Desktop Environments
---

### Post by 3602 on 2011-05-01
So instead of risking a borked upgrade, while wanting to try something new, I installed Unity (from a guide somewhere) and Gnome-Shell from Ubuntu Tweak.
Well they installed and run fine. The problem is this: Many pop-up menus, right-click menus and volume icons and such are warped and deformed. There is a diagonal line running through the box and the text is all slanted and "wrapped around" this diagonal.
I do not know what to provide as of right now, so here's what I can think of:
```
uname -a
2.6.35-29-generic #51-Ubuntu SMP Fri Apr 15 17:12:35 UTC 2011 x86_64 GNU/Linux

```
Yes the kernel is from Maverick-proposed. I am running Fire GL (fglrx).

Is this Compiz and Mutter conflicting or...?
Thank you very much.

---

### Post by 3602 on 2011-05-01
Also, drop-down menus in Firefox and all other programs are warped this way. I cannot take a screenshot since the Shutter window is also warped this way...

---

### Post by 3602 on 2011-05-02
Bump.

---

### Post by artoonie on 2011-05-29
I have this problem as well...any fixes?

---

### Post by maverick280857 on 2011-05-29
To be honest, the best way to (try to) not have this problem is to do a clean install of Ubuntu 11.04 and follow the instructions here:

[http://ubuntuforums.org/showpost.php?p=10734567&postcount=1](http://ubuntuforums.org/showpost.php?p=10734567&postcount=1)

and if needed

[http://ubuntuforums.org/showthread.php?p=10855699#post10855699](http://ubuntuforums.org/showthread.php?p=10855699#post10855699)

Get Unity to work properly, and then use a terminal to download all the packages you need to get gnome3 to work.

---

### Post by 3602 on 2011-05-30
Well I'm in Mavvy and what I did was to fully purge everything made by *jhbuild build* and every bit of "Unity" and "Netbook" I can find in Synaptic. Then I installed the Gnome Shell from Ubuntu Tweak and everything is almost fine. Well, no warped menus but everything is a bit choppy.

---


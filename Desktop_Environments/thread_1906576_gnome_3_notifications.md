---
title: "gnome 3 notifications"
date: 2012-01-09
forum: Desktop Environments
---

### Post by cybergalvez on 2012-01-09
Hi all I am using gnome-shell, what I want to know is can the time that notifications stay popped up at the bottom of the screen be set? on my desktop they seem to go away very quickly, while on my laptop they seem to stay up until I clink on them.

---

### Post by jerrrys on 2012-01-11
I think your talking about "notify osd".  This is dated and you will have to find the right download for 11.10.

[http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26](http://maketecheasier.com/easily-customize-notifyosd-ubuntu-lucid/2010/05/26)

---

### Post by hhh on 2012-01-11
@cybergalvez, gnome-shell does NOT use notify-osd and the link given by the poster above will not help you. As I am not sure how Ubuntu implements gnome-shell when Unity is already installed (I am running the shell on Debian), I would wait until someone with more knowledge posts before you make any changes.

My apologies to jerrrys if I am mistaken. Cheers.

---

### Post by jerrrys on 2012-01-11
No, my apologies. I run classic and it was an assumption on my part.

---

### Post by jerrrys on 2012-01-11
Ok, heres an update.  Thought I try to redeem myself. :)

I have searched and found ways (hacks) to remove, move, remove stacking, remove icons, but nothing on time-out.  Seems to be hard coded from what I make of it.

Some hacks edit the /usr/share/gnome-shell/js/ui/main.js
May be something useful in there.

And on a side note:
One suggested removing libnotify-bin to remove notifications.  Which sounded like a good idea, so I removed it from mine. When removing the lib, it also said the ubuntu-desktop would be removed.  But this only added up to two packages and 160K of space, which made no sense. So I did it anyhow. Things seem to be ok. Need to give it a day or two or three to see if that indeed was a good idea.

Good luck

---

### Post by hhh on 2012-01-11
@jerrrys, ubuntu-desktop is a "meta package", which means that it just calls a whole lot of other packages but does not remove those packages when the meta package is removed....
[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Cheers.

---

### Post by jerrrys on 2012-01-11
Yep, no big deal.  And I haven't had a pop-up for one hour :)

---

### Post by ptsubin on 2012-01-12
I too found it annoying sometimes, especially when I mount one of my partitions. The notification stays there asking me if I want to open the mount point when it is already open in front of me.

---

### Post by cybergalvez on 2012-01-12
I haven't been able to figure this out either. I looked at the code for the permanent notificatoins extension, but I really don't understand it

---


---
title: "Flashback (no effects) session unusable in Ubuntu GNOME"
date: 2013-10-26
forum: Desktop Environments
---

### Post by kansasnoob on 2013-10-26
I've been trying to figure this out for a few days w/o success :(

The "flashback (no effects)" session works perfectly in both Ubuntu and Edubuntu, which makes sense since the Edubuntu devs need to support "flashback" for their LTSP project. But installing that session in Ubuntu GNOME results in an unusable desktop.

The menus and windows just don't react in even a remotely normal way, I'll post some screenshots:

[ATTACH=CONFIG]247271[/ATTACH][ATTACH=CONFIG]247272[/ATTACH][ATTACH=CONFIG]247273[/ATTACH][ATTACH=CONFIG]247274[/ATTACH]

I'm really at a loss here so any suggestions would be appreciated.

Oh, I have tried a fresh user profile with no success.

---

### Post by grahammechanical on 2013-10-26
A wild guess this. Most likely so wild as to be wrong. Are you using Nouveau? There is a subset of Nouveau called llvmpipe that Ubuntu uses when a video adapter is not able to run what was once called Unity 3D. It is what we get now when we use Recovery>Resume. Llvmpipe makes an acceptable presentation but it is noticeable that screen moves are not so snappy.

I was just wondering what the purpose of Gnome Fallback/Flashback is for, apart from giving some people the desktop look that they like, that is. Did it not originally have a similar purpose to Unity 2D? As a fallback mode? 

Regards.

---

### Post by kansasnoob on 2013-10-26
> **grahammechanical said:**
> A wild guess this. Most likely so wild as to be wrong. Are you using Nouveau? There is a subset of Nouveau called llvmpipe that Ubuntu uses when a video adapter is not able to run what was once called Unity 3D. It is what we get now when we use Recovery>Resume. Llvmpipe makes an acceptable presentation but it is noticeable that screen moves are not so snappy.

I was just wondering what the purpose of Gnome Fallback/Flashback is for, apart from giving some people the desktop look that they like, that is. Did it not originally have a similar purpose to Unity 2D? As a fallback mode? 

Regards.

No Nouveau, the hardware used is:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

And the flashback session is needed for Edubuntu's LTSP installs.

---

### Post by kansasnoob on 2013-10-27
I went ahead and raised this issue on the mailing list:

[https://lists.ubuntu.com/archives/ubuntu-gnome/2013-October/001063.html](https://lists.ubuntu.com/archives/ubuntu-gnome/2013-October/001063.html)

Then I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1245209](https://bugs.launchpad.net/ubuntu/+source/ubuntu-gnome-default-settings/+bug/1245209)

---

### Post by VMC on 2013-10-27
I haven't used flashback, but have you tried *gnome-tweak-tool*:
*Tweak Tool* -> *Shell Extension*s -> [click on]*Applications menu *+ [click on] *Places status indicator*

I like the look and feel compared to old gnome.

---

### Post by kansasnoob on 2013-10-28
> **VMC said:**
> I haven't used flashback, but have you tried *gnome-tweak-tool*:
*Tweak Tool* -> *Shell Extension*s -> [click on]*Applications menu *+ [click on] *Places status indicator*

I like the look and feel compared to old gnome.

I actually find the gnome-shell default DE quite pleasant to use in Ubuntu GNOME with very few tweaks, but I maintain over 40 individual PC's and some users still want a truly "classic" DE. I've been able to move many to Lubuntu but some still want a truly GNOME experience circa version 2, and I don't like Mate.

In this case it's simply a matter of figuring out why the "flashback (no effects)" session works OK in Ubuntu and Edubuntu, but not in Ubuntu GNOME.

---

### Post by kansasnoob on 2013-11-09
I was playing again this AM and found that using lightdm with lightdm-gtk-greeter allows me to boot to a usable flashback (no effects) session.

---

### Post by monkeybrain20122 on 2013-12-11
I don't use it, but the other day installed it on Saucy just to show people this can be done.It worked but with one strange issue. The cursor froze whenever I switched user and back (so me -> guest user ok but guest use -> me cursor freezes) Well this is nouveau and it has that problem sometimes and usually (though not always) can get out of that with ctrl+alt+f7/8, but with gnome flashback installed it happens 100% of the time almost and the key combo doesn't work.  Removed it and now back to normal.

You maybe interested in testing it out.

---

### Post by VMC on 2013-12-11
Yea, its *nouveau* for sure. Using gnome I have to install nvidia drivers or it will at undetermined times freeze using *nouveau*. Using Xubuntu and *nouveau*, it only happens using Abiword. It must be related to my integrated video. I have several bug reports on the subject.

---

### Post by monkeybrain20122 on 2013-12-11
> **VMC said:**
> Yea, its *nouveau* for sure. Using gnome I have to install nvidia drivers or it will at undetermined times freeze using *nouveau*. Using Xubuntu and *nouveau*, it only happens using Abiword. It must be related to my integrated video. I have several bug reports on the subject.

No freezing with nouveau accept for switching user and that happens a lot more frequently with gnome-session-flashback installed than otherwise. Except for that nouveau is actually smoother than the Nivdia blob in many ways on my system. I have not tested if this (freezing when switch user with flashback installed) with the Nvidia driver.

---

### Post by kansasnoob on 2013-12-11
Sorry I can't be of any help but if you look back to post #3 you'll see I'm using Intel hardware so no Nouveau is in play here at all.

I did however encounter this:

[http://ubuntuforums.org/showthread.php?t=2192712](http://ubuntuforums.org/showthread.php?t=2192712)

But I'm still using Precise for production :)

---

### Post by monkeybrain20122 on 2013-12-11
I should clarify that the freezing occurs just because gnome-session-flashback is installed. I was not even using it, I was in Unity when I switched user. After removing flashback it got a lot better. I installed LXDE as an alternative DE just to find out if it is because of having a second DE or gnome specific. Turned out flashback is the culprit, having lxde on the system doesn't cause freeze when switching user the way that flashback did.

This is about having gnome-session-flashback in default Ubuntu (Unity as the desktop) not Ubuntu Gnome. Also the freezing occurs only for the cursor (keyboard works fine) and only for switch back from guest to main user. The flashback session itself works without issue.

P.S. I am not asking for help, but only curious if others might have experienced this or if a bug report has been filed. As I said I don't use flashback, but it may be useful for those who use it.

Edited: Just tested with the Nvidia driver instea of nouveau, this problem doesn't happen.

---

### Post by VMC on 2013-12-11
I agree. *nouveau* is much smoother! Too bad it freezes my computer.

---


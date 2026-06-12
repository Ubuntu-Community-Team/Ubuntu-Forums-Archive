---
title: "Everything has gone transparent!"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by knightnet on 2007-04-03
Help!

Everything on screen is now transparent, scrolling doesn't work properly and it looks like the video buffer is totally ******** with things being overridden.

I've tried removing my kde settings from my home folder & I've also tried resetting xorg.conf but I still get the problem.

Can anyone point me in the right direction?

It is likely that I've installed something that has messed it up since I've been experimenting. BTW, the machine is a Toshiba laptop and the default installation seemed to go pretty well.

I am doing my best to switch from Windows to Linux but stuff like this is certainly not helping me!

Cheers, Jules.

---

### Post by finferflu on 2007-04-03
So, you're using the Feisty Fawn? If so I suggest you to switch to Edgy Eft, since Feisty is still beta (that is, not stable), and things like that are likely to happen.

---

### Post by knightnet on 2007-04-03
Hmm, thanks - yes I can do that but Feisty is due out before the end of the month, if there is an issue, it would be good to find in now wouldn't it?

I understand that I am living on the edge and I am simply looking for pointers for where to go to try stuff.

If it helps, I am not a novice, I'm an IT consultant, it's just that I've always had to spend more time with Windows than Linux and I want to redress the balance.

Regards, J.

---

### Post by Shoubidouw@@@ on 2007-04-03
What is your graphic card? Are you running Beryl ??
Please give more details.

Thanks

---

### Post by finferflu on 2007-04-03
Also, which folders have you deleted? I hope the solution is simpler than expected, perhaps you haven't deleted all the configuration folders in your home directory...

---

### Post by knightnet on 2007-04-03
Thanks for the replies.

I've renamed .kde and .kderc, I also have Gnome installed and I've renamed all of the .gnome*, .metacity and .gconf stuff.

Beryl is installed, I've been trying to remove it as it did seem a likely candidate - though this does not seem to be that easy unless I've missed something. I've also renamed the .beryl folder. I've even renamed the .gtk* folders just in case.

The graphics card is an on-board Intel i810.

Regards, J.

---

### Post by Shoubidouw@@@ on 2007-04-03
Transparent in both KDE and Gnome?

When you say everything is transparent, you mean 100% of your desktop?

---

### Post by knightnet on 2007-04-03
In the login screen the menu is transparent (black text with transparent background).

When logged in to KDE, every window that opens has a transparent background (the desktop shows through).

What is worse though is that the background is not redrawn properly. So when something changes on screen, the previous contents remain.

In Gnome, the startup sequence shows some of the icons with the KDE default backdrop (this is not my actual KDE backdrop but the one from the login screen). This stays there for about a minute before the actual Gnome backdrop appears. There is then a further delay before the menus appear - much longer than there should be, 30 sec or so. Some menus then work (e.g. System/Preferences) but not others (System/Administration). And the whole of Gnome seems massively slow - not at all like the fresh installation.
 When I then go in to add/remove applications for example, the window is not correctly repainted. The categories list and application list sections are not painted at all until I run the mouse over them and scrolling the lists leaves them in a mess unless I run the mouse over everything again.

Regards, J.

---

### Post by finferflu on 2007-04-03
There must be still some configuration file lying around. Usually in such occasions I simply do:

```
rm -rf ~/.*
```

I know it's not the most orthodox solution, but it reverts everything to default without reinstalling the whole thing... I hope you can find a better, more professional, solution though...

---

### Post by Shoubidouw@@@ on 2007-04-03
Agree with finferflu...this solution helped me too sometimes...

---

### Post by knightnet on 2007-04-03
Nice try but I'm afraid that it is still the same! So it must be a system setting somewhere.

J.

---

### Post by finferflu on 2007-04-03
Ok, let's move on to Xorg...
you said you tried to reset Xorg. Did you use this command?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by knightnet on 2007-04-03
```
sudo dpkg-reconfigure xserver-xorg
```

Yep.

---

### Post by knightnet on 2007-04-03
Interestingly, "Failsafe" login also shows the same symptoms

---

### Post by finferflu on 2007-04-03
What a very odd problem... I wish someone with more experience than me could see this thread...

---

### Post by Shoubidouw@@@ on 2007-04-03
Can you try this one:

Edit your xorg.conf and use the vesa driver. Try it. If it works, your current driver might be corrupted. 
Let us know.

---

### Post by knightnet on 2007-04-03
Arrrrrhhhh!!!!

I tried to wipe the installation by installing from a Kubuntu CD (an older version not feisty). Guess what, I got the same issue!!

So in desparation, I started to try a PClinuxOS CD but had to leave it to do something else. When I came back, the PC had booted into Feisty again and ... bingo, the screen was back to normal.

Strange, the only thing I can think of was that I got impatient and powered the PC off on the last reboot!

So back to a normal boot and ... everything is back to normal. What's that all about?

Oh well, I suppose everything is OK now so I'll have to put it down to experience.

Many thanks to both of you for your help.

Regards, Jules.

---

### Post by Chrisj303 on 2007-04-03
Aahh, the old 'switch it off, then switch it back on again' technique in full effect!

chrisj303

---

### Post by finferflu on 2007-04-03
> **Chrisj303 said:**
> Aahh, the old 'switch it off, then switch it back on again' technique in full effect!

chrisj303
LOL! That's a powerful one! :D

---

### Post by knightnet on 2007-04-10
For reference, it was a suspend/resume problem!

Suspend and resume always reproduces this problem and it always requires a power-off to fix. :(

---


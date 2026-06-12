---
title: "Freeeeezing!!"
date: 2005-12-23
forum: General Help
---

### Post by Odinist on 2005-12-23
Grrrr! :mad: 

I'm currently running Warty on my computer. This upsets me.


I had been running Hoary since a handful of days after its release, with pretty much no issues. Well, I tried to upgrade to Breezy a little while back, and after the install, my computer would freeze completely after anywhere from 30 seconds to a few minutes of X usage. So, I wiped my drive and tried to reinstall Hoary, and lo and behold, it did the same thing. =/

I remember when I had first tried to upgrade to Hoary (before its release date, mind you) I had the same problem, and tried numerous things to try and fix it with no success. I waited until it was officially released and did a clean install of it, and it worked fine.

So, I know that I've been able to get a version other than Warty to work on my hardware before, I just don't know what I need to do to get it to work now for Breezy.

The computer is an MSI K-7 board with an AMD Sempron 2600+ processor, with 768 megs of RAM. To recap the problem, on a fresh install of either Hoary OR Breezy, the whole computer freezes (i.e. no mouse movement, no CTRL-ATL-F# for a different terminal, no CTRL-ALT-Delete to restart, nothing) after a short period of X usage. I've noticed seems to be set off by resizing Nautilus windows, browsing the web, or pretty much anything dealing with open windows. 

Any ideas guys? I'm really dying to upgrade because I not only can I not get Warty to install the MS codecs (So I can play wmv, wma, etc etc), but I really want to get lmms up and running to play around with it.

Thanks in advance!!

---

### Post by BathroomNinja on 2005-12-23
Try this, boot up to the Ubuntu Breezy live CD (don't install).  See if you can get it to freeze.

---

### Post by Odinist on 2005-12-23
<bump>

Any other ideas on this?

(I can't try the live CD right now; I'm at work. I'd like to have as many ideas as possible ready to try out when I get home. TIA!)

---

### Post by DevilsAdvocate on 2005-12-23
When your computer hangs, try to switch to terminal 1 (CTRL+ALT+F1) and see if there are any messages there.  This is the terminal X is running in.  I would also try to switch to any other terminal, e.g. 2, and see if it'll take commands.  Try switching run levels.  

```
sudo init 6
```

this will reboot.

Just looked at your thread more closely and see you can't switch term's...I ponder.

---

### Post by Zimmer on 2005-12-23
Overheating..?... I read a few threads the other day about cpu temp control problems under certain circumstances ... I will re investigate..
Zimm
EDIT...
[http://ubuntuforums.org/showthread.php?t=76288&page=9&highlight=freeze+lock](http://ubuntuforums.org/showthread.php?t=76288&page=9&highlight=freeze+lock)

Plenty of others with similar problems..... and various solutions...

---

### Post by DevilsAdvocate on 2005-12-23
Curious, what kernel gets installed w/ your CPU?

---

### Post by PMO6022 on 2005-12-23
Do you have RenderAccel enabled in your xorg.conf?  I've seen random lockups caused by enabling that with certain versions of the nvidia drivers.

---

### Post by Odinist on 2005-12-23
Fixed it!!!!!

I used Synaptic to uninstall powernowd, then thereafter I changed sources.list to the Hoary repositories, and then used Synaptic to upgrade.

Everything's running wonderfully now, and I've already changed the repositories to Breezy and am in the process of upgrading to that! 

w00t!!!

Thanks for everyone's help! This is why I *LOVE* Ubuntu... The community support is just freakin' amazing!

---

### Post by Odinist on 2005-12-25
Just a quick update on how the upgrade to Breexy went...

Like I said, the upgrade to Hoary went fantastically, with everything running swell and lock-up free. 

But, for some reason, the upgrade to Breezy wasn't as smooth. When I rebooted for the first time after the upgrade was done, GDM gave me some weird message about how it wasn't configured correctly, and that I should fix that. OKing that message gave me a graphical login, although not the normal one. I could log in from there, but within about a minute, the system had locked up. Grrr. =/

I went ahead and did a clean install of Breezy from a CD, and after it was finnished, when the login screen came up, I switched to a differnt terminal, ran apt-get remove powernowd, and then rebooted, this time going ahead and logging in. After I logged in, I downloaded Automatix, let it do it's thing, and now I'm running a gorgeously functional Breezy system. =)

I love Ubuntu!

---


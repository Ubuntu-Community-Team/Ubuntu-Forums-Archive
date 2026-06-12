---
title: "No desktop"
date: 2013-01-27
forum: Desktop Environments
---

### Post by jfbooth on 2013-01-27
Xubuntu 12.10

This computer is an old WIN ME machine with only 512MB of memory.  I wanted to go to a 'lightweight' browser . so I installed MIDORI.  All well and good.

It also has a very small capacity hard drive (18GB) so I try to uninstall anything I don't need.

**I am also a LINUX rookie.**  I should mention total confusion between GNOME, XFCE, KDE, desktops/environments and the like.  I somehow got this machine to look/feel the way I liked it .. I think by invoking XFCE some time ago.

Sooo, I uninstalled 'Web Browser' .. which warned me that I would also uninstall SEVERAL other things .. like THUNAR file manager.  Fine .. I 'went for it'.  Came back up, and sure enough, several aps were gone .. so I installed XFS file manager  LOVE IT.  

Then .. I did some more uninstalls ... and yes .. I don't remember what they all were .. I did it 'intuitively' and seemed like a good thing to do.

Now, when I boot up, I get:

'unable to launch "startxfce4" X session NOT Found, falling back to default session'.

and a totally empty desktop ... only wallpaper.  Cannot see anything BUT wallpaper.  I done 'bricked' the desktop.

HALP, ... please!!  Thank you in advance.

---

### Post by sidzen on 2013-01-27
Can you get to tty console with Ctrl-Alt-F1 (thru F6) and get back with Ctrl-Alt-F7?

---

### Post by ibjsb4 on 2013-01-27
Without knowing what you removed, its difficult to know how to fix.

Since this seems to be a fresh install maybe it would be best just to reinstall Xubuntu.  12o4 is supported for 5 years.

---

### Post by Peripheral Visionary on 2013-01-27
It sounds like you have made a mishmash mixture of settings and tools from different desktop environments.

Read [this]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") first. It is a description of the different Linux desktops, and a feature of desktop environments called *integration*.  While it is possible (and fun) to mix them up a bit, there can be a cost if it's overdone.

---

### Post by jfbooth on 2013-01-27
> **sidzen said:**
> Can you get to tty console with Ctrl-Alt-F1 (thru F6) and get back with Ctrl-Alt-F7?

Remember .. rookie here.  I take it you are referring to 'terminal'.  

I take it you mean .. from this 'blank' desktop, hit Ctrl-Alt F1, F2, F3, F4, F5, F6 and see if I get a terminal window from one of the combinations.  And if I do, .. try Ctrl-Alt-F7 to get back to 'blank' desktop??????

Assuming that is exactly what you mean, I will give it a try.

OK .. F1-F6 all take me to a login prompt.  F7 takes me back to blank desktop.

I am encouraged.  Thank you for your help.  What next, please?

---

### Post by jfbooth on 2013-01-27
> **Peripheral Visionary said:**
> It sounds like you have made a mishmash mixture of settings and tools from different desktop environments.

Read [this]("http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893") first. It is a description of the different Linux desktops, and a feature of desktop environments called *integration*.  While it is possible (and fun) to mix them up a bit, there can be a cost if it's overdone.


Maybe.  I don't think it is 'that bad' .. what I did was uninstall WEB BROWSER from package manager .. and that ininstalled SEVERAL other things .. such as THUNAR and stuff 'related' to XFCE.  The ONLY thing I INSTALLED was Midori browser.

---

### Post by tgalati4 on 2013-01-27
Open a terminal and post:

```
history
```

Perhaps we can figure out what you removed by looking through your history.  You have to be careful when removing packages.  Some packages are *meta* packages, meaning they are a collection of several packages bundled together.  If you remove the meta package then you will remove several things at once and that will break things.

Linux is yours to break.  And you get to keep both pieces.  But that is how you learn.  Either buy a larger hard disk, or spend more time researching what is safe to remove and what is not safe to remove.  After about 3 borked systems, you have a good idea.  You now have 1 borked system, so you are on your way.

---

### Post by jfbooth on 2013-01-27
> **tgalati4 said:**
> Open a terminal and post:

```
history
```

Perhaps we can figure out what you removed by looking through your history.  You have to be careful when removing packages.  Some packages are *meta* packages, meaning they are a collection of several packages bundled together.  If you remove the meta package then you will remove several things at once and that will break things.

Linux is yours to break.  And you get to keep both pieces.  But that is how you learn.  Either buy a larger hard disk, or spend more time researching what is safe to remove and what is not safe to remove.  After about 3 borked systems, you have a good idea.  You now have 1 borked system, so you are on your way.

You certainly make good points.  Right now, I would very much like to restore this computer to pre-bork if at all possible.

So, .. I logged into TTY console .. which I GUESS is 'terminal'.

OH .. one more thing, . I declared Xubuntu 12.10 .... my mistake, .. it is 12.04.

So .. at the XUBUNTU website, I found this:

[B]Upgrading from Xubuntu 12.04
The update manager GUI will offer you 12.10 Xubuntu (it shows as Ubuntu, but updates Xubuntu); Alternatively, launch a Terminal and enter sudo do-release-upgrade[/B]

Would not that update/repair to 12.10 .. from the only thing I can interact with ... the TTY console???????

Edit:  history lists 297 lines .. which scroll so fast, I cannot see the top 1/2.  I do not know how to pause a scroll.

I also found this:

**sudo apt-get install xfc4**

Would that 'fix' everything???????  ... maybe???

---

### Post by jfbooth on 2013-01-27
I break 'em .. I fix 'em.  I took a deep breath and from TTY console

**sudo apt-get install xfce4**

and it APPEARS everything is back where I started .. preBORK.

Thank you ALL for your attention.  I paid heed to every reply.  I learned A LOT .. thanks to you marvelous experts.  Thank you all again.

---

### Post by tgalati4 on 2013-01-28
history | more

To see your history one page at a time.

---

### Post by jfbooth on 2013-01-28
> **tgalati4 said:**
> history | more

To see your history one page at a time.

Thought about that .. but figured NAH .. that's DOS.  Also, I would have seen 270+ lines one screen at a time ... with no idea how to post those lines here in this forum.  Sure .. pipe output to a file (DOS style??) but then needed to get the file into a browser somehow.  USB stick?  Mount that from console?  Way over this rookie's head.  I WISH I knew how to do all such things.

---


---
title: "No Launcher, No dash after upgrade 11.10"
date: 2011-10-14
forum: Desktop Environments
---

### Post by pp. on 2011-10-14
Up to now, I used to use the Gnome Classic desktop in 11.04.

After updating to 11.10

[LIST]
[*]There is just the desktop with a menu bar.
[*]There is no launcher, no dash; in fact, in can't find any of the things the help file shows.
[*]Excepting the menu bar, there are no controls of any sort anywhere.
[*]There is no program menu. There is no terminal window.
[*]In fact, I only can start programs by double clicking on files.
[/LIST]

I would like my Gnome desktop back, please.
Failing that, I would like to have all those controls such as Launcher, dashes and whatever they are called just so I can use my computer again.

---

### Post by randywilharm on 2011-10-14
Go to a terminal and enter:

sudo apt-get install gnome-panel

and reboot after it finishes loading. Immediately before you enter pass-
word upon reboot, select Gnome classic from options, or sometimes there is a cog
you click...try that.

---

### Post by g30rg3 on 2011-10-15
I have the same problem. Dash has suddenly disappeared. I would like to bring it back. I'm using Ubuntu 11.10. Is there any way I can bring up the terminal and then Compiz Settings Manager? I would like to avoid reinstalling from scratch

---

### Post by Krytarik on 2011-10-15
> **g30rg3 said:**
> Is there any way I can bring up the terminal and then Compiz Settings Manager?
Try first if pressing Ctrl+Alt+T brings up the Terminal - as this wasn't the case in Natty 11.04, but is indicated in another [thread]("http://ubuntuforums.org/showthread.php?t=1859786") to work now. If it doesn't, please see this guide for another way, and more instructions:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by qunungnauraq on 2011-10-15
I have a similar problem. I did a clean install of 11.10 64 bit and enabled initiate window picker for all windows for an expose effect. After a reboot my dash launcher was stuck in auto-hide and I would have to use the key command to launch it.

---

### Post by pp. on 2011-10-15
Thanks to allfor their advice.

All attempts to fix the problem failed. Some produced error messages about "invalid characters in package names" referring to jaunty.

I think that the repeated updates for several years have left so much garbage that the new packages somehow failed to clean up my system.

In the meantime I have decided to re-install from scratch. Which I did. Everything seems to work now. I don't know whether I like the "new" Unity. I certainly don't like being told when I have to learn to use a new GUI,

Such is life.

---

### Post by robertmf on 2011-10-15
> **randywilharm said:**
> Go to a terminal and enter:

sudo apt-get install gnome-panel

and reboot after it finishes loading. Immediately before you enter pass-
word upon reboot, select Gnome classic from options, or sometimes there is a cog
you click...try that.

:P *[COLOR="DarkRed"]Thanks.[/COLOR]*

---

### Post by Krytarik on 2011-10-15
> **randywilharm said:**
> Go to a terminal and enter:

sudo apt-get install gnome-panel

and reboot after it finishes loading. Immediately before you enter pass-
word upon reboot, select Gnome classic from options, or sometimes there is a cog
you click...try that.
Btw., this way is only possible because "gnome-session-fallback" is a 'recommend' of "gnome-panel":

[http://packages.ubuntu.com/oneiric/gnome-panel](http://packages.ubuntu.com/oneiric/gnome-panel)

So, it's quite an indirect installation method for the Gnome Classic sessions :P , and it doesn't work if you disabled the automatic installation of 'recommends', which it isn't by default, however.

Regards.

---

### Post by pacodea on 2011-10-16
I had the same problem and the only way I could recover it was starting Ubunto 2D.

I hope this help.

---

### Post by areeda on 2011-10-16
I ran into this issue and found compiz was crashing.

As far as I can tell it has to do with setting options in Compiz settings.  I'm pretty conservative in my settings nothing very drastic.  I haven't nailed down which one so I decided to give up on them while I decide it I upgrade now or wait for a few bug fixes first.

I could recover by Ctl-Alt-F2 to drop to a terminal, log in then run unity --reset, reboot and the launcher and top menu bar were back.

Joe

---


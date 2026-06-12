---
title: "Lucid Lynx - Appearance/Compiz problem"
date: 2010-05-01
forum: Desktop Environments
---

### Post by G_u_s on 2010-05-01
Hi all,

first, I have posted a very similar thread in the Apple section. I'm using a MacBook 2.1, so i posted there, but in case my problem is not specific to Apple hardware, I'm posting it here again.

I've just updated from 9.10 to 10.04.

The first time I logged in, I had display problems:
- Windows were too high, overlapping the top panel.
- Desktop icons were also a tad too high, as if they didn't "register" the top panel when ordering themselves.
- On top of all of that, keyboard shortcuts were not working (Alt + F7 to move windows around, for instance).

Thanks to having Gnome Do installed, i succeeded in invoking the Appearance menu, and noticed that visual effects were disabled. When i enabled them (any of the three other options - Normal, Extra, Custom), it said "enabling drivers" or something like that, and things started to work as before. I was happy, until i rebooted and noticed that it didn't save my changes. It doesn't change anything that I reboot, log out and back in, or use Ctrl+Alt+Backspace.

One other thing I have noticed: it also didn't save my changing the number of workspaces.

Any idea? This is my work laptop, I can't really afford to have to hack every time i boot... Thank you very much for your help!

---

### Post by G_u_s on 2010-05-02
Does anybody at all have an idea, even the slightest? Thank you!

---

### Post by Xanthomryr on 2010-05-02
Create a new entry under System -> Preferences -> Startup Applications with /usr/bin/compiz in the Command field.

[https://bugs.launchpad.net/ubuntu/+bug/563161](https://bugs.launchpad.net/ubuntu/+bug/563161)

---

### Post by G_u_s on 2010-05-03
> **Xanthomryr said:**
> Create a new entry under System -> Preferences -> Startup Applications with /usr/bin/compiz in the Command field.

[https://bugs.launchpad.net/ubuntu/+bug/563161](https://bugs.launchpad.net/ubuntu/+bug/563161)

Wow, thanks a lot. This nailed it.

Still, as said in the comments, it seems to be only a workaround. A damn good workaround that really makes me happy, granted, but a workaround anyway =)

In the comments, I've also read someone who mentioned something about Emerald being installed before the upgrade, and maybe config files messing up everything. I did have Emerald installed before. I've tried uninstalling, but it didn't solve the problem like adding "/usr/src/compiz" did.

Maybe there's something here, which would be cleaner than just force-launching compiz? And faster too: my desktop loads for a few seconds before being usable, with the menu bar being a few pixels too high (i can see it is there but too high because the windows snap on top of my screen, and the menu bar appears when i'm using two monitors with one "on top" of my main one).

I'm not sure I should mark my thread as solved for this reason. Although, again, thanks a lot because it'll save me time and frustration =)

---

### Post by G_u_s on 2010-05-04
Well, actually, it doesn't really work that well. When i do that, I've got an older-looking version of GNOME (quite "blocky"), and the new theme doesn't trigger until I launch the "Appearance" program. Strangely, just launching it is enough, I don't need to touch any button.

So, for the time being, I've removed this stuff and do the former method, which is to manually reactivate the Visual Effects in the Appearance interface after each reboot.

Any help?

---

### Post by G_u_s on 2010-05-06
Anyone, please? This is very, very annoying, and none of the fixes in the bug report actually worked =/

---

### Post by rabideau on 2010-05-07
I have placed a comment re: Avant Windows being the possible cause at: [http://ubuntuforums.org/showthread.php?t=1461210](http://ubuntuforums.org/showthread.php?t=1461210)

---

### Post by G_u_s on 2010-05-20
> **rabideau said:**
> I have placed a comment re: Avant Windows being the possible cause at: [http://ubuntuforums.org/showthread.php?t=1461210](http://ubuntuforums.org/showthread.php?t=1461210)

Thank you rabideau, but my thing happened without Avant installed. I'll go read that thread hoping to find solutions, though. Thanks =)

---

### Post by rabideau on 2010-05-20
Hi Gus

After reinstalling all my composite oriented software everything fixed itself....

---

### Post by G_u_s on 2010-05-20
> **rabideau said:**
> Hi Gus

After reinstalling all my composite oriented software everything fixed itself....
What exactly are those? I've already uninstalled (and purged) emerald, and reinstalled every compiz-related package. What did I overlook?

Thank you for your help!

---

### Post by chaanakya_chiraag on 2010-07-21
I believe gnome-settings-daemon is not being launched. Try adding gnome-settings-daemon to the startup applications.

---


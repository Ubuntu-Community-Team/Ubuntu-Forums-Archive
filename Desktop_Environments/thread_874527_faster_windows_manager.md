---
title: "faster windows manager?"
date: 2008-07-30
forum: Desktop Environments
---

### Post by justinhj on 2008-07-30
I installed compiz, but it's too slow on my old PC. I'd like to keep it around, but use something faster by default. Is there anything faster than metacity? I don't much care for special features or looks for my day to day work. 

Currently I have to type 'metacity --replace &' in the console after I login. How can I replace compiz and emerald without uninstalling?

Thanks

---

### Post by michaelomichael on 2008-07-30
Hi,

There's a panel applet that lets you do this easily; it's just called "Compiz Fusion Icon", and you can usually start it by choosing Applications->System Tools->Compiz Fusion Icon.  I *think* it was installed automatically with compiz but I'm not 100%, so you might need to install it separately.  

Here's the wiki page anyway: [http://wiki.compiz-fusion.org/CompizFusionIcon]("http://wiki.compiz-fusion.org/CompizFusionIcon")

If that doesn't work then you could try using the text editor to create a file in your home directory called ".gnomerc".  Just put a single line in it, e.g.:

```
export WINDOW_MANAGER=/usr/bin/metacity
```

When you log out and log in again, gnome should read this file and use the window manager you've chosen.

Good luck!

M

---

### Post by SunnyRabbiera on 2008-07-30
well you can use things like ice WM in gnome, as well as some of the low memory window managers...
also using blackbox is possible too

---

### Post by Ademan on 2008-07-30
I've done my own horribly unscientific tests, and in my experience, replacing metacity with other window managers like fluxbox, blackbox, or even icewm did *not* reduce overall memory consumption!

I believe that the real savings you get with lightweight window managers are like this:
(flux|black|open)box all provide their own panels, therefore you no longer need gnome-panel, and you've eliminated an entire process and its associated memory.

from there you can start stripping out other things like the gnome-keyring-daemon, gnome-power-manager, gnome-session, gnome-vfs-daemon   and so on.

(of course, the problem with all of this is: you may like using gnome's keyring and want to keep gnome-keyring-daemon, or maybe you don't like using a .gtkrc so you want to use gnome-settings-daemon instead, or you have a laptop and you want to have power management)  anywho, the point is simply that the real power of alternative window managers (in my opinion) is stripping out the cruft of full fledged desktop environments (note you can also do that with your plain jane window manager as well...)

</ramble>

Hope that helped

---

### Post by TenPlus1 on 2008-07-30
I have Openbox, obconf and obmenu installed for a lite iwndow manager and I'm using fbpanel to replace the gnome-panel since that is very small also...

---

### Post by justinhj on 2008-07-30
> **michaelomichael said:**
> Hi,

There's a panel applet that lets you do this easily; it's just called "Compiz Fusion Icon", and you can usually start it by choosing Applications->System Tools->Compiz Fusion Icon.  I *think* it was installed automatically with compiz but I'm not 100%, so you might need to install it separately.  

Here's the wiki page anyway: [http://wiki.compiz-fusion.org/CompizFusionIcon]("http://wiki.compiz-fusion.org/CompizFusionIcon")

If that doesn't work then you could try using the text editor to create a file in your home directory called ".gnomerc".  Just put a single line in it, e.g.:

```
export WINDOW_MANAGER=/usr/bin/metacity
```

When you log out and log in again, gnome should read this file and use the window manager you've chosen.

Good luck!

M

Ah yes, that was easy, I forgot about the compiz fusion icon. 

Thanks for all the other tips guys, I'll investigate some of those other window managers.

justinhj

---


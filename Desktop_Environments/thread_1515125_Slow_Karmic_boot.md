---
title: "Slow Karmic boot"
date: 2010-06-21
forum: Desktop Environments
---

### Post by Esthellin on 2010-06-21
I have been experimenting with different window managers with Ubuntu Karmic. Had a bit of fun with scrotwm but decided to go back to Metacity and Gnome.
Ever since, when logging in with gdm, it takes 20 seconds or so just to login. Normally it took about 5 seconds to login.
Has scrotwm not been fully uninstalled so it is trying to find it before switching back to metacity? That shouldn't be the case as I set the session type in the scrollbox as "Gnome" and in my actual profile, it is all set up to use metacity and not scrotwm.

I haven't found anything so far online and through the forums about having a slow karmic boot after window manager changes.
Any help?

---

### Post by Esthellin on 2010-06-22
> **oliver6419 said:**
> Here is something interesting about bootchart.

When I use it i get some kind of mounting error on the initial splash screen.

But that's not all!!! Using a stopwatch from grub to desktop with icons and the network manager password box showing takes 45 seconds.

Removing bootchart and the mounting error disappears and it appears that booting only takes 43-44 seconds. 

But the really weird thing is my "bootchart" says it takes 1:13 to boot.

There is no way I am off by almost 28 seconds using a stopwatch.

I suggest you do the same tests and see what you get.

I am also finding that after making changes, sreadahead needs to be executed during boot, and then you need to reboot again (thus resulting in two reboots). The second boot, after making system changes is a lot faster.
_________________________________________
[Managed Services Provider](http://www.4net-technologies.co.uk/)
[Managed Services](http://www.4net-technologies.co.uk/managed-services.html)
Sounds like the age-old "Have you turned it off and on again?"
Ill try that and see if it goes any faster.

I have reinstalled scrotwm. I realised that I prefer tiling window managers to stacking. And I LOVE screen real estate :P

But I am stuck with the default Karmic login background (the purple-brown mess). I can't see any options in scrotwm for setting up the backgroun, and using gnome-appearance-properties doesn't affect my background. Perhaps its an option under x?

---


---
title: "Lost my desktop after update."
date: 2013-08-06
forum: Desktop Environments
---

### Post by paul10 on 2013-08-06
Well, I decided that Windows 8 was so horrible, so I'd give Ubuntu a go as my main desktop on my Q6600 quad-core, 8 GB Dell 755 SFF PC with a Radeon HD 6450 low-profile graphics card.

I set up a desktop, including VMware Player (I have some VMs which I need to use), Citrix Receiver (I need to access a remote desktop), and added in the ATI/AMD graphics driver because the generic OS one didn't provide 3D within my VMs.

I also did a bit of customization of my preferences, added icons to the launcher, installed the unity tweak tool, set it to use my wallpaper, etc.

All looking good.

I used it a few times.

Then I booted it up today and it offered me some updates, which being a good citizen I accepted and rebooted.

Now when I login my desktop has no icons, no launcher, no panels, just a plain wallpaper.

I did Ctrl-Alt-T and got up an xterm.

I tried unity --reset but it says it's deprecated.

I tried removing .config/ .gconf/ .local/ and .cache/ and doing dconf reset -f /org/compiz/ and unity --reset-icons &disown but that didn't work, other than removing my wallpaper.

Right now my system is unusable.

Is there anything else I might do to try and resurrect it?

I really don't want to just give up, but it's not great if I can't trust update...

---

### Post by paul10 on 2013-08-06
I just tried reinstalling the ATI catalyst driver, and now the bare wallpaper display with a single terminal moves smoother.

But I still don't have a desktop.

---

### Post by stinkeye on 2013-08-06
> **paul10 said:**
> I just tried reinstalling the ATI catalyst driver, and now the bare wallpaper display with a single terminal moves smoother.

But I still don't have a desktop.

Install compizconfig-settings-manager and check the unity plugin is enabled.
```
sudo apt-get install compizconfig-settings-manager
```
Enter ccsm in the terminal to run.

---

### Post by paul10 on 2013-08-06
> **stinkeye said:**
> Install compizconfig-settings-manager and check the unity plugin is enabled.
```
sudo apt-get install compizconfig-settings-manager
```
Enter ccsm in the terminal to run.Thanks - that did it!

(I already had ccsm installed, so just had to run it.)

On enabling the Unity plugin it complained about some key bindings conflicts with gnome items.

I appreciate the help!

---

### Post by stinkeye on 2013-08-06
> **paul10 said:**
> Thanks - that did it!

(I already had ccsm installed, so just had to run it.)

On enabling the Unity plugin it complained about some key bindings conflicts with gnome items.

I appreciate the help!
Yes, the conflicts are just the alt+F1 and alt+F2 shortcut key differences between gnome and unity.
Should be disabled in the ccsm > Gnome Compatibility Plugin.

The command in 13.04 to reload unity without loosing your current compiz settings is....
```
setsid unity
```
Goodluck.

---


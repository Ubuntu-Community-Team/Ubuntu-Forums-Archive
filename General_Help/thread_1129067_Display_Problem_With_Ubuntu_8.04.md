---
title: "Display Problem With Ubuntu 8.04"
date: 2009-04-18
forum: General Help
---

### Post by jackhe22 on 2009-04-18
Hello all, I booted up my computer this morning to find that suddenly my screen resoloution is at 800x600. Ignoreing this, I went to System > Screen Resoloution. Im left with two options, 640x480 or 800x600. I'm usually at 1280x1024, and I have NO idea why, and how this happend. Also my graphics driver has stopped functioning correctly. In System > Hardware Drivers, it says:
nvidia_new (Tick in box) Not in use.

If its any help, my graphics card is a GeForce 7600GS.

Everything was working fine before so can somebody help?

Thanks,
topsyandpip56

---

### Post by Paranoid Tux on 2009-04-18
Try reinstalling the driver. In your restricted drivers dialog box, you should have some new options, try that. Let us know how you go.

Cheers,

Paranoid

---

### Post by jackhe22 on 2009-04-18
I'm worried about unticking it, when I do that, it says If you disable this, your display will no longer work, etc..

It might also be that I recently got a new moniter which uses DVI instead of VGA, should I go for an adapter?

Cheers,
topsyandpip56

---

### Post by Paranoid Tux on 2009-04-18
You could try that, but at the end of the day the worst that could happen is that you have to get the display back up from the shell. You can always boot into rescue mode from grub and retick the box.

Good luck with it.

---

### Post by jackhe22 on 2009-04-18
Okay I'm gonna try the adapter, I'll tell you how I get on

BTW, its also a Wubi installation if that means anything.

---

### Post by jackhe22 on 2009-04-18
Okay, ive managed to reinstall it, Compiz and such is fine, but its still jammed on 800x600, or now 320x240. Ive also installed the Nvidia manager, and thats been no help. PLEASE HELP!

---

### Post by jackhe22 on 2009-04-18
Never mind, Ive uninstalled Wubi, perhaps Ubuntu is just not for me. Thanks anyway Paranoid Tux.

---

### Post by CatKiller on 2009-04-18
> **jackhe22 said:**
> Never mind, Ive uninstalled Wubi, perhaps Ubuntu is just not for me.

That's a shame. It's often quite a simple fix. Perhaps when you're feeling adventurous again, you should try a full install with some future version. X is in a state of flux at the moment, with some major architectural changes going on. Perhaps when that's all settled down a future version will be more to your liking.

---

### Post by jackhe22 on 2009-04-18
I think it might actually be my monitor! Windows thinks the max is 2048xsomethingstupid, Ubuntu thinks it 800x600! Its real max is 1280x1024!
I might oneday try again with my old CRT, but not now, its in the attic. Thanks for your help guys. -Actually, maybe tomorrow I thought compiz was beautiful.

---

### Post by CatKiller on 2009-04-18
> **jackhe22 said:**
> I think it might actually be my monitor! Windows thinks the max is 2048xsomethingstupid, Ubuntu thinks it 800x600! Its real max is 1280x1024!
I might oneday try again with my old CRT, but not now, its in the attic. Thanks for your help guys. -Actually, maybe tomorrow I thought compiz was beautiful.

There's something called EDID, which is a method for your computer, through your graphics card, to tell your Operating System which resolutions and refresh rates it can do. Many combinations of monitor and graphics card don't manage to pass this information on correctly; largely, I suspect, because manufacturers have grown accustomed to putting registry entries in Windows instead (this is what "monitor drivers" in Windows actually do).

Since this information isn't being passed on, and X doesn't want to damage your monitor by setting a refresh rate that's too high, it defaults to a really low value that won't damage anything. Unfortunately, it also means that you can't use higher resolutions. The solution is simply to tell X which ranges you want it to use instead of the low defaults.

X's configuration is stored in /etc/X11/xorg.conf. You'll need to find out the refresh rate ranges your monitor supports, horizontal and vertical. With a bit of luck, these should be in the manual or specifications for your monitor. You put these ranges in your xorg.conf's "Monitor" Section.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

The bit that you want to enter will look something like this.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```

where aa-dd are the numbers that you found from your monitor's specifications.

---


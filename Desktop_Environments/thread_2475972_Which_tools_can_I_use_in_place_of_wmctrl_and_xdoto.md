---
title: "Which tools can I use in place of wmctrl and xdotool in Wayland?"
date: 2022-06-13
forum: Desktop Environments
---

### Post by Paddy Landau on 2022-06-13
I've been playing with Ubuntu 22.04. The default window manager, Wayland, seems to be fine, apart from something that I need for some of my scripts: Window control (how ironic) and mouse and text control.

In X.Org, wmctrl and xdotool do the job well.

In Wayland, they don't work.

The proposed replacements include wtype, specifically for Wayland, and ydotool. Unfortunately, neither of them works in Wayland, or even in X.Org.

So, my question is:

**Which tools can I use in place of wmctrl and xdotool in Wayland?**

---

### Post by vanadium on 2022-06-13
For now, there will be no other tools than these...

I today managed to get "abc" typed in the terminal using "ydotool", however... ydotool must run as root.

There is a daemon, ydotoold, that is intended to avoid the need for ydotool to create a virtual input device each time, reducing delays etc. In my first experiments, it loads but then crashes when using ydotool. The version shipped with Ubuntu 22.04 is 0.1.8-3. It may be worth the trouble to try installing the "refactored" version 1.0.1 (which now only works with the daemon).

---

### Post by TheFu on 2022-06-13
Wayland isn't a Window Manager. It is a display server.

These scenarios are why Wayland is useless to me as well. For now, just use X11.

---

### Post by vanadium on 2022-06-13
I tested my first working ydotool macro (currently under Xorg, though). Version 1 only works with keycodes, so coding is less friendly than with xdotool. Version 1 also dropped command chaining.

The macro inserts the current date:

```

#!/bin/sh
sleep 0.2 ; ydotool type $(date +"%Y-%m-%d")

```

The equivalent code with xdotool was:

```

xdotool keyup ctrl+shift+d sleep 0.4 type $(date +"%Y-%m-%d")

```

The "sleep" is also needed in ydotool. It gives you time to release the shortcut key before typing begins, which otherwise is affected by the modifier keys. In xdotool, I need 0.4 seconds for it to work reliable in all circumstances. 0.2 seems enough in ydotool (after quick experimentation only).

The keyup statement in xdotool is there to release my shortcut key before typing begins. It allows the macro to work even when you keep down the shortcut key. In ydotool, that trick does not work (ydotool releases these keys in the virtual input device that it creates rather than the keys of your keyboard).

So there is a start of it working, but with drawbacks rather than advantages, except for the fact that it *works* in Wayland, over xdotool in xorg.

---

### Post by TheFu on 2022-06-13
I use cnee to record interactions, then play them back later.  I try to record the shortest possible set of events, then use bash to script those in a loop to happen over and over and over as needed.

Professional web developers use similar tools for automatic testing of their webapps, but the GUI tool (browser or something else) shouldn't matter.  Far too many interfaces are extremely busy and can only be worked using mouse point-click actions.

To my knowledge, Wayland has no support for these workflows.
And let's be very honest, X11 allows them due to security faults in X that allow outside programs to control input devices.  Because X11 is network agnostic, this can mean that remote people can send commands to the X-Client for mouse and keyboard inputs, if there isn't a firewall in the way.  X11 uses UDP, not TCP, so if done by a smart attacker, the inputs can use spoofed source IPs.  In the last 5 yrs or so, X11 has added some security to make these remote commands harder, but it is fairly weenie security.

I'm not usually anti-security, but I'm addicted in some web-scrapping scripts that run for 30 minutes while I do things useful elsewhere instead of boring, repetitive, stuff.

ydotool writes directly to  /dev/uinput 
```
$ ll /dev/uinput 
crw------- 1 root root 10, 223 Jun 11 09:34 /dev/uinput

```
those permissions mean it has to be run as root to work. That's bad.

---

### Post by Paddy Landau on 2022-06-13
> **vanadium said:**
> I today managed to get "abc" typed in the terminal using "ydotool", however... ydotool must run as root.
There is a daemon, ydotoold…
For me, ydotool crashes with a dump, whether or not I run ydotoold, every time. I did figure out that it needs sudo.
> **vanadium said:**
> It may be worth the trouble to try installing the "refactored" version 1.0.1.
Where do you find the refactored version?
> **vanadium said:**
> The keyup statement in xdotool is there to release my shortcut key before typing begins.
I [FONT=courier new]sleep 0.2s[/FONT] and then include [FONT=courier new]--clearmodifiers[/FONT] with xdotool, which always seems to work for me.
> **TheFu said:**
> … ydotool … has to be run as root to work. That's bad.
Agreed.

I realise what people are saying about security, but we need to be able to automate tasks.

---

### Post by TheFu on 2022-06-13
We can fight with Wayland or just stay with X11.  It isn't like there are plenty of non-Wayland distros and we can still strip Wayland completely from Ubuntu, so that wouldn't be a reason to change distros. Heck, there are many other things that Canonical is pushing which would be much higher reasons to change, IMHO.

20.04 still has 3 yrs of support remaining. Many things change change in 3 yrs.  Snaps might become the ideal packaging systems.  It could happen, right?  No, I'm not laughing. /s

---

### Post by Paddy Landau on 2022-06-14
> **TheFu said:**
> … that wouldn't be a reason to change distros.
I'm intend to stay with Ubuntu, but until this is fixed, I'll have no choice but to use Ubuntu on X.Org when upgrading to 22.04.
 > **TheFu said:**
> Snaps might become the ideal packaging systems.  It could happen, right?
Theoretically, they could. But they'd have to be a lot more like flatpak: Eliminate the stupidly long startup time after a reboot (which Canonical says that it's trying to fix); and provide flexibility with the security model (as flatpak can do with Flatseal). The lack of flexibility is a problem; for example, I can't use the snap version of gedit (you can't edit files outside specific folders inside your home).

---

### Post by vanadium on 2022-06-14
Also on 22.04, Xorg is still fully available and functional. It takes clicking a button on the login screen to land on a fully functional Xorg session of Ubuntu. So nobody is forcing anybody to use Wayland for the foreseeable future.

I documented my installation of ydotool 1.01 [over on Askubuntu](https://askubuntu.com/a/1413830/558158). The new version has been fully stripped down, which probably is a good thing:

- It now only runs using the daemon
- The record function has been removed (and hopefully will be done in a separate executable - this is what xdotool has been lacking all the time)
- No command chaining anymore
- Codes must be specified to indicate the keys (which takes away the problem with different keyboard layouts)

[quote=TheFu] To my knowledge, Wayland has no support for these workflows.[/quote] It is rather that Wayland currently lacks the tools. With a record function, ydotool already would come close to what you achieve now with cnee.

[quote=TheFu] … ydotool … has to be run as root to work. That's bad.[/quote]
Yes it is, but then you refer to the security issues on X11, which still are a million times worse &#128578;.

---

### Post by Paddy Landau on 2022-06-14
> **vanadium said:**
> I documented my installation of ydotool 1.01 [over on Askubuntu]("https://askubuntu.com/a/1413830/558158").
Thank you for this. The problem that I have is that I need not only a replacement for xdotool but also wmctrl. I'll have to continue with X.Org until Wayland has a suitable replacement.

---

### Post by vanadium on 2022-06-14
Replacing `wmctrl` will be less obvious. Procedures to manage windows now depend on the window manager/compositor, and differ between Gnome, KDE, Sway, etc. With the removal of Xorg, a layer of standardization is gone.

---

### Post by TheFu on 2022-06-14
> **vanadium said:**
> Replacing `wmctrl` will be less obvious. Procedures to manage windows now depend on the window manager/compositor, and differ between Gnome, KDE, Sway, etc. With the removal of Xorg, a layer of standardization is gone.

Not if an  ICCCM-compliant WM is used.  Gnome3+ is breaking those standards.  That's their choice and a huge reason I'll not use Gnome.  Gnome thinks that the programs should have control over the window decorations.  I find that extremely obnoxious.  gnome-disks started doing this. It is ugly and non-standard.  We've been trained over decades to recognize what a "window" looks like.  Allowing each program to have a different look for the 'window' breaks that.

---

### Post by Paddy Landau on 2022-06-14
> **TheFu said:**
> Gnome thinks that the programs should have control over the window decorations. I find that extremely obnoxious. gnome-disks started doing this. It is ugly and non-standard.
I fully agree with you.

Google Chrome does this, but at least it's optional. If every app uses its own interface, it'll be metaphorical chaos.

---


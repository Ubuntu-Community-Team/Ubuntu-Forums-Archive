---
title: "Set Window Decorator to Compiz &amp; Emerald"
date: 2010-02-17
forum: Desktop Environments
---

### Post by neu5eeCh on 2010-02-17
I've been using Fusion-Icon to set the Windows Manager and Decorator to Compiz & Emerald respectively, but I'm having to do this every time I reboot KDE 4.4. What do I need to edit in order to make Compiz and Emerald permanent masters of the desktop?

---

### Post by Zorael on 2010-02-17
If you have Compiz (and possibly the **compiz-wrapper** package) installed, you should be able to set it to be your default window manager in System Settings -> Default Applications -> Window Manager. You may need to log out and back in, not sure.

As for Emerald, doesn't Compiz still have a Window Decorator plugin in ccsm, in which you can specify what binary to run?

---

### Post by neu5eeCh on 2010-02-17
Thank you Zorael! I found the same information elsewhere, just before you posted your response.

One gets the sense that Linux is in transition. A lot of the information is still command line oriented (but increasingly outdated), while the newest, like yours, references the windows interface. "Just choose such and such an option..."

I love  being able to use the command line, but it would take days of repetitive practice before the command line structure really began to sink in (with me).

---

### Post by Hero of Time on 2010-02-18
Funny, on my Xfce4 systems, I set Fusion-Icon to auto start on logon and the icon remembers what WM I was using and sets that one directly. If I set it to use Compiz, Compiz will be started (my windows/panels might flash once because of it), if I set it to Xfwm4, then Xfwm4 starts as it normally would. Are you sure that Fusion-Icon starts automatically?

---

### Post by neu5eeCh on 2010-02-18
Hi Hero. It sounds like the XFCE windows manager starts up first in both instances. The first time I tried to establish compiz as the windows manager, I created a symbolic link to fusion-icon in the start-up folder. This loaded KWIN first, then fusion-icon. Just as you describe, the panels would flash because they were switching desktop managers. In KDE, however, I discovered (as Zoreal wrote) that one can specify which Windows Manager to use under System Preferences. This means that only one Windows Manager is booted (rather than one and then the other).

The same can be accomplished in XFCE, [according to what I've read]("http://wiki.archlinux.org/index.php/Compiz"), if not with the same push-button ease.

---

### Post by Hero of Time on 2010-02-18
That's a nice howto, didn't know that one, thanks. I'll stick with my current method though, as I can easily reload Compiz in case it crashes (or Emerald crashes, one of the two).

I'm considering switching to Arch because of it's policy to be as no-nonsense as possible. I'll try it in a VM first, in case I don't like it, but from what I've read, it's not that hard compared to Ubuntu.

---


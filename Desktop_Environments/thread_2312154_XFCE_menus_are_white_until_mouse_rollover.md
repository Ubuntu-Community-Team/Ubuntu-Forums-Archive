---
title: "XFCE menus are white until mouse rollover"
date: 2016-02-02
forum: Desktop Environments
---

### Post by henrylaw on 2016-02-02
Ubuntu 14.04 desktop 32-bit, with xubuntu package installed over the top (this is a workstation build customised to look like Windows, for teaching basic IT skills in a community centre).

Symptoms: the applications menu (customised with a Windows start button graphic ...) brings up a menu which is completely blank (white); if you roll the mouse over it the relevant items appear.  Sub-menus are also white, and appear on rollover.  Applications which come up are seriously mangled, and their clickable options (buttons and so forth) also remain white until mouse rollover.  And pretty soon everything seems horribly slow.

  [Here's a screenshot]("http://www.lawshouse.org/download/XFCEBlankMenus.png") of the applications menu doing its thing.

I thought this was a graphic card fault but it's appearing on several machines, including one that I've just built on different hardware and fully patched.  It's holding up teaching operations and I'm completely baffled.  Suggestions for debugging, anyone?

---

### Post by Dennis N on 2016-02-02
If it's not installed, install the package **gtk-theme-config**

Settings > Theme Configuration

will launch a little dialog to change menu text color and menu background color.

---

### Post by henrylaw on 2016-02-02
Update: this doesn't just apply to XFCE menus.  I restarted the machine and tried Libreoffice: no menus, no text in the pulldown menus. As shown in [this new screenshot]("http://www.lawshouse.org/download/Libreoffice.png").  The underbar characters in the menus, showing the default actions, are still there, bizarrely.

---

### Post by henrylaw on 2016-02-02
Dennis, thank you for replying and for the suggestion.  But this can't be a colour setting problem, since it doesn't happen all the time.  I just rebooted the machine (see my other reply in the thread) and the first time the user desktop came up the menu items were all right, then shortly afterwards the error behaviour started again.

---

### Post by Dennis N on 2016-02-02
You said it is "a workstation build customised to look like Windows", so the customizing may have introduced some problems. It's hard to say from here. My thinking is that it is a theme problem. Basic questions: What gtk theme are you using? What window manager theme? Did you make modifications to the theme configuration files?

If it is important to have something that looks like Windows, there is Zorin OS, which is said to be able to mimic Windows 7, XP, or 2000. Depending on what lengths you are willing to go, it might be worth considering. It is based on Ubuntu, so your Ubuntu skills should transfer.

---

### Post by henrylaw on 2016-02-03
The theme is one I've been using for some time, called "win2-7_0.1_all" from a PPA repository called "'ppa:upubuntu-com/gtk3".  I think you're right that this theme is the culprit.  I've been saying that "nothing has changed" but actually I install the theme from the PPA afresh each time I build a machine, and it's possible that it's changed.  I'm experimenting now without the theme, with everything else the same, and so far I don't have this "blank menu" problem.  Thanks again for the pointer.

---

### Post by vasa1 on 2016-02-03
> **henrylaw said:**
> ... "'ppa:upubuntu-com/gtk3". ...
In addition to all that Dennis N mentioned, you may want to be extra careful with your choice of themes and ensure that they 
support _both_ gtk2 and gtk3
support the gtk3 version you have on your system. For example, the "Arc theme" [isn't meant for Ubuntu 14.04 or 14.10]("https://github.com/horst3180/arc-theme") but only for shinier Ubuntus.

I'd also add that one should stay away from ppas and software from external sources unless sure of the consequences.

---


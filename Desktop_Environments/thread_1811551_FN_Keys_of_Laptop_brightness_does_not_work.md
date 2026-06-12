---
title: "FN Keys of Laptop brightness does not work"
date: 2011-07-25
forum: Desktop Environments
---

### Post by xaviercab on 2011-07-25
I have installed Xubuntu 11.04 on a HP Probook 4510S and the FN Keys of brightness only works when i on the login screen (gdm). Until i enter to my desktop the FN Keys stop Working. This is a XFCE Issue?

I have another Laptop, a IBM THinkpad X40, with the same Xubuntu 11.04 and the FN Keys works perfect! Even the keyboard light Works!

I think this is a ACPI related problem, i google it the problem with out a specific issue like this.

The only thing that i can do it is use of xbacklight when i'm on my session.  :(

root@xavierc-lt-xub:~# ls /proc/acpi/
ac_adapter  battery  button  event  wakeup
root@xavierc-lt-xub:~#

---

### Post by xaviercab on 2011-07-25
Definetely a XFCE issue, i just install Gnome on XUBUNTU and all FN keys Works...  :(

---

### Post by Toz on 2011-07-25
Very interesting. You should file a bug report at: [https://bugzilla.xfce.org/]("https://bugzilla.xfce.org/")

---

### Post by enimeizoo on 2011-07-25
I can't remember where but I know there are scripts to interact with ACPI settings. Did you try the ones for the brightness to see if it is a key issue or a script issue?

---

### Post by Toz on 2011-07-25
Whats really interesting is that it works at the gdm login screen, which leads me to believe its not an acpi issue. Something in xfce is blocking the fn key combinations. First time I've seen this.

---

### Post by enimeizoo on 2011-07-25
The fn+X combination do send keysyms, it might just be that the said keysym is unbound by xfce (I don't really see how, though), or that another shortcut overrides it (seems more likely to me, but again, not common). Also, xfce could change the keyboard layout, or something, changing keysyms sent by the fn keys, without changing the bindings (I don't even know how those bindings are made, I think they are in the acpi scripts). I just think it is worth looking for this kind of things.
Checking the acpi scripts would ensure that the problem is with the keys. Then binding the same key, or another to the right script could fix the issue.
Actually, just checking that the keyboard model and layout selected in both gnome an xfce would be a good idea, too.

---


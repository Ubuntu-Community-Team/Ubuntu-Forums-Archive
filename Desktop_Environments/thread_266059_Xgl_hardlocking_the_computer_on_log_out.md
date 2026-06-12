---
title: "Xgl hardlocking the computer on log out"
date: 2006-09-26
forum: Desktop Environments
---

### Post by warden on 2006-09-26
Hello everyone,

As I understand xgl is still in development, so one can expect this to be a bug, but I'm really annoyed by the following problem:

When working in gnome/kde session xgl runs perfectly, but sometimes when I log out, instead of the greeting I get just an empty white screen (with a little grey box in the middle)! Keyboard gets locked, ctrl+alt+f1 instead of the tty1 console shows vertical RGB lines across the screen and then everything hangs (including a remote ssh session which I tried to use to kill the xgl!). On the good ol' X everything worked like a charm so it's not a hardware problem...

Has anyone got any ideas as to what can be the problem? :confused: 

Dapper Drake 6.06 on Acer 5022 Laptop, 1.6GHz Turion with ATI Mobility Radeon X600/64MB

---

### Post by graigsmith on 2006-09-26
it's an ati driver bug. not much you can do but wait for ati to develop drivers that aren't complete crap.  they actually said they fixed the logout bug. but every time i logout, or change users. with my x800, it just crashes just like you describe.

---

### Post by warden on 2006-09-26
And I hoped that I would never have to reboot a Linux box for any reason, especially not because of a system hang! Well, I don't want to uninstall Xgl, because font anti-aliasing on old X.org looks like crap on my LCD and I can't use compiz/beryl either, so I guess that we'll just have to wait (and pray... and send angry e-mails to ati support - if they ever read them)...

Thanks for the fast response...

---


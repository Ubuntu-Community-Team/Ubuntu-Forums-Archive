---
title: "Standby instead of Shutdown"
date: 2018-11-21
forum: Desktop Environments
---

### Post by fabiopazzini on 2018-11-21
Hi all, I've recently installed Xubuntu 18.04 i386 on an old Netbook Acer Aspire One. It runs nicely, but there is a minor error going on: when I go to Shutdown via power button or by clicking on the menu/shutdown, it acctualy goes on Stand By, instead of properly shutting down. When I open Terminal and just type plain "shutdown", it shuts down as it should.

Any clues? Any tips?

I'm not an advanced Linux user, nor an intermediate, in terms of knowing commands in terminal, but I'm pretty good at searching the web for help and tips, and always did several terminal stuff.

Also, I must say that previously, this netbook was running Lubuntu (I guess the last one was 14.04), and Shutdown was never an issue. If I can't fix the regular Shutdown buttons, I'm happy with a solution that would trigger terminal shutdown with a link in the desktop.

Thanks for any help!

---

### Post by ajgreeny on 2018-11-21
On my Xubuntu systems for the past few years I have set keyboard shortcuts to both standby and shutdown, easily done in Xubuntu from the Keyboard section of Settings Manager.

In the Application Shortcuts tab click on Add and in the command box add ***xfce4-session-logout --halt*** for the shutdown command or ***xfce4-session-logout --suspend*** for the standby command, click OK and you will be asked to press a key or keys for the shortcuts; I use **Pause/Break** for standby and **Super (WinKey)+Pause/Break** for shutdown.

Take care, you get no confirmation dialogue or second chance with these shortcuts so the shutdown one will lose any unsaved data in open applications.

---

### Post by fabiopazzini on 2018-11-22
> **ajgreeny said:**
> On my Xubuntu systems for the past few years I have set keyboard shortcuts to both standby and shutdown, easily done in Xubuntu from the Keyboard section of Settings Manager.

In the Application Shortcuts tab click on Add and in the command box add ***xfce4-session-logout --halt*** for the shutdown command or ***xfce4-session-logout --suspend*** for the standby command, click OK and you will be asked to press a key or keys for the shortcuts; I use **Pause/Break** for standby and **Super (WinKey)+Pause/Break** for shutdown.

Take care, you get no confirmation dialogue or second chance with these shortcuts so the shutdown one will lose any unsaved data in open applications.


Thanks a lot!

---


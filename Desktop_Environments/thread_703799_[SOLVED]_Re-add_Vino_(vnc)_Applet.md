---
title: "[SOLVED] Re-add Vino (vnc) Applet"
date: 2008-02-21
forum: Desktop Environments
---

### Post by Son of Silas on 2008-02-21
I accidently deleted the vino applet from the panel at the top of the screen that allows me to terminate remote VNC desktop sessions.

After some kind help from people on the forum I solved half my problem (disconnecting myself from the server on which i deleted it) but now I need to re-add the applet so I can easily disconnect VNC sessions.

Can anyone suggest anything?

[IMG]http://www.thedawnmist.co.uk/File_Transfers/applet2.jpg[/IMG]

---

### Post by imoatama on 2008-02-21
Which applet are you referring to? Have you checked your setting in vino-preferences (Preferences->Remote Desktop)?

Was the applet always there, or just when you were accepting vnc connections?

---

### Post by Son of Silas on 2008-02-22
Its the little icon that appears on the desktop of the computer that you connect to. When you right click it it allows you to disconnect any connected clients.

Its really useful if you VNC to a server in fullscreen mode. It allows you to disconnect yourself so you can use your client PC again!

[IMG]http://www.thedawnmist.co.uk/File_Transfers/applet2.jpg[/IMG]

---

### Post by Son of Silas on 2008-02-22
OK... I've fixed it.

I found steps on another forum to reset gnome-panel to default settings.

> 1. rm -r ~/.gconf/apps/panel or just move the folder elsewhere if you want to back it up.
2. Log out of GNOME, then back in.

---


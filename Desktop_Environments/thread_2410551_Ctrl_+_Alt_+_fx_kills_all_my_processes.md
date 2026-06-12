---
title: "Ctrl + Alt + fx kills all my processes"
date: 2019-01-17
forum: Desktop Environments
---

### Post by crusty1337 on 2019-01-17
I'm running Ubuntu 18.10

I'm running maybe 5 applications in gnome and everything is fine.

I press Ctrl + Alt + f2 and I can see tty2 as expected. Logging in and typing "w" shows that tty2 is the only logged in session.

I press Ctrl + Alt + f1 and I return to the gnome gui, but I'm logged out. Logging in again shows no applications running.

Why is my session being dropped when I change to another terminal?

My laptop is connected to a USB-c dock with 2 other monitors connected. That wouldn't be the cause would it?

---

### Post by The Cog on 2019-01-17
I thought the GUI was normally on Alt-F7. Have you tried that one?

---

### Post by CatKiller on 2019-01-17
> **crusty1337 said:**
> Why is my session being dropped when I change to another terminal?
I don't think it is. I think you're experiencing an X crash when you change back.

---

### Post by crusty1337 on 2019-01-17
> **The Cog said:**
> I thought the GUI was normally on Alt-F7. Have you tried that one?

AFAIK that is obsolete information, and the GUI is now on Alt+F1 (or maybe the login screen is on Alt+F1 and the GUI is on Alt+F2 ... I'm a little confused now)

Change log from Ubuntu 17.10 ([https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Ubuntu_Desktop](https://wiki.ubuntu.com/ArtfulAardvark/ReleaseNotes#Ubuntu_Desktop)):
> **GDM**[COLOR=#333333][FONT=&amp] has replaced LightDM as the default display manager. The login screen now uses virtual terminal 1 instead of virtual terminal 7.[/FONT][/COLOR]

---

### Post by crusty1337 on 2019-01-17
> **CatKiller said:**
> I don't think it is. I think you're experiencing an X crash when you change back.

Ah hah! You've got it in one CatKiller. Nice catch.

> 

... gnome-session[1982]: gnome-session-binary[1982]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
... gnome-session[1982]: gnome-session-binary[1982]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
... gnome-session-binary[1982]: WARNING: App 'org.gnome.Shell.desktop' exited with code 1
... gnome-session-binary[1982]: Unrecoverable failure in required component org.gnome.Shell.desktop
... gnome-session[1982]: gnome-session-binary[1982]: CRITICAL: We failed, but the fail whale is dead. Sorry....
... gnome-session-binary[1982]: WARNING: App 'org.gnome.Shell.desktop' respawning too quickly
... gnome-session-binary[1982]: CRITICAL: We failed, but the fail whale is dead. Sorry....
... gdm-password][1884]: pam_unix(gdm-password:session): session closed for user USERNAME



Seems to be an issue with my laptop dock.
Doesn't happen when the dock is disconnected.

Thank you very kindly.

---


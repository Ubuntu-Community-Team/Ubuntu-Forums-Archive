---
title: "Nautilus won't restore as default file manager"
date: 2009-03-03
forum: Desktop Environments
---

### Post by RetroX on 2009-03-03
I recently downloaded kdebase and xfce4 via synaptic so that I could have all of the default apps from both KDE and XFCE (Konqueror, Thunar, etc).

However, after I opened Thunar (or installed XFCE; I don't know which but I opened it right after it was installed), it became my default file manager.

I've searched for various ways of restoring Nautilus, without success.  Is there a way to make Nautilus my default file manager without uninstalling Thunar or XFCE (I still want to keep it, but I don't want it as default).

---

### Post by benerivo on 2009-03-03
See [this page]("http://www.psychocats.net/ubuntu/nonautilusplease") for instructions on restoring nautilus to the default file manager.

---

### Post by RetroX on 2009-03-03
Erm, I tried that.  In fact, that was the first method I tried.

It didn't work.  It said "Nautilus is now your default file manager," yet things still opened in Thunar.

---

### Post by ellgor on 2009-03-04
Hi,

You don't mention what distro you are using, so, do you actually have "Nautilus" installed?

Regards, Ellgor.

---

### Post by RetroX on 2009-03-04
> **[ubuntu]** nautilus won't restore as default file manager
:(

EDIT: Although, I'm using 8.10 (Intrepid Ibex), if that's what you meant.

---

### Post by narnie on 2009-05-30
bump

---

### Post by TDFZ on 2009-10-31
You could always pop in a cd or mount a removable device.  When it asks for the action to be performed chose Open Folder(nautilus).  Then go to Places>Computer Right Click on the Removable and from there it will let you chose the default open with command.  You might have to click reset in the bottom right hand corner before you chose nautilus as the default action.  This should reset all folders to open with nautilus.
I know this is kinda old just want to help out anyone who comes across this prob.

---

### Post by Abra on 2010-03-03
> **TDFZ said:**
> You could always pop in a cd or mount a removable device.  When it asks for the action to be performed chose Open Folder(nautilus).  Then go to Places>Computer Right Click on the Removable and from there it will let you chose the default open with command.  You might have to click reset in the bottom right hand corner before you chose nautilus as the default action.  This should reset all folders to open with nautilus.
I know this is kinda old just want to help out anyone who comes across this prob.

I know the subject is quite old but, I wanted to inform that above method works for 9.04, too.
Instead of mouinting a new device, I right clicked "Filesystem" folder in computer:/// and chose nautilus as the default.
Thanks for the help.

---

### Post by COKEDUDE on 2011-06-06
> **benerivo said:**
> See [this page]("http://www.psychocats.net/ubuntu/nonautilusplease") for instructions on restoring nautilus to the default file manager.

Thx for this.

---

### Post by eightdollarbeer on 2011-10-25
run this command its the preferred app changer for xfce set things back to nautilus exo-preferred-applications

---

### Post by CinoxFellpyre on 2011-12-07
Hate to bump this, but I am running on 11.04, using xubuntu.

I don't wanna get into WHY I am using xubuntu, but it involves a mishap with compiz that i cannot recover now, so gnome is out of the question.

Anyways, I tried to use the ./defaultthunar script I was told to. I ran it once and got the confirmation that Thunar's default.

Problem is, I tried repeating it again to get my Nautulis back, and....well....

```
Changing to application launcher directory


Restoring backup files


Removing backup folder


Restoring Nautilus launcher

Removing 'local diversion of /usr/bin/nautilus to /usr/bin/nautilus.old'

Making Nautilus manage the desktop again

 17:59:14 up 14 min,  1 user,  load average: 0.38, 0.30, 0.32
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
cinoxfel tty7     :0               17:44   14:28   1:30   0.03s /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
root@cinoxfellpyre-Satellite-L305:/home/cinoxfellpyre# /usr/share/themes/NOX/gtk-2.0/gtkrc:233: Murrine configuration option "gradients" is no longer supported and will be ignored.

(nautilus:2994): EggSMClient-WARNING **: Failed to connect to the session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)

```


I tried this normal, I tried this in root (against better judgement). I'm still using xcfe, I just wanna be able to move my desktop icons like I used to, and I really, REALLY hate thunar. :C

Maybe some assistance with this?

---


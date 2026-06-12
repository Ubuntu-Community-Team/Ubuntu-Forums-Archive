---
title: "GNOME apps using file system take a long time to load"
date: 2009-03-10
forum: General Help
---

### Post by tmastran on 2009-03-10
Something is timing out causing most GNOME applications to take a long time to load. About 20 seconds. This occurs with applications using the file system. Things like gnome-screenshot, gnome-system-monitor, and even FireFox. File dialogs are also slow to open.

This warning prints on a console, strace shows that the delay is here:

(gnome-screenshot:23043): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.HalVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the networkconnection was broken.

Any ideas?

---

### Post by tmastran on 2009-03-10
Update, If I sudo the gnome application, I do not get this warning and the application starts right up. Is there something security related I could look at?

---

### Post by Mr. Brownstone on 2009-04-27
I'm getting the same symptoms. "Browse" for upload dialogs in Firefox take ages to load, as do "File > Open" in Firefox and gedit and such. Running the application using sudo "fixes" the issue.

EDIT - I'm using a fully up-to-date 9.04.

---

### Post by kerry_s on 2009-04-27
sudo should be used with care, you could be or have screwed up the permissions.

can you post your ~/.xsession-errors

---

### Post by kc600 on 2009-06-07
I also get this in F-spot and LinuxDC++.

I did 'tail -f ~/.xsession-errors' but nothing shows there when saving a Firefox page.

---


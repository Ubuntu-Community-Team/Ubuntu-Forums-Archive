---
title: "Nautilus is driving me crazy (mount issue)"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Anthem on 2006-08-30
I have all of my photographs on a network server.  I need to find a specific photo.  In Windows and KDE, I just look through the thumbnails.  GNOME, however, despite claiming to be a pro-network environment, is apparently incapable of displaying thumbnails on a network drive.  That's ridiculous, but whatever.  Features confuse the user.  I get it.

Ok fine, I think, I'll just install F-Spot.  Easy.  Once in F-Spot, though, I can't figure out how to navigate to the folder holding my photos.  When I connected to that server, it put a folder on my desktop.  When I navigate to the desktop in the File Open Dialogue, though, the network drive doesn't appear.  It doesn't show up in "Computer" either.

How is this supposed to work?  And why is the process so brain-dead?  I've had the same problem in the past with my music, which is also kept on my media server.

It shouldn't be this hard... especially when Windows and KDE do this so easily, quickly, and well.

---

### Post by mssever on 2006-08-30
In Nautilus, try going to Edit > Preferences > Preview tab. There's a drop-down labeled show thumbnails. Change it to always. I imagine the Gnome devs felt that making thumbnails over slow network connections would slow Nautilus down.

What kind of network connection are you dealing with? NFS? SMB? It may be that Nautilus is handling all of the mounting stuff itself, rather than assigning it a regular mount point.

On another note, I really like Picasa for pictures. You can get it by adding ```
# Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free
``` to your /etc/apt/sources.list then doing ```
sudo apt-get update && sudo apt-get install picasa
```

---

### Post by Anthem on 2006-08-31
> **mssever said:**
> What kind of network connection are you dealing with? NFS? SMB? It may be that Nautilus is handling all of the mounting stuff itself, rather than assigning it a regular mount point.
It's a samba share from a linux-based NAS device.

---

### Post by mssever on 2006-08-31
So are you getting thumbnails in Nautilus now?

As far as the other issue goes, if you want to be able to mount a samba partition like a normal partition, this link might help: [http://us3.samba.org/samba/docs/using_samba/ch05.html#samba2-CHP-5-SECT-4.1](http://us3.samba.org/samba/docs/using_samba/ch05.html#samba2-CHP-5-SECT-4.1)

---

### Post by Anthem on 2006-08-31
> **mssever said:**
> So are you getting thumbnails in Nautilus now?

As far as the other issue goes, if you want to be able to mount a samba partition like a normal partition, this link might help: [http://us3.samba.org/samba/docs/using_samba/ch05.html#samba2-CHP-5-SECT-4.1](http://us3.samba.org/samba/docs/using_samba/ch05.html#samba2-CHP-5-SECT-4.1)
Yeah, I get it now.  I had the option to display as list or display as icons, but no option to display as thumbnails.  Now I know that there isn't a third option to display as thumbnails, but a switch that makes all file views (icon or list) act as thumbnail views.  I don't think that's a good design decision, but I'll live with it for now.

Regarding the samba mount, I'll give it a try.  I take it that's the only way for programs to connect to the server?

---

### Post by mssever on 2006-08-31
> **Anthem said:**
> I don't think that's a good design decision, but I'll live with it for now.
I agree with you there.
> Regarding the samba mount, I'll give it a try.  I take it that's the only way for programs to connect to the server?
It appears so. In Nautilus, you can type Ctrl+L and then smb:// to browse the SMB network. It would be nice if the Gnome open/save dialog would support that.

When I looked in to mounting my samba shares some time ago, I decided that it would be simpler to use NFS instead. If you don't need to access that share from Windows, that might be an easier solution. Plus, NFS preserves file permissions.

---

### Post by hyperandy on 2008-02-11
I know this is a "Super" old post but I was just on-line researching the same thing and I am using Ubuntu 7.10 after trying 2 different file managers and not really liking them all.
 I went into edit --> preferences --> then to the preview tab and was able to configure what I was looking for. I set it to show thumbnails as long as the file is under 5MB. I post this only because the dummy I am never looked there to start with, I guess I was just use to older Nautilus and assumed it wasn't there still, I assume if I didn't know right off the bat someone else might be in the same boat. Anyway, it is there in Nautilus 2.20.0 which is default on Ubuntu 7.10.

---


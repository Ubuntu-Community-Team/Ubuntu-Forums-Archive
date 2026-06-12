---
title: "how to properly configure file associations"
date: 2014-11-29
forum: Desktop Environments
---

### Post by geoffmen on 2014-11-29
I have a problem with deluge opening the files with the wrong applications. On the deluge forums I was answered that deluge uses xdg-open therefore which app is chosen is out of its control.
I ALREADY HAVE setup my prefered applications in the gui control center / system settings, AND ALSO through the file manager in the files' properties dialogs. This problem happens across systems, wether it's XFCE, Gnome, MATE, cinnamon...
So where does xdg-open truly take its file associations so I can really set them up how I want?

---

### Post by ajgreeny on 2014-11-29
> **geoffmen said:**
> I have a problem with deluge opening the files with the wrong applications. On the deluge forums I was answered that deluge uses xdg-open therefore which app is chosen is out of its control.
I ALREADY HAVE setup my prefered applications in the gui control center / system settings, AND ALSO through the file manager in the files' properties dialogs. This problem happens across systems, wether it's XFCE, Gnome, MATE, cinnamon...
So where does xdg-open truly take its file associations so I can really set them up how I want?
My first caveat is that I have never used deluge, so I'm not totally sure about this, nor do I fully understand what you mean by deluge opening files with the wrong application; surely deluge is a torrent client, not an application that you use to open files.

However, my understanding is that **xdg-open** uses the application that is set by the system as the default for any file, in the same way that **exo-open** does.  It sounds as if that is not happening in your case
Have a good look through the contents of  **.local/share/applications/mimeapps.list** to see if that gives you any clues.

---

### Post by mc4man on 2014-11-29
likely you are looking for an entry in .local/share/applications/mimeapps.list for application/x-bittorrent= in the [Default Applications] section.
If there isn't an entry then you haven't actually changed it, ie. - 
right click on a .torrent > Properties > Open with  > select Deluge, click on "Set as Default"

---


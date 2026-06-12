---
title: "reset MIME file assocations"
date: 2008-05-11
forum: Desktop Environments
---

### Post by Melodic_BM on 2008-05-11
Hi there,
I've got some problems with GNOME mimetypes. Since my last distribution
upgrade (I upgraded Ubuntu Gutsy to Ubuntu Hardy [Beta, now using stable]), almost all file associations are broken. For example, JPGs are opened in Firefox, PDFs aren't opened anymore etc. I had hoped that it would be possible to reset the file-associations but I found no way to do this. What I tried myself is:

 * deleting >/usr/share/mime/*< (on Ubuntu) and >~/.local/share/mime/*< and then upgrading the mime database;
 * reconfiguring shared-mimetype-info with dpkg-reconfigure
 * removing gnome-mime-database with deleting all configuration files and then reinstalling it.

(After each step I restarted my machine)

None of these steps changed anything. I'm using Nautilus as file browser  and for managing my desktop icons.
So my question is: Is there a way to reset _all_ application - file associations?

This thing's drivin' me crazy, I cannot even open a txt-file (because nautilus wants to open it in GIMP -.-)
(And, yes, I could set all those associations myself, but p.e. "Eye of Gnome" is not listed in the list where I can choose with which application to open the mime type)

Thanks, regards,
    MBM

---

### Post by Tomatz on 2008-05-11
I had this problem before.

The file you need to delete is in your home directory. You need to delete it then logout/in.

I cant remember the location of it though :(

I will try to find it.

---

### Post by Melodic_BM on 2008-05-12
Thank you.
Yesterday someone told me to delete and copy from a hardy iso the /etc/mailcap file but it didn't change anything.
Cheers

---

### Post by Melodic_BM on 2008-05-15
*push*

---

### Post by nathangreen on 2009-01-08
*bump*

My problem is for only one association - .desktop files.  I don't know how it happened, but a new MIME type got created and I can't launch .desktop files anymore.  I deleted ~/.local/share/applications/x-extension-desktop.xml and it's still broken.  What's more, that type still appears in assogiate, which refuses to delete it.  I'm running 8.04 and I can't upgrade to 8.10.

---

### Post by dougalf on 2009-06-08
I had a similar problem: after an upgrade all my files would open in 'text editor'. Plus all icons would render as a text file but with the attempt to print the contents appearing down and to the right.

I tried the various guide on the web to remove directories from my home dir and looking at system mime files but nothing worked. In the end I thought I'd try a different file system explorer application and did
```
sudo apt-get install rox-filer
```
This obviously restored some common file that had gone wrong under Nautilus because everything was now back to normal!

---

### Post by mescobal on 2010-01-03
Same problem with Ubuntu 9.10. After playing with different window mangers and desktops, Nautilus doesn't make the association between filetype and application. Properties windows doesn't give you a default option. You can install Nautilus extensions with Synaptic and you get a limited configuration window that doesn't change de default icon. ¿Any help?
Thanks.

======================================

Update

The problem wasn't Nautilus. What happened was that PCFileMan (default file manager for LXDE) replaced Nautilus as the default file manager (when I opened Nautilus it worked fine).

---

### Post by ben2talk on 2011-05-24
This sucks - I click to open torrent files in Nautilus, they open in deluge - but when I click in my Chromium download section, it opens Nautilus.

Same with Miro - can't 'play in external player' now, just opens Nautilus.
Same with some other apps also - but not gPodder.

---

### Post by ben2talk on 2011-05-24
Nope, not here.

I can't play files from Miro - when I click 'play' they simply open with Nautilus.

Everything opens in Nautilus for me now - jpg/torrent/pdf files downloaded with Chrome or Firefox, all the same.

Everything opens fine from Nautilus though...

---


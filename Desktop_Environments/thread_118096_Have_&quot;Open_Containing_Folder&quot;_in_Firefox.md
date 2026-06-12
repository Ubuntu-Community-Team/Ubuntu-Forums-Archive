---
title: "Have &quot;Open Containing Folder&quot; in Firefox open Konqueror"
date: 2006-01-16
forum: Desktop Environments
---

### Post by NeoChaosX on 2006-01-16
Okay, I've been using Firefox in KDE for awhile, and there's one thing that bugs me - I can't for the life of me, get the "Open Containing Folder" feature in Firefox's download manager to use Konqeuror instead of the apparent default, Nautilus. I'm using Firefox 1.5 and it seems to not work with previous hacks to do what I'm asking (for instance, having /usr/bin/nautilus point to /usr/bin/konqueror). Have any Firefox users in Kubuntu been able to do this, and can you explain how?

---

### Post by NeoChaosX on 2007-01-20
Bump. I'm sitll going through this problem in Firefox 2.0 with Kubuntu; anybody at all managed to do this?

---

### Post by oobuntoo on 2007-01-20
Back when I was using Dapper, I'd managed to get it to work. I haven't tried it on Edgy.
It's such a small inconvenience that it's not worth the effort. OK, I don't want to contaminate my Kubuntu with too much Gnome stuff!

I don't remember exact steps I had to do, but it involved installing firefox/mozilla-gnome support packages, gconf, gnome-settings, and whatever dependecy packages are needed. Basically, you have to use a script to get gnome-settings and gconf to run at the start of KDE, then through gconf, change any instances  of nautilus to konqueror.

When I was using Dapper Kubuntu and XGL/compiz, I simply used the scipt for starting compiz  to start gnome-settings and gconf.

Dont blame me if you try it and it does not work :biggrin: 
It would be nice if you can try it out and report back :D

---

### Post by NeoChaosX on 2007-01-20
Actually, go figure, I've just got it to work. Here's how I did it:

1) Open up */usr/share/applications/kde/kfmclient_dir.desktop* in Kate (or other text editor of choice). I then modified the mimetype line from this
```
MimeType=inode/directory
```
to look like this:
```
MimeType=inode/directory;x-directory/gnome-default-handler
```

The mimetype **x-directory/gnome-default-handler** is key here, since Firefox uses programs affiliated with this type to open a file manager. However, we have to update the system so it recognizes Konqueror as a program that can open that mimetype. For me, the way to get this done was to...

2) Install Nautilus. All it took was a simple 
```
sudo aptitude install nautilus
```
to get it installed. Installing Nautlius updated the MIME types so Firefox was aware that Konqueror was one program that could open the g-d-h mimetype. However, Firefox will open Nautilus first when calling for a download folder, so I removed it and all dependencies after that.

With Nautilus removed, Konqueror remained as the only program registered to open the gnome-default-handler mimetype. Now, Firefox is successfully opening Konqueror when asked to open the folder of where a download is located. :biggrin:

Special thanks goes to [this thread](http://www.kde-forum.org/artikel/12531/firefox--kde-open-with-menu-does-not-work-properly.html) on KDE-Forum.org that pointed me in the right direction to fixing this problem.

---

### Post by Tony G on 2008-04-07
[http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux](http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux)

---

### Post by DannyW on 2008-05-01
> **Tony G said:**
> [http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux](http://rubylution.ping.de/articles/2007/09/11/open-containing-folder-in-firefox-under-linux)

Worked a treat. Thanks

---


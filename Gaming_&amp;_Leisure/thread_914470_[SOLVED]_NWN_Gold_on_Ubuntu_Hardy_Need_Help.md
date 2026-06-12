---
title: "[SOLVED] NWN Gold on Ubuntu Hardy: Need Help"
date: 2008-09-08
forum: Gaming &amp; Leisure
---

### Post by TheThinker on 2008-09-08
Hi everyone. I followed TO THE LETTER all of Bioware's instructions for installing Neverwinter Nights Gold Edition. I even installed the 1.6 linux patch manually, and ran the fixinstall shell after everything was done. Fixinstall seemed to work fine, but when I use the dmclient shell or the nwn shell, the only thing that happens is a black screen for a fraction of a second, then my desktop appears again. Nothing! I've worked for 3 hours trying to get this to work, and I'm getting frustrated. I even used Ravage's installer to no avail.

My cdrom is mounted as /media/cdrom0; does this matter? I would appreciate any help anyone can give me. Thanks a lot.

Mind you, I'm using Ubuntu Hardy 8.04

---

### Post by Perfect Storm on 2008-09-08
Guide: [http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

But you properly need to change the nwn file line 10 (which are described in the guide).

---

### Post by TheThinker on 2008-09-08
Thanks A.I, but the instructions ask for the 1.2 gigabyte nwresources129 tar package (yikes!). Is this the only way? I already tried the installation instructions for NWN Gold here: [http://nwn.bioware.com/downloads/linuxclient.html#nwngoldinstall](http://nwn.bioware.com/downloads/linuxclient.html#nwngoldinstall). Are those Gold Edition CD's worthless now?

Not that I can't download 1.2 gigs in under an hour, but I don't like pushing the bandwidth as we have a shared cable connection where I live.

---

### Post by Perfect Storm on 2008-09-09
There's another thread on how to install gold/diamond edition without download on this forum - you might want to search for it if you don't want to download. 
The reason I wrote this one is if everything else fails.

---

### Post by TheThinker on 2008-09-09
HEY! I found this thread: [http://ubuntuforums.org/showthread.php?t=666726](http://ubuntuforums.org/showthread.php?t=666726)

It turns out that the LibSDL (the one that appears to be a link) in the lib folder of the nwn directory was the culprit. I removed it and voila: NWN in all its glory.

Funny. You'd think that this little problem woudld had been fixed by Bioware by now, as the file was included in the linux client. It's such a simple bug.

Thanks for the help, nonetheless.

---


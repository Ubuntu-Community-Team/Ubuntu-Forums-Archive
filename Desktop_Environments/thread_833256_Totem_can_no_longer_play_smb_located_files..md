---
title: "Totem can no longer play smb:// located files."
date: 2008-06-18
forum: Desktop Environments
---

### Post by SarahKH on 2008-06-18
A very odd problem is occurring in 8.04 after the last round of updates.
Most of my media is stored on a server, which presents samba shares (and NFS for MythTV frontends). 

So quite often I'm sat happily playing back (as an example) smb://madcat/media/Television/NCIS/Season 1/1x01.avi  using gvfs to mount it and browse.  All has been good until yesterday.  

Now Totem responds "An error occurred Could not read from resource".  Irksome.  Mplayer has no such problems but appears to go via /home/<username>/.gvfs/<etc>/1x01.avi 

Madcat hasn't had any software updates.
The Wireless network is stable.
The laptop has however updated itself with the usual fixes and such which is when the problem started happening. 

Rebooting doesn't fix it, nor does logging in as another user.

Now if this is an issue with the new gvfs (which seems twitchy) or Totem I couldn't tell you, but I'd like to know what's changed and how to undo it because TBQFH it's very annoying.

---

### Post by Jungies on 2008-06-28
I have the same problem. There are some files in a directory I can open in Totem over Samba, and some I can't. It's not a permissions problem, as the same file opens fine in VLC. It's not a codec problem, as if I copy it locally it opens fine. My Windows laptop can open the files over Samba, as can my XBox running XBMC.

It's pretty annoying.

---

### Post by SarahKH on 2008-06-28
Oddly enough, checking Madcat's samba logs I'm seeing "Connection reset by peer" appearing when Totem is trying to playback .avi's. 

MKV's work fine, it's just AVI files as far as I can tell (regardless of the actual video inside the container).  Curiously playing the AVI files over NFS is a-ok, it's just gvfs mounted samba stuff. 

I'm wondering if ripping out all the gstreamer plugins and reinstalling them might work.

---

### Post by Jungies on 2008-07-02
Looks like it's been fixed:
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/241448](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/241448)

...and seems to be working for me.

---


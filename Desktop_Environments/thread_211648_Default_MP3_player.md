---
title: "Default MP3 player"
date: 2006-07-08
forum: Desktop Environments
---

### Post by AZzKikR on 2006-07-08
I've been trying my *** off to change the default mp3 player to rhythmbox. I changed the /usr/share/applicatons/defaults.list to use the rhythmbox.desktop entry. After a Gnome restart, it still fired up Totem. 

The Right-Click on an MP3 and then selecting 'rhythmbox', did start up the Rhythmbox player, but nothing was played, and the entry is not saved. 

-- 

It seems that when the music resides on a Samba share (my ubuntu server machine), it uses Totem as its default player. When an mp3 resides on my own desktop harddrive, it open up in RhythmBox just fine. What on earth is going on here?

---

### Post by AZzKikR on 2006-07-10
Well, it doesn't matter anymore really. When I mount the Samba share using an entry in /etc/fstab it will open up Rhythmbox just fine. Problem solved.

---


---
title: "VLC, Mplayer, gxine Not Playing SMB shared Media"
date: 2006-06-06
forum: Desktop Environments
---

### Post by gotmonkey on 2006-06-06
Something just does not seem right. 

I just did a clean install of 6.06 on my system. I set up network sharing between ubuntu and my XP system. Installed samba and configured workgroup. I have no problem accessing the smb shares or playing the media files across the network in totem-xine. 

I installed gxine, mplayer, and vlc for players as well. I can play media files that are locally stored on the ubuntu system, but I can't play files directly from the smb shares. 

Any thoughts?



system spec's
AMD XP3200 
1 gig PC3200
Nvidia 6600GT AGP 128meg
200gig WDC
Samsung Optical

---

### Post by Jason_25 on 2006-06-06
Totem can do it though, becuase of it's integration with nautilus.  You can always manually mount those smb shares and play it with anything.

```

sudo mount -t smb //server/nameofshare /media/mountpoint

```

---

### Post by gotmonkey on 2006-06-07
[QUOTE=Jason_25]Totem can do it though, becuase of it's integration with nautilus.  You can always manually mount those smb shares and play it with anything.

```

sudo mount -t smb //server/nameofshare /media/mountpoint

```[/QUOTE]

I tried doing the mount. It came back with unknown filesystem type "smb"

??

---

### Post by Jason_25 on 2006-06-07
Sorry, your bound to post a mistake eventually.  Try *smbfs*

---


---
title: "usb mp3 player problem"
date: 2006-01-12
forum: General Help
---

### Post by ohzopants on 2006-01-12
I have a weird problem with my creative mp3 player: whenever I erase what's on it and put new music on it the old music is still there.  When I listen to some songs they will cut out half way through and start playing something I had erased.  This does not happen to all the songs, and all the new song information is there (title, artist, folders, duration) but somehow the old songs are still there.

How do I fix this, having to reboot into windows just to do this is really annoying (by now this is the only thing I use windows for)?

thanks

---

### Post by lapsey on 2006-01-12
[QUOTE=ohzopants]I have a weird problem with my creative mp3 player: whenever I erase what's on it and put new music on it the old music is still there.  When I listen to some songs they will cut out half way through and start playing something I had erased.  This does not happen to all the songs, and all the new song information is there (title, artist, folders, duration) but somehow the old songs are still there.

How do I fix this, having to reboot into windows just to do this is really annoying (by now this is the only thing I use windows for)?

thanks[/QUOTE]

did you delete them fully or did you send them to the wastebasket.

I made just that mistake until i realised i could go to system > preferences > file management > behaviour > wastebsket and 'include delete command that bypasses the wastebasket'.

hope this helps.

---

### Post by Zhukov on 2006-04-28
Dunno if it worked for you but it didn't worked for me.
I found out Ubuntu isnt mounting the player as it should. It should be mounter with async, but that way copying files is impossible.
You can easily solve it by issuing sudo umount /dev/sd(a/b)1 and wait for the command to complete.

---


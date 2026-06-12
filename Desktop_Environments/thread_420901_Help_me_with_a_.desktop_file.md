---
title: "Help me with a .desktop file"
date: 2007-04-24
forum: Desktop Environments
---

### Post by json684 on 2007-04-24
So this is what I have in my ~/.kde/share/apps/konqueror/servicemenus/

playInMplayer.desktop
```
[Desktop Entry]
ServiceTypes=video/*
Actions=playInMplayer

[Desktop Action playInMplayer]
Name=Play In Mplayer
Icon=mplayer
Exec=mplayer %u
```

The idea is to play a smb:// file from a networked computer. The problem is that the url passed is 
```
smb://user@server/file
``` from konqueror when browsing the samba share. What i need to pass is the username and password. Which means I need to send ```
smb://user:PASSWD@server/file
```

Is there a way to modify the %u that is in the exec line? I tried using the -passwd option for mplayer but it doesn't work. The password has to be part of the passed url. If there is a way to have the entry access my kde wallet that could work too. Thanks for any help I can get.

---


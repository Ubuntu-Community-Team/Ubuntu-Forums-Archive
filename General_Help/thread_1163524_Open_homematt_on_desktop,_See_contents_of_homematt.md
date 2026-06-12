---
title: "Open /home/matt on desktop, See contents of /home/matt on server"
date: 2009-05-18
forum: General Help
---

### Post by mattalexx on 2009-05-18
Environment:
Ubuntu Jaunty desktop
Ubuntu Hardy server (samba)

I keep all of my files on the server. Is there anyway to symlink /home/matt on the server to /home/matt on the desktop? When I open /home/matt my desktop, I'd like to see the contents of /home/matt on the server. 

Possible? Ridiculous? Is there a better way?

---

### Post by CatKiller on 2009-05-19
You could probably mount your server files to your local /home using NFS, but I've never done it so I don't know how sensible it is.

---

### Post by geirha on 2009-05-19
I second using NFS. There's a guide here [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---


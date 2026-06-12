---
title: "Playing music from smb shares"
date: 2005-11-13
forum: Desktop Environments
---

### Post by BRODEL on 2005-11-13
I installed beep media player and I wanted to play some songs off of the windows share I have setup. I connected to the windows share fine, but when I went to play them it downloaded them to a temporary folder (I assume) and then played it. Is there anyway I can just get it to play from the share? 

I am using beep media player if that matters.

---

### Post by daller on 2005-11-15
Open it from the mounted directory, instead of the virtual path!

I'm not using smb-shares myself, but I'll compare it with an external harddisk, to make my point!

Opening files for amarok from "media:/sda1" make the files copy to temp!

Opening files from "/media/sda1" works without that bug, it seems!

---

### Post by komputes on 2008-02-18
I'm using VLC, and it does'nt play music off smb:// shares. Any ideas why?

---


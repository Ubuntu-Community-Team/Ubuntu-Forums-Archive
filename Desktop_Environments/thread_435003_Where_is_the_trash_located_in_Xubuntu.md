---
title: "Where is the trash located in Xubuntu?"
date: 2007-05-06
forum: Desktop Environments
---

### Post by musclesprout on 2007-05-06
So here is the situation, I am currently using Xubuntu 7.04. I plugged in my PSP for the first time, and deleted some files. I'm sure this was somehow my fault (improperly unmounting the PSP or something), but now, not only is the space not freed up on my PSP, but the items in the trash are "Read Only" and undeletable. To correct undeletable files in the past, I've simply gone to ~/.Trash in the terminal, and chmod 777'd the files, and deleted them. I can not, however, find the trash, via the terminal, in Xubuntu. So can anyone point me in the right direction? And while I'm asking, anyone else use a PSP with Xubuntu? I assumed it worked like any other removable drive.

---

### Post by afoglia on 2007-05-06
Check ~/.local/share/Trash.  In there are two folders, files, and info.  Files has the files, info has the original location and deletion date.  I believe this is the freedesktop.org standard.

---


---
title: "Change where Ubuntu /home/user folders point to"
date: 2009-04-26
forum: General Help
---

### Post by werdna5225 on 2009-04-26
I have a dual boot system, and I would like for my /home/user/music, video, and pictures folders to point to the users folder in windows that houses the same media type.  Does anyone know how to do this?

---

### Post by mcduck on 2009-04-26
The easiest way is to make sure the Windows drive is automatically mounted at boot (as in configured in /etc/fstab) and then just symlink those directories from Windows drive into your home.

---

### Post by sekinto on 2009-04-26
Mount Windows partition somewhere. In Nautilus (file manager) open up two tabs (press ctrl-t to open up a second tab), in the first one browse to your home directory, then browse to the folder containing your Windows directories in the second tab and "middle-click drag" the ones you want to the first tab and when it asks you if you want to link, move or copy choose link. Then just rename the links to whatever you want.

---


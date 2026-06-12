---
title: "does anyone understand this er."
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by alexlex on 2007-05-13
i am trying to run wolf-et and not only do i have no sound but it shuts down and i get this err.

Sys_Error: recursive error 'Sys_LoadDll(ui) failed, no corresponding .so file found in fs_homepath or fs_basepath
' after: CL_ParseServerMessage: Illegible server message 0


does anyone know what it means?

---

### Post by B. Gates on 2007-05-13
Well, for the issue of having no sound, you can try running the following two commands in a terminal:

sudo chmod 777 /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

As for your Sys_Error, dunno sorry.

---

### Post by n1ppon on 2007-10-28
I just experienced the same Sys_error ... If you came up with a solution please post it here.

---

### Post by msinkm on 2008-01-12
Just solved it.  Check out this link:

[http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=950](http://www.linux-gamers.net/modules/newbb/viewtopic.php?topic_id=950)

Hopefully that will do it.

---

### Post by nikoPSK on 2008-01-12
EDIT: whoopsey, thought you were the thread creator. hehe

---


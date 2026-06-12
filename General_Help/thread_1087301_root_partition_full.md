---
title: "root partition full"
date: 2009-03-04
forum: General Help
---

### Post by xjgnsdof on 2009-03-04
My root partition is about 10GB. Recently, I noticed that I only have 2.1MB free.

I have emptied my Trash (as user), run "sudo apt-get autoclean," and "sudo apt-get autoremove." I still have almost no free space left in my root partition.

If this matters, I recently canceled some large file transfers to and from my /home partition. I also can't empty the trash as root because Nautilus tells me this: Sorry, could not display all the contents of "trash": Operation not supported

---

### Post by Slim Odds on 2009-03-04
You could reduce the reserved space with tune2fs (the -m option).

---

### Post by xjgnsdof on 2009-03-04
I know what's eating all the space in my root partition: some backups that I haven't removed.

I have navigated to it (/root/.local/share/Trash) and deleted everything there. I have freed up a lot of space now.

---

### Post by sujoy on 2009-03-04
cant remove as in? what errors are you getting?

try::

sudo rm -rf /root/.local/share/Trash/*

WARNING: this will delete all files and folders in the Trash directory and its subdirectoy

---

### Post by xjgnsdof on 2009-03-04
> **sujoy said:**
> cant remove as in? what errors are you getting?

try::

sudo rm -rf /root/.local/share/Trash/*

WARNING: this will delete all files and folders in the Trash directory and its subdirectoy

I was hasty to post. I just figured it out, but I will keep your instructions in mind.

---


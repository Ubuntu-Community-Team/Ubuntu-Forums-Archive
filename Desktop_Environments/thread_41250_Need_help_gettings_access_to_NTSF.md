---
title: "Need help gettings access to NTSF"
date: 2005-06-12
forum: Desktop Environments
---

### Post by NakedGreekStatue on 2005-06-12
I used Synaptic to install "libntfs-gnomevfs" which says in the description that I will be able to "allow GNOME VFS clients to seamlessly use the NTFS library". I also installed "ntfsprogs" and "libntfs-5". I dual boot my comp with windows XP and I have a lot of files that I would like to bring over to Ubuntu. I have no idea how to get to the NTFS system through gnome or otherwise. Any help?

---

### Post by aussiedini on 2005-06-12
the easiest way is open a terminal, then type sudo mkdir /windows(you pick the name you want), then sudo mount /dev/hd* (whatever your XP is on) -t ntfs /windows(again hwatever you named the folder). You should be able to open the folder and see your Xp installation. If you want to make it a permenat thing you need to amend your fstab file.

---

### Post by NakedGreekStatue on 2005-06-12
can you tell me what to do with the fstab file? I do want to make it permanent.

---

### Post by NakedGreekStatue on 2005-06-12
Also, how do I find what number my NTFS partition is?

---

### Post by TeeJay on 2005-06-12
[QUOTE=NakedGreekStatue]can you tell me what to do with the fstab file? I do want to make it permanent.[/QUOTE]

Add the following lines at the end of the file 

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

This is mine, but you should get an idea what yours should be like.

Also go here [ http://ubuntuguide.org/](http://ubuntuguide.org/) to see other ways of mounting NTFS filesystems.

---

### Post by NakedGreekStatue on 2005-06-12
[QUOTE=TeeJay]Add the following lines at the end of the file 

/dev/hda1       /media/windows  ntfs    umask=0222      0       0

This is mine, but you should get an idea what yours should be like.

Also go here [ http://ubuntuguide.org/](http://ubuntuguide.org/) to see other ways of mounting NTFS filesystems.[/QUOTE]
 WIth the guide I got it working, thanks. :)

---


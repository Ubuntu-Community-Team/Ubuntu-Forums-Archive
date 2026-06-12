---
title: "Gnome Do won't follow symlinks"
date: 2010-02-16
forum: Desktop Environments
---

### Post by jpangamarca on 2010-02-16
Hi, I have a problem with Gnome Do. I have a NTFS partition mounted on /media/varios. I made a symlink on my home directory called Docs (/home/juanpablo/Docs), which points to /media/varios. I have music and some docs on that partition. I have the Locate files plugin enabled on Gnome Do, it searches for files on the root partition (/) and my home dir correctly, but it won't list the files on that NTFS partition. I used the symlink trick for the Music folder and Amarok has no problem reading the files and building the media library, but it isn't the case with Do. What should I do to get Gnome Do list the files on that folder (/media/varios)? Isn't the symlink enough?

---

### Post by Dangger on 2010-05-15
This might solve the issue for you. Go into Gnome-do:

 preferences>plugins

check the box for 'Files and Folders' then click in configure and add the folder to the list of indexed folders.

---

### Post by atulkakrana on 2010-06-06
Thanks for the tip DANGGER.

That seem to solve the problem. I believe a restart is required after this.

---


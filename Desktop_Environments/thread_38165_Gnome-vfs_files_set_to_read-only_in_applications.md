---
title: "Gnome-vfs: files set to read-only in applications"
date: 2005-05-30
forum: Desktop Environments
---

### Post by Zandor on 2005-05-30
Hi

Is it normal that I can't save any files in applications that I opened in a gnome-vfs session? Opening them is no problem, but they are all set to read-only. Tried it with ftp and ssh connections. However, I can save them in nautilus (drag & drop).

Thanks!

---

### Post by lorap on 2005-05-30
hi friend!
you can change the attributes this way:
sudo chmod 755 /path_to_the_folder_you_need -R

-R means all subdirectories also
have a nice day.
pavel

---

### Post by lorap on 2005-05-30
go to this link to read more but remember:

4 means read
2 mean write
1 means execute
first digit in 751 is 7 for owner and says "read+write+execute"(4+2+1), second digit is 5 for group and says "read+execute"(4+1), third digit is 1 for "execute" for guests.

this's more dipper explanation:

[http://unix.cms.gre.ac.uk/general/chmod.html](http://unix.cms.gre.ac.uk/general/chmod.html)

---

### Post by Zandor on 2005-05-30
Thanks for the answer...
but there's no problem with the local permissions. It's that I can't save opened files to a remote server directly in the application (gedit, bluefish... every application that supports remote gnome-vfs connections in the open/save dialog).

---


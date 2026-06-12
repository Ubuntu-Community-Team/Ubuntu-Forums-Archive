---
title: "fstab?"
date: 2009-04-07
forum: General Help
---

### Post by Freddy on 2009-04-07
Where can I find /etc/fstab? I can't find it within /etc where it should be.

/Thanks.

---

### Post by coffeecat on 2009-04-07
It has to be in /etc otherwise your system wouldn't boot up.

Are you trying to find it in Nautilus (the Gnome/Ubuntu file manager)? Try scrolling down below all the many folders that are also in /etc. The files are all in alphabetical order below the folders.

---

### Post by neu2buntu on 2009-04-07
it may also be hidden by default > in nautilus click on > view > show hidden folders . or open it from the command line with ```
gedit /etc/fstab
``` or ```
sudo gedit /etc/fstab
``` if you need to make permanent changes to it (make sure to hit >save)

---

### Post by sofasurfer on 2009-04-07
I bet your looking for it as a directory.
It is a file, located after the directories in the /etc folder.

---

### Post by coffeecat on 2009-04-07
> **neu2buntu said:**
> it may also be hidden by default > in nautilus click on > view > show hidden folders . or open it from the command line with ```
gedit /etc/fstab
``` or ```
sudo gedit /etc/fstab
``` if you need to make permanent changes to it (make sure to hit >save)

Couple of points. Hidden files/folders always commence with a dot which /etc/fstab does not, so I don't think showing hidden folders will help.

Second: you can get away with using sudo for opening gedit, but it's safer to use gksudo. Have a look here, (about halfway down, but it's worth reading it all):

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by neu2buntu on 2009-04-07
thanks Coffeecat !!! i have tried to be the teacher here,when im really just the pupil,...lol..   i think i have been overusing "sudo" when "gksudo" would be more appropriate...cheers

---

### Post by Freddy on 2009-04-07
Thanks, I found it, guess I'm tired I just searched the folders and didn't scroll down to the plain .conf files :).

---


---
title: "&quot;sudo -i&quot; causes problems"
date: 2005-08-25
forum: Desktop Environments
---

### Post by ^NoX on 2005-08-25
i wrote "sudo -i" in order to run a root terminal (as said in "ubuntulinux wiki") and now i cant login to my account. it says permission denied.
in /etc/passwd i found out that /home/username is still my home dir, so this is not the problem.
even though /home/username is owned by me, and there are read permissions, i cant read from it.
i dont know what this command did to my ubuntu.
what to do? i cant login as root either...  :-?

---

### Post by smack on 2005-08-25
Running 'sudo -i' just gets you a root terminal. 'man sudo' for more information on this. You can't log in as root because there's no root account enabled. You get root level privledges through sudo.

Hmm.. is your caps lock on or something? What all did you do after you ran 'sudo -i'.

---

### Post by ^NoX on 2005-08-25
just copied some files from my FAT32 partition in order to delete it.
i didnt changed anything.
suddenly x-chat started to give me "permission denied - unable to write to ~/.xchat2/logs" and i couldnt open the terminal, so i thought to reboot and run as root and fix these problems.
here is the exact error:

"your session only lasted less than 10 seconds. if you have not logged out yourself, this could mean that there is some installtion problem or that you may be out of diskspace. Try logging with one of the failsafe sessions to see if you can fix this problem.

and than when i click "show details" it gives me the following 2 lines:

"(gnome-session:7717):libgnomevfs-WARNING **:Unable to create ~/.gnome dir : permission denied

"Could not create per-user gnome conf dir `/home/ofer/.gnome` : permission denied


even thru Recovery Mode in grub, i cant read from my own /home/user. only when im root.
already did "chown -R user:user /home/user" and "chmod -R 666 /home/user"
i have already make sure that /home/user is in /etc/passwd in the correct place.
the partition is mounted as regular, and i dont think that there is any chance that it has been unmounted when i worked on it, linux would have crash...
my disk space is atleast 150GB free.. so its not the problem

---


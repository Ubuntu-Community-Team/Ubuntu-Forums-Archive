---
title: "permissions problem???"
date: 2006-06-18
forum: Desktop Environments
---

### Post by pellgarlic on 2006-06-18
i seem to be having a few problems, that lead me to believe there is an issue with the permissions of certain areas of my dapper installation:

- when i make any changes using alacarte, they fail to apply. (if i add/remove any items to/from a menu, the change does not happen. if i try to change an icon, it does not work).

- when i try to "open with other application", and choose an app that has not been used before for that file type, i get an "application could not be added to the application database" error.

- when the automatic file system check runs after the 20 boots without check having been performed, i have noticed the message "file system seems to be mounted read-only"

could my use of a reiserfs partition for "/" be the cause of the problem?

my setup:

hda:
hda1: 50 mb ext3 /boot partition
hda2: 15 gb reiserfs / partition
hda3: 15 gb reiserfs /void partitoin (for installing other distros to try out)
hda4: 40 gb JFS /movies

hdb:
hdb1: 2 gb swap partition
hdb2: 100 gb ext3 /home partition
hdb3: 50 gb JFS /music partition
hdb4: 40 gb vfat /backup partition

how do i go about checking the permissions of "/ "?
or do i only need to check the permissions of certain directories? (such as /etc, /var, /sbin or such like). if so, which directories, and what should the permissions be?

or is this nothing to do with permissions?

---

### Post by Ramses de Norre on 2006-06-18
Things like your menu and applications databases seem like they should be in your home folder, so maybe in there the permissions are messed up.
Try a ```
sudo chown -R username ~ && sudo chmod -R u +rwx ~
```

---

### Post by pellgarlic on 2006-06-18
[QUOTE=Ramses de Norre]Things like your menu and applications databases seem like they should be in your home folder, so maybe in there the permissions are messed up.
Try a ```
sudo chown -R username ~ && sudo chmod -R u +rwx ~
```[/QUOTE]

thank you ramses! :) although i didn't follow your suggestion exactly, you certainly provided me with the answer i needed -

i understood what the command you suggested would do, and i was reluctant to change the permissions for *all* the directories and files in /home, as i believe some of them will be restricted with good reason, and will usually be circumventable by appropriate use of "sudo", if needed.

so, i looked in /home for any files or directories that were not "owned" by me. one stuck out - a directory called ".local". the icon was a red square with a cross in it, and when i tried to open it, i got a message saying i didn't have permission. so i did a "sudo nautilus", and had a look inside. although the contents were sparse, they seemed like they might be relevant to my problem, so i took your suggestion, but modified it to only apply to the ".local" directory:

```
sudo chown -R pell /home/pell/.local && sudo chmod -R u+rwx /home/pell/.local
```

(p.s. - the command would not work until i removed the space between the "u" and "+rwx")

i tried doing the "open with other application", and it worked. making changes in alacarte still did not work, so i logged out and back in (to restart gnome) and then it worked! i don't know how the permissions for that directory got messed, but i'm glad someone was able to provide some good advice. thanks for your help :-)

---

### Post by Ramses de Norre on 2006-06-18
Ow I guess I didn't pay enough attention.. the second sudo wasn't necessary neither. 
But the command only sets you as owner of your whole home dir and gives you (and only you) all permissions, the permissions for group and others aren't changed.

---


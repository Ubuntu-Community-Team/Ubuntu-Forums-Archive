---
title: "Sharing a common file between drives"
date: 2009-04-22
forum: General Help
---

### Post by texas.chef94 on 2009-04-22
1. two debian based OS, with one residing on sda and other sdb external.
2. File in question titled STUFF on both OS
3. What must I do to be able to write to either folder from a given OS

Thanks

---

### Post by scheuri on 2009-04-22
Hi there

Both OS need to recognize the partition of the other OS and mount it.
If that is done the ownership and rights of the respective folder must be correct. That means that your user is actually allowed to read and write to that folder.

If I understood you correctly, that should do it.

cheers
scheuri

---

### Post by texas.chef94 on 2009-04-22
> **scheuri said:**
> Hi there

Both OS need to recognize the partition of the other OS and mount it.
If that is done the ownership and rights of the respective folder must be correct. That means that your user is actually allowed to read and write to that folder.

If I understood you correctly, that should do it.

cheers
scheuri
I appreciate that and I now need some specifics if you can help an challenged old man

Thanks and regards

---

### Post by StuartN on 2009-04-22
> **texas.chef94 said:**
> I appreciate that and I now need some specifics if you can help an challenged old man

If both partitions are mounted and you can see both files (in Nautilus or the command ls) then I assume only one (let's say in dir1) belongs to your username. You could either take ownership of the other file (dir2):

  sudo chown myuser:mygroup dir2/STUFF

or change permissions on your own file:

  chown +w:ga dir1/STUFF

The first command will take ownership away from your other username, so you will not be able to write when logged into your other OS. The second grants write acces to other members of your group and to all users.

An alternative method is to create a symbolic link in one partition, so that there is only one actual STUFF file:

  ln -s dir2/STUFF
  sudo chmod +w:ga STUFF

STUFF must not exist in dir1 and ln creates a pathname link to STUFF in dir2, then chmod makes it writable to all. Now whichever STUFF is edited will be reflected in both partitions because one contains the file and the other contains a symbolic link to it.

(I guess in Nautilus you can do the same with some right-clicking to create a launcher and to change permissions).

---

### Post by texas.chef94 on 2009-04-22
Stuart N I thank you for a most informative specific reply with options

Allen

---

### Post by texas.chef94 on 2009-04-22
Why should it be easy :P Obviously I probably need to edit a file and believe it or not never done that.
Anyway as terminal report shows 1st command no problem. and I tried chomd and way over my head.
Sorry for comprehension challenges
Allen

allen@allen-desktop:~$ ln -s dir2/STUFF
allen@allen-desktop:~$ sudo chmod +w:ga STUFF
chmod: invalid mode: `+w:ga'
Try `chmod --help' for more information.
allen@allen-desktop:~$

---

### Post by StuartN on 2009-04-22
Sorry, my mistake. The correct line is:

chmod ga+w dir1/STUFF

Chmod takes ugoa (user, group, others, all) followed by +- or = and then the permissions rwx to add, remove or set.

---

### Post by texas.chef94 on 2009-04-22
One more time
allen@allen-desktop:~$ ln -s dir2/STUFF
ln: creating symbolic link `./STUFF': File exists
allen@allen-desktop:~$ chmod ga+w dir1/STUFF
chmod: cannot access `dir1/STUFF': No such file or directory
allen@allen-desktop:~$ 
Allen

---

### Post by MN Noob on 2009-04-22
> **texas.chef94 said:**
> One more time
allen@allen-desktop:~$ ln -s dir2/STUFF
ln: creating symbolic link `./STUFF': File exists
allen@allen-desktop:~$ chmod ga+w dir1/STUFF
chmod: cannot access `dir1/STUFF': No such file or directory
allen@allen-desktop:~$ 
Allen

Probably need to do sudo chmod...

---

### Post by StuartN on 2009-04-22
> **texas.chef94 said:**
> One more time
allen@allen-desktop:~$ ln -s dir2/STUFF
ln: creating symbolic link `./STUFF': File exists

It looks like you already have a file called STUFF in your home directory, so it isn't creating the link. Make sure there is no file in the current directory with the name of the link you are creating.

> **texas.chef94 said:**
> allen@allen-desktop:~$ chmod ga+w dir1/STUFF
chmod: cannot access `dir1/STUFF': No such file or directory

...and at this point you are in your home directory, ~/, so you are referring to a file called ~/dir1/STUFF. chmod ga+w STUFF should work if the previous command worked.

(By the way, chmod will change the permissions of the linked file and NOT the permissions of the link, so ls -l ~/ will show unchanged permission xrwxrwxrw and ls -l dir2/STUFF will show -rw-rw-rw).

---


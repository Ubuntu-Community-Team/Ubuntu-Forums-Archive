---
title: "/home to /home"
date: 2009-01-25
forum: General Help
---

### Post by Stargazer989 on 2009-01-25
I just re-installed Ubuntu Intrepid Ibex on my laptop once again but the partition i have for /home did not **become** /home. is there a way to replace /home with the /home **partition** ?

---

### Post by taurus on 2009-01-25
You mean you have a separate /home partition but forgot to mount it when you reinstalled?  

Did you use the same login name?

You can edit /etc/fstab 

```
gksudo gedit /etc/fstab
```

and include an entry for that partition, mounting it to /home.

```
**/dev/sda3**   /home   ext3   defaults   0   2
```
Replace /dev/sda3 with the right partition.

---

### Post by Stargazer989 on 2009-01-25
i think i used the same login name... pretty sure actually.

but i had a thought... wouldn't the current hidden files in /home need to be placed in the /home partition ?

---

### Post by taurus on 2009-01-25
If you don't want to keep your old settings, then you would remove all those dot files and directories.  Then, replace them with the new ones--default settings.

---

### Post by cb951303 on 2009-01-25
you should have mounted that partition as "/home" when reinstalling

---

### Post by Stargazer989 on 2009-01-25
thing is: when i originally installed ubuntu on my laptop.. EVERYTHING was screwy, so i reinstalled it. don't remember mounting /home for that. :\
probably why i didn't this time either.

but since this reminded me of something: where is the config folder for epiphany. this way i won't have to go to all the websites again and remember everything... again.

---

### Post by taurus on 2009-01-25
Shouldn't it be in ~/.epiphany?  If you are looking the one in your old /home, then you first mount it before you can access it.

---

### Post by dcstar on 2009-01-25
> **Stargazer989 said:**
> .........
but since this reminded me of something: where is the config folder for epiphany. this way i won't have to go to all the websites again and remember everything... again.

[LIST=1]
[*]Boot up off Live CD
[*]Mount hard disk
[*]Rename old /home directory in disk root filesystem to /home.old
[*]Create new /home directory
[*]Reboot into normal system
[*]Log in and copy what you want from /home.old to mounted /home folder
[/LIST]

---

### Post by cb951303 on 2009-01-25
it's in ieather ~/.epiphany pr ~/.config/Epiphany

---

### Post by Stargazer989 on 2009-01-26
@taurus  i'm seeing a whole lot more than just a one liner for stuff... do i have to add other stuff to make it a correct entry or is it really just > /dev/sda3   /home   ext3   defaults   0   2 ?

---


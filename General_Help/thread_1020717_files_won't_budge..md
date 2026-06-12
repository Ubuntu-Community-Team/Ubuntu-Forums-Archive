---
title: "files won't budge."
date: 2008-12-24
forum: General Help
---

### Post by aboud on 2008-12-24
no matter what .. 
```
sudo rm -rf 
```

remount with umask=0 or 007 or 000

some folders that vista created refused to be deleted, 
the error message: 
"operation not supported"
any one knows the option i need to add to mount to do get rid of them ?

---

### Post by Slim Odds on 2008-12-24
What type of partition is it?

What filesystem?

---

### Post by snova on 2008-12-24
> **aboud said:**
> no matter what .. 
```
sudo rm -rf 
```

remount with umask=0 or 007 or 000

some folders that vista created refused to be deleted, 
the error message: 
**"operation not supported"**
any one knows the option i need to add to mount to do get rid of them ?

It means precisely that- the driver is not capable of it.

What filesystem is it?

---

### Post by aboud on 2008-12-25
as all Vista partition it's NTFS, mounted with ntfs-3g.

what is more intersting, is i even can't delete them when i booted from herin's boot CD with NTFS MS-DOS.

---

### Post by MaxIBoy on 2008-12-25
Try the following command:
```
sudo chown -R $USERNAME:$USERNAME [the folder you want to delete]
```

Explanation:
[LIST]
[*]SUDO runs the command with root privileges.
[*]CHOWN means "change owner."
[*]-R means "recurse," in other words, "do this to every item inside every level of subfolder inside the folder I'm about to give you."
[*]$USERNAME get the name of the current user. Usually the current user is a member of a group with the same name. So if my login name was Max, it would be Max:Max. $USERNAME automatically gets replaced so you can copy the code in without modifying it.
[/LIST]


Also, keep in mind that if you're using "rm -Rf," the R must be capitalized. 




If that doesn't work, make sure the filesystem is mounted as read/write.

---

### Post by ajcham on 2008-12-25
> **MaxIBoy said:**
> 
Also, keep in mind that if you're using "rm -Rf," the R must be capitalized. 


Actually, that is not the case - upper or lower case is fine. From the **rm** manpage:
```
       -r, -R, --recursive
              remove directories and their contents recursively

```

---

### Post by MaxIBoy on 2008-12-25
Oh? I didn't know that. I stand corrected. 

Well, anyway, in most (or at least many) applications, the R has to be capitalized, so it's a good habit.

---

### Post by aboud on 2008-12-25
> **MaxIBoy said:**
> Try the following command:
```
sudo chown -R $USERNAME:$USERNAME [the folder you want to delete]
```

Explanation:
[LIST]
[*]SUDO runs the command with root privileges.
[*]CHOWN means "change owner."
[*]-R means "recurse," in other words, "do this to every item inside every level of subfolder inside the folder I'm about to give you."
[*]$USERNAME get the name of the current user. Usually the current user is a member of a group with the same name. So if my login name was Max, it would be Max:Max. $USERNAME automatically gets replaced so you can copy the code in without modifying it.
[/LIST]


Also, keep in mind that if you're using "rm -Rf," the R must be capitalized. 




If that doesn't work, make sure the filesystem is mounted as read/write.

you took your time to write all this without spend a fraction of second to look at what the problem is ? 

i mentioned as well that i remounted the partition with different options, do think i did that to mount it as write protected ?

---

### Post by MaxIBoy on 2008-12-25
I'm not saying you didn't do it right. I'm just saying that things don't always happen the way they're supposed to. You could double-check by attempting to create a file inside that partition. If you're able to do that, we can narrow the problem down.

---

### Post by aboud on 2008-12-25
:popcorn:  wanna some of this ?

---

### Post by aboud on 2008-12-28
solved . 

it seems that is not supporet by the current build in ubuntu ntfs-3g 1.2 driver but it's supported by the 1.5.. which can be found on [www.ntfs-3g.org](www.ntfs-3g.org) 

more about this : 
[http://www.ntfs-3g.org/support.html#filedelete](http://www.ntfs-3g.org/support.html#filedelete)


:lolflag:

---


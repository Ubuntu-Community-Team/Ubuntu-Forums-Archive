---
title: "external hard disk (usb) and permissions ext3"
date: 2009-05-09
forum: General Help
---

### Post by scheuri on 2009-05-09
Hi all

I have (several) external harddisk which I can plug in with USB.
Some of those harddisk were formatted with ntfs. I reformatted them with ext3.

Now I have an issue with the permissions whenever I plug those ext3 external harddisk on.

**Situation:**
I have user "scheuri" and "joe" on my system. Both use Gnome. Whenever I plug in one of my harddisk with both user the harddisk gets detected and I am going to be asked what shall be done. My main (and actually only) choice is open a file browser (nautilus or whatever) so I can browse the content.
So that is fine...

Now, when I am logged in with scheuri (or joe) neither of them can actually WRITE on the disk (and even dont read).
I completely understand that joe can not alter (and maybe not even read) content from scheuri and vice versa. That is a permission thing with ext3 and is absolutely fine and works as intendend.
HOWEVER, the "root" of the disk can NOT be written to by either user.
Only root can do that (or actually the users using sudo).

**Goal:**
The root of the harddisks are accessible and writtable for ALL User who plug in the harddisks. Of course, when scheuri writes something on the disk it belongs to scheuri and depending on the permission scheuri sets no one else can write and/or read it. The same applies to all other users.
But I really want ALL users to be able to make folders or put files on the root in the first place.

Is there anything I need to do with udev permissions or with fstab?
I am working on jaunty by the way.

Thanks a lot
cheers
scheuri

---

### Post by scheuri on 2009-05-10
really no one ever had this issue?

---

### Post by scheuri on 2009-06-16
Bump again....

---

### Post by bellial on 2010-12-06
I'm having this same issue. I want to take my external hd to work, where I also use ubuntu but don't have root password, and because of that I can't copy anything to my external hd, it says I can't create the folder in it. At home I have to open with nautilus to be able to paste in it.

---


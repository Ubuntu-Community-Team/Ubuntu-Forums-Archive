---
title: "clonezilla question...."
date: 2009-05-12
forum: General Help
---

### Post by zero7404 on 2009-05-12
i haven't seen an option when running clonezilla to be able to delete the backups i created....

i have a seperate ext3 partition on my system that i use only for clonezilla storage, and so far i have backed up my ubuntu partition 3 different times, so i have 3 different images.

i see the folders clonezilla created of my images, but i cannot delete them (in nautilus, the delete option is not available)...

is it safe to delete the individual images ? are they self containing, or are subsequent backups incremental ? there is also a lost & found folder in that partition, not sure what it's used for...

---

### Post by logos34 on 2009-05-12
no, each of the separate folders is a separate clonezilla session with complete image. (To see what I mean look inside at the size of the '*.aa' file--the actual .gz image--  they should all be roughly the same).

My clonezilla folder ('2009-05-10-20-img') also has a padlock on it, owned by root, [edit: I have to delete it from command line as root:

sudo rm -r 2009-05-10-20-img

---

### Post by zero7404 on 2009-05-12
> **logos34 said:**
> no, each of the separate folders is a separate clonezilla session with complete image. (To see what I mean look inside at the size of the '*.aa' file--the actual .gz image--  they should all be roughly the same).

My clonezilla folder ('2009-05-10-20-img') also has a padlock on it, owned by root, [edit: I have to delete it from command line as root:

sudo rm -r 2009-05-10-20-img

cool, so i can delete the file as root, i should be able to do this from the command line or starting a root nautilus session....
would you be able to tell me how i can switch to another mountpoint within terminal ?

thank you

---

### Post by logos34 on 2009-05-12
> **zero7404 said:**
> cool, so i can delete the file as root, i should be able to do this from the command line or starting a root nautilus session....
would you be able to tell me how i can switch to another mountpoint within terminal ?

yep, exactly, or

alt+F2 

gksudo nautilus

To change directories:

cd /path/to/wherever

---

### Post by zero7404 on 2009-05-13
> **logos34 said:**
> yep, exactly, or

alt+F2 

gksudo nautilus

To change directories:

cd /path/to/wherever

thanks logos...
could you pls clarify the path you wrote ?
for example, the drive is listed in nautilus as /media/disk, it does not have a title.

also when pulling up a root nautilus session, the drive is not listed.
EDIT: nevermind my last question, after first mounting the partition, then opening root nautilus shows it there....

thanks again logos...

---

### Post by logos34 on 2009-05-13
cd /media/disk

---


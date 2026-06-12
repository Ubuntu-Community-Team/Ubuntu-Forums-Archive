---
title: "Repartition and moving /home"
date: 2006-01-10
forum: General Help
---

### Post by TheForumTroll on 2006-01-10
Hello.
Linux newbie calling ubuntu support ;) 

I got myself a new hard drive that i want to use for /home. How do i move home to the new disk? (hda10 -> sda1) :confused: 

Also is there any way to resize/move system partitions in a GUI?
I got gParted but as all partitions is mounted i can't do it there. Do i have to boot up in rescue mode and use parted from there or do i have to repartition and reinstall? (Eek!)

---

### Post by docmanny on 2006-01-10
Partition sda however you like. 
Then sudo mount /dev/sda1 /newhome
copy everything from /home to /newhome
go into fstab and change the line that reads 
/dev/hda10 /home... to /dev/sda1 /home...
Then umount /home
mount -a

Maybe there's a better way, but that's worked for me in the past.

Best way to change partitions is to either boot in rescue or knoppix and move things, since nothing will be mounted then.

---

### Post by az on 2006-01-10
[QUOTE=docmanny]
go into fstab and change the line that reads 
/dev/hda10 /home... to /dev/sda1 /home...
Then umount /home
mount -a

Maybe there's a better way, but that's worked for me in the past.

Best way to change partitions is to either boot in rescue or knoppix and move things, since nothing will be mounted then.[/QUOTE]
You will be able to partition sda as you like with gparted running since it should not be mounted (you said it is new)

You do not need to repartition hda if everything is on one partition.  In that case, there will not be a /home line in your fstab.  Juts make one identical to / but name it /home and put the proper device in the column.

---

### Post by TheForumTroll on 2006-01-10
/home is on it's own partition (hda10).
If I try to copy everything from /home (as root) I get an error saying something about a "lock" file that can't be copied.

---

### Post by docmanny on 2006-01-10
Try logging in as someone else (user B)
Then sudo cp /home/userA to whatever the new directory is. That way, the files in that folder won't be in use.

---

### Post by TheForumTroll on 2006-01-10
Now why didn't I think of that :p 
Will give it a try.

Update: It worked. Thank you :)

---


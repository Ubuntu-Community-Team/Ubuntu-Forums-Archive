---
title: "yet another therad about resizing partition"
date: 2005-12-24
forum: General Help
---

### Post by ubuntu27 on 2005-12-24
Hey guys! I've look the whole existing thread I believe. but,  can't seem to find what I need.

I recently resized my Windows Partition (NTFS) and made a Free Space.
Now I want to Resize my Ubuntu Partition (ext3) so it could have more space.

[[IMG]http://img422.imageshack.us/img422/1678/probgparted8rr.png[/IMG]](http://imageshack.us)

THe thing is that gparted nor Qtparted allow me to increase my ext3 partition. It only allows me to shrink it :(

What should I do guys ?

Edit: I'm running from the Live CD ;)

---

### Post by az on 2005-12-24
You cannot grow from the beginning.  Only the end.  You can copy your partition to the beginning of the free space, delete the original copy and then grow it to fill all the space.

---

### Post by ubuntu27 on 2005-12-24
[QUOTE=azz]You cannot grow from the beginning.  Only the end.  You can copy your partition to the beginning of the free space, delete the original copy and then grow it to fill all the space.[/QUOTE]

Ok. The problem that I now have is that I cannot move my files that I have to the Free space. It tells me that I cannot have more than four primary partitions when i try to format the Free space or when I try to copy my data that is on Linux to the Free space.

[[IMG]http://img474.imageshack.us/img474/408/partitionerror5hp.png[/IMG]](http://imageshack.us)

BTY, My Free space is not formatted yet.

---

### Post by ubuntu27 on 2005-12-24
any ideas?

---

### Post by briancurtin on 2005-12-25
if you cant create more primary partitions, create an extended parition.

---

### Post by ubuntu27 on 2005-12-25
[QUOTE=briancurtin]if you cant create more primary partitions, create an extended parition.[/QUOTE]

Thank you briancurtin.

How do I do I create a extended partition?

---

### Post by zoiks on 2005-12-25
Just so you know, that first partition of around 4 GB is probably a utility/diagnostic "hidden" partition that came from your computer's vendor.  I know Dells come formatted like this, and would guess that maybe Gateways, HPs, etc, do the same thing.  If you don't care about using their little utility functions (BTW the partition usually has a stripped-down Windows 98 on it with special software for doing the diagnostics) you can safely delete it.  This might make it easier to move your ubuntu non-swap partition.

Another way is to boot from a live CD, turn your swap partition off, and then copy your linux partition to another one at the biggining, and then delete the original partition, resize the new one, and add back your swap partition.

Of course, I'm just saying you *could* do these things, not necessarily saying you should.  You could hose your data real quick if you're not careful.  You'll have to reconfigure grub, for example, if the partition numbering changes.  Anyway, just be aware that bad things happen and make backups of your data first.

---

### Post by ubuntu27 on 2005-12-25
[QUOTE=zoiks]Just so you know, that first partition of around 4 GB is probably a utility/diagnostic "hidden" partition that came from your computer's vendor.  I know Dells come formatted like this, and would guess that maybe Gateways, HPs, etc, do the same thing.  If you don't care about using their little utility functions (BTW the partition usually has a stripped-down Windows 98 on it with special software for doing the diagnostics) you can safely delete it.  This might make it easier to move your ubuntu non-swap partition.[/QUOTE]


Well, yeah. I knwo about my 4GB partition has a recovery tool :) I don't want todelete it since it saved my  life many times :D

[QUOTE=zoiks]Another way is to boot from a live CD, turn your swap partition off, and then copy your linux partition to another one at the biggining, and then delete the original partition, resize the new one, and add back your swap partition.[/QUOTE]

Well, there is a problem. I am trying to copy the data that it is in my linux partition to the free space. But it keep me telling that I cannot have more than four primary partition [I have to format the free space].


[QUOTE=zoiks]Of course, I'm just saying you *could* do these things, not necessarily saying you should.  You could hose your data real quick if you're not careful.  You'll have to reconfigure grub, for example, if the partition numbering changes.  Anyway, just be aware that bad things happen and make backups of your data first.[/QUOTE]

Yep, I did a backup of my important files. I am willing to risk :D


There ave to be a way...
So, looks like I have to create a Extended partition, how do I do that ?

---

### Post by plors on 2005-12-25
Hi,

You already have an extended partition. it's called /dev/hda4 and it contains your swap partition. Since you can only have one extended partition you cannot simply create another one. But don't worry, there's an easy solution.

-disable your swap partition (swapoff /dev/hda5)
-remove your swap and extended partitions.
-copy /dev/hda3 to the beginning of unallocated space (you can resize it while you're on it)
-when (and only THEN) that's succesfully done, you delete your 'old' /dev/hda3.
-then recreate your swappartition (in an extended partition if you like)

Don't forget to update your /etc/fstab since some partitionnumbers will/may change.

Merry Christmas btw :cool:

---

### Post by ubuntu27 on 2005-12-25
[QUOTE=plors]Hi,

You already have an extended partition. it's called /dev/hda4 and it contains your swap partition. Since you can only have one extended partition you cannot simply create another one. But don't worry, there's an easy solution.

-disable your swap partition (swapoff /dev/hda5)
-remove your swap and extended partitions.
-copy /dev/hda3 to the beginning of unallocated space (you can resize it while you're on it)
-when (and only THEN) that's succesfully done, you delete your 'old' /dev/hda3.
-then recreate your swappartition (in an extended partition if you like)

Don't forget to update your /etc/fstab since some partitionnumbers will/may change.

Merry Christmas btw :cool:[/QUOTE]

Man!!  I understand what you are saying, at least the theory.
But, I don't know how to do it :(  Could you tell me step by step how to do it? please ;)

ah. Mery Christmas everyone !! :D :KS

---

### Post by ubuntu27 on 2005-12-25
Help me~ please~
Ayudame~ por favor~
&#25163;&#20253;&#12387;&#12390;&#12367;&#12428;~

---

### Post by plors on 2005-12-25
Oh please, how hard can it be. I gave you the sequence of things already. Just read them carefully and you'll be fine.

just play a bit with gparted till you think it's fine. Changes are only applied to disk after hitting 'apply', so there's no way you'll accidentaly destroy anything.

good luck :)

---

### Post by ubuntu27 on 2005-12-25
[QUOTE=plors]Oh please, how hard can it be. I gave you the sequence of things already. Just read them carefully and you'll be fine.

just play a bit with gparted till you think it's fine. Changes are only applied to disk after hitting 'apply', so there's no way you'll accidentaly destroy anything.

good luck [/QUOTE]

Hi plors. Thank you. It was more easier than I though :D

[QUOTE=plors]
Don't forget to update your /etc/fstab since some partitionnumbers will/may change.

Merry Christmas btw :cool:[/QUOTE]

Thank you :D 

Hey, how do I update /etc/fstab ? ><
 ahhhh.. man! I need to learn more !!

---

### Post by ubuntu27 on 2005-12-25
Hey guys. 
Can you look at the image attachment, and see if everything is alright?

My partitions are in this order now:

/dev/hda1
/dev/hda2
/dev/hda4
/dev/hda3
/dev/hda5


anyway, now I will have to change/update my    /etc/fstab
I am using Ubuntu Live CD. How can I update my  /etc/fstab ?

Thank you guys&girls who helped me. I appreciate a lot !! 
muah! [Kiss]

---

### Post by ubuntu27 on 2005-12-25
ok, this is what I have in my  /etc/fstab


/dev/mapper/casper-snapshot / auto noatime 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/hda5 swap swap defaults 0 0



I don't have any idea what do I have to change... and..
 i'd open this as read only. How can I make changes? :confused: 

sorry! I'm still a newbie :(


**EDIT: ** NO, That is not my /etc/fstab .. looks like it is from the CD.

How can I acces /etc/fstab with the Live CD?

---


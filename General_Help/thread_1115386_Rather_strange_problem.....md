---
title: "Rather strange problem...."
date: 2009-04-03
forum: General Help
---

### Post by Monotoko on 2009-04-03
Hiya, i use gOS, but it is based off ubuntu, just with a few GUI changes, uses the same sources etc, so i assume the same advice would happen, and the gOS forums seem a lil dead.

Well, iv used it for about a month, no problems, repartitioned my disks about 2 weeks ago and everything was fine.....i just gone back to do a lil more finetuning with my partitioning, and this comes up (image attatched)

what is dev/sdc0?? I have checked all round my computer, nothing is plugged into any USB....so where is it getting 1.09GB from?!

My proper harddrive is still there under /dev/sda but id love to know where this 1.09GB has magically appeared from :S

---

### Post by ninjapirate89 on 2009-04-03
I think that is a cd drive. Do you have a cd in your computer?

---

### Post by Monotoko on 2009-04-03
nope, computer doesnt have a CD drive at the moment
thats what im finding strange....the only thing in there is my harddrive.

---

### Post by ninjapirate89 on 2009-04-03
Well I'm stumped then. I thought for sure thats what it was. Maybe someone who is more knowledgeable than I am can help.

---

### Post by ibuclaw on 2009-04-03
Its not sdc0, it's **scd0**.

scd devices are usually **CD-ROM** devices, but why it is showing up in gparted it a mystery, to me, at least.

Try closing the Partition Manager, removing the CD inside the CD-ROM drive, then check to see if it still exists.

[EDIT]
> **Monotoko said:**
> nope, computer doesnt have a CD drive at the moment
thats what im finding strange....the only thing in there is my harddrive.
Okies... I'll have a look around for a possible reason and solution then.

Regards
Iain

---

### Post by Monotoko on 2009-04-03
Aye sorry, typo

And there is no CD-ROM drive.....

EDIT (after seeing your edit): okay :)

---

### Post by ninjapirate89 on 2009-04-03
> **tinivole said:**
> Its not sdc0, it's **scd0**.

scd devices are usually **CD-ROM** devices, but why it is showing up in gparted it a mystery, to me, at least.

Try closing the Partition Manager, removing the CD inside the CD-ROM drive, then check to see if it still exists.

[EDIT]

Okies... I'll have a look around for a possible reason and solution then.

Regards
Iain

That is what is unusual. He (if she my apologies) said there is no CD-ROM drive.

---

### Post by ibuclaw on 2009-04-03
Could you, in the Partition Manager click onto **View -> Device Information**

And post the information display about the device, if any?

Also, open a terminal and post the output of these following commands:
```
df -h
```
```
sudo fdisk -l
```
```
cat /etc/mtab
```

Regards
Iain

---

### Post by tjwoosta on 2009-04-03
wtf??

the only times i have ever seen /dev/scd0 was when it was a disc drive

like my dvd burner drive

---


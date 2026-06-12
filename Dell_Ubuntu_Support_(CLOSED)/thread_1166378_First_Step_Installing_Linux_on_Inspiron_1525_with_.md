---
title: "First Step Installing Linux on Inspiron 1525 with Vista"
date: 2009-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sudeep.makku on 2009-05-21
Hii
I have Inspiron 1525 
 
First I m having problem in doing partion to install Linux.
My computer comes with 4 partitions 
177MB EISA 
99 GB C
10 GB Recovery
2.5 Hidden ( I suppose for Dell Media Direct)
 
Could you please tell me the step wise procedure.....
As dell Vista does not allow more than 4 partition, which one I should delete....
 
Reply me urgently

---

### Post by Hoary on 2009-05-21
Surely you don't want to delete whatever's used for C.

I don't know what "Recovery" could mean. Whatever kind of "recovery" it refers to, surely it's a "recovery" that assumes that this partition and perhaps more of the hard drive is healthy. That strikes me as an odd assumption to make when planning for a recovery.

I suggest that you use CloneZilla to back up the entire hard drive. You'll then be able to recover it from the image that CloneZilla has made. Then do away with the "Recovery" partition. 

But before doing this, wait till you get a reply from somebody who actually knows what "Recovery" is for.

---

### Post by sudeep.makku on 2009-05-21
Thank You...But I hope there would be many who have dual boot on dell inspiron 1525.....could anyone tell me what they have done.

---

### Post by mangurt on 2009-05-21
The recovery drive is the drive that has the vista image in case you have to do a complete recovery of your computer (virus or some major screw-up).  I don't know how much you want to play around with deleting partitions, you should be able to create a partition on the main C: drive and install from there.  Vista will not be able to read those partitions.

---

### Post by Crafty Kisses on 2009-05-21
These are the options you have as far as I can tell, but to clarify this, I'd like you to go into the Live-CD and run the following so I can just make sure and tell you what you're best options are, but anyway open up a Terminal and run the following commands:
```
sudo fdisk -l
sudo fdisk -lu
```
From the looks of it right now, you have the options of shrinking C, but you only have 99 gigs, so that's not that much. Depending on how much of that 99 gigs you're using it you can probably run Ubuntu comfortably at 20 gigs depending on what you're going to do with it. The second option is just using your recovery partition and installing Ubuntu on that, not sure if you want to do that though.

---

### Post by Hoary on 2009-05-21
> **mangurt said:**
> The recovery drive is the drive that has the vista image in case you have to do a complete recovery of your computer (virus or some major screw-up). 

Malware that considerately refrained from screwing up this partition. Er, this is not something I'd want to rely on.

> **mangurt said:**
> I don't know how much you want to play around with deleting partitions, you should be able to create a partition on the main C: drive and install from there.

No, if this drive has four partitions, then that's all it can have.

---

### Post by sudeep.makku on 2009-05-22
I agree to you all, But How could I create some more partitions as Vista is only allowing 4 partitions which I already have.....How further I could create

---

### Post by Gausian on 2009-05-22
shrink your main partition in vista with the built in tool.  then use the ubuntu install cd to install on that empty, unallocated space.

vista wont even know that the partition is there since it cant recognize linux partitions.

---

### Post by sudeep.makku on 2009-05-22
> **Gausian said:**
> shrink your main partition in vista with the built in tool.  then use the ubuntu install cd to install on that empty, unallocated space.

vista wont even know that the partition is there since it cant recognize linux partitions.
Thank You Gausian 
But Vista is not allowing more than 4 partitioms and it already contains 4 partitions as i mentioned earlier..........Now what I should delete........Do I need to make Logical partitions......How?

---

### Post by Gausian on 2009-05-22
is vista not allowing you to shrink and the 99gb partition?

---

### Post by sudeep.makku on 2009-05-22
My computer comes with 4 partitions 
177MB EISA 
99 GB C
10 GB Recovery
2.5 Hidden ( I suppose for Dell Media Direct)

So although it is allowing C drive to Shrink but not allowing to create a new Volume.

---

### Post by sudeep.makku on 2009-05-22
> **Gausian said:**
> is vista not allowing you to shrink and the 99gb partition?
My computer comes with 4 partitions 
177MB EISA 
99 GB C
10 GB Recovery
2.5 Hidden ( I suppose for Dell Media Direct)

So although it is allowing C drive to Shrink but not allowing to create a new Volume. 
[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by Gausian on 2009-05-22
shrink the volume in vista and use the unbuntu install cd to create the new partition as per my original post.

in other words, leave the space created by shrinking empty and let gparted do the volume creating.

after installing ubuntu on the freed space, vista will not see the newly created partition.  it will still think you have only 4 partitions.

---

### Post by sudeep.makku on 2009-05-22
Ok Thank You...I will try this and will see if it works..and will reply you

---

### Post by sudeep.makku on 2009-05-22
> **Gausian said:**
> shrink the volume in vista and use the unbuntu install cd to create the new partition as per my original post.

in other words, leave the space created by shrinking empty and let gparted do the volume creating.

after installing ubuntu on the freed space, vista will not see the newly created partition.  it will still think you have only 4 partitions.
Ok Thank You...I will try this and will see if it works..and will reply you

---

### Post by luvr on 2009-05-22
You can shrink the "C:" partition all you want, but, as you have already pointed out, you won't be able to create an additional partition, since you already have four--which is the maximum number of partitions on a PC disk drive.

If I were you, I would zap the Recovery and Hidden partitions (in addition to, perhaps, shrinking "C:"), and install Ubuntu on the space that you free up.

(Well, if I *really* were you, I would delete **all** current partitions, and forget about Vista--but, then, I'm *not* you, am I?)

If you want to make sure that you can keep using Vista, then it is a good idea to create an image backup of your disk before you start, though.

---

### Post by Gausian on 2009-05-22
i think the 4 partition limit is for primary partitions only, which i'm pretty sure the dell partitions are not.

---

### Post by sudeep.makku on 2009-05-22
> **Gausian said:**
> i think the 4 partition limit is for primary partitions only, which i'm pretty sure the dell partitions are not.
Yes these are 4 primary partitions only..........Now what should I do to install ubuntu.........do i need to delete one partition or i need to make some other sort of partitions

---

### Post by luvr on 2009-05-22
> **sudeep.makku said:**
> do i need to delete one partition or i need to make some other sort of partitions
Would you mind running the commands that [**Codename** mentioned above,]("http://ubuntuforums.org/showpost.php?p=7324312&postcount=5") and post the output here? That's really the only way for us to be sure what types of partitions you currently have, and whether or not you could create more of them without having to delete any of the existing ones.

---


---
title: "How to go Linux, full-time"
date: 2006-10-01
forum: Desktop Environments
---

### Post by PigCorpse on 2006-10-01
Hi!

I'm switching to Kubuntu, full time!

Now, when I installed it, I had only two mountpoints, / and swap. I'm going to remove my Windows partition. Should I keep it as / and swap? Or should I consider having more mountpoints? What is the purpose of having many mountpoints?

Also, if I remove my Windows partition, the partition names will change. If I want to solve that, all I need to do is edit the fstab to reflect the changes, correct?

And is it possible to resize a Linux ext3 partition towards the beginning? To clarify, my Windows partition is the first one on the disk. If I remove it, can I resize the Linux one to the left, or is it only resizable to the right?

Also, what's the best way to back up a Linux partition? Currently, I'm using Acronis True Image in Windows, which is the only use I have for Windows right now. I can't remove the Windows partition without finding a way to back up my Kubuntu install.

Thanks!!!

---

### Post by meng on 2006-10-01
I recommend a separate partition (mountpoint) for /home. That way, you can reinstall Ubuntu, overwrite when a new Ubuntu version comes out, or even change Linux distros without losing your personal data and settings.

---

### Post by PigCorpse on 2006-10-01
How can I make new mountpoints without reinstalling Kubuntu?

---

### Post by orb9220 on 2006-10-01
Well it is basically making the new partition with gparted a ext3 partition then there is a procedure covered here in the forums to copy your root home to new HD and then modify the fstab to point there.

I'll see if I can find the thread that tells you how.

Here it is
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

But I was just talking to billy and he said that you are not allowed to get rid of winXP said something about it being written into the software license.

---

### Post by PigCorpse on 2006-10-01
Wow, thanks a lot! That link is really clear and helpful!

And after reading the whole, unabridged EULA, I found out you were just joking, phew!

So does this mean that I can resize ext3 partitions towards the beginning of the drive (add space to the beginning of the partition)?

Thanks again!

---

### Post by orb9220 on 2006-10-02
Well when you use gparted you can delete the win patition and just leave as unallocated. Then you can either create another partion or resize root to encompass the unallocated space.

Gparted now supports moving partitions too.

> Also, what's the best way to back up a Linux partition?

Search the threads here on > rsync

Post your fstab here and tommorow I look at it and give suggestions if needed.

---

### Post by pay on 2006-10-02
You can try this [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by james99 on 2006-10-02
Thank you orb9220, Ive been checking the forums for a clear and concise way to backup, and youve just pointed me in the right direction.

---

### Post by fabertawe on 2006-10-02
> **PigCorpse said:**
> Also, what's the best way to back up a Linux partition? Currently, I'm using Acronis True Image in Windows, which is the only use I have for Windows right now. I can't remove the Windows partition without finding a way to back up my Kubuntu install.

Thanks!!!

Make a boot disc from True Image and you don't need to go anywhere near Windows ;)  That's what I use, works great.

Paul

---

### Post by Ramses de Norre on 2006-10-02
I thought you couldn't change the start point of an ext3 partition?
But why don't you just make a /home partition in the free space from the windows partition?
And you'll need to change fstab and /boot/grub/menu.lst, otherwise you wont be able to boot!
(you will be if you make the new partition before trying to boot)
Also: do all this things from a live disc, changing partitions on a disc with other mounted partitions is asking for problems, I've been there.

---

### Post by meng on 2006-10-02
> **Ramses de Norre said:**
> I thought you couldn't change the start point of an ext3 partition?
I think the very latest version of GParted allows moving partitions of all types.

---

### Post by PigCorpse on 2006-10-02
Hey, thanks all!

I went to that site about moving the home partition and after copying my home folder to the new partition, the two folders ended up having different sizes, with the one on the new partition being larger. I decided to back off and leave it for another time. Did I do something wrong?

And thanks for the True Image boot disc idea, it worked great!

---


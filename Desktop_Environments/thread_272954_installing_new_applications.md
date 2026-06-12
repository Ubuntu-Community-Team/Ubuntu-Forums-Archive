---
title: "installing new applications"
date: 2006-10-07
forum: Desktop Environments
---

### Post by stansaraczewski on 2006-10-07
I've just installed Dapper Drake on a new system after working with Breezy Badger for several months. The question I have is almost embarassing, but I cannot find an answer. 

I know how to install new applications, but how do I direct the installation to a particular hard drive ? My new 'clone' came with a 80gb drive but I am going to add a couple larger ones. I want to use them for applications.

Thank You

---

### Post by rogier.de.groot on 2006-10-07
Short answer: don't. Not with applications you get with apt / synaptic anyway, they all install to the standard filesystem locations. And 80GB is plenty of room for apps from the usual repositories. If you're building applications from source though, you can usually use an option with the configure script to point them to any directory. I personally prefer /opt, so I'd make the second harddisk /opt.

---

### Post by stansaraczewski on 2006-10-07
Thank You Rogier - I appreciate your prompt reply.

---

### Post by rogier.de.groot on 2006-10-07
Oh, BTW, there are some applications with binary installers, like google earth and the jdk+netbeans package I just installed myself, which let you choose installation paths - again I prefer /opt. But I'm really wondering what kind of application would need so much space on your harddrive? Most of the really big stuff on my machines is just user data - so maybe making your bigger drive the /home partition would be a good idea if that's your situation aswell.

---

### Post by stansaraczewski on 2006-10-07
I don't have a particular application in mind now that would require the space. Still getting used to a new pc, and Dapper Drake after a two month inactive spell. I turned over a older clone running Breezy to my son and now am ready to move forward with rebuilding apps on the new machine. 80gb may be a lot of room... I just don't want to use it all and have to start over with a bigger drive.

Thanks again for your thoughts.

---

### Post by CatKiller on 2006-10-07
You can copy an entire filesystem with the **dd** command. So if you find in the future that you wish to migrate everything to a larger drive you can, assuming your current drive is hda and the other is hdb```
dd if=/dev/hda of=/dev/hdb
```to copy absolutely everything as a perfect clone. Then resize the partitions on the new drive to use all the space, take the old drive out and you're done. But you're unlikely to use more than 80Gigs on normal applications. Data in /home, or source code in /usr/src might get big, I suppose, depending on what you're doing, but those **can** be put on different partitions.

---

### Post by stansaraczewski on 2006-10-07
That's a great solution.

You really aren't a catkiller, are you ?

---

### Post by CatKiller on 2006-10-07
> **stansaraczewski said:**
> That's a great solution.

Thirty years of people with beards.

> You really aren't a catkiller, are you ?

No. It's an anagram.

---

### Post by stansaraczewski on 2006-10-07
My five cats will appreciate hearing that...

---

### Post by CatKiller on 2006-10-07
My two think I'm cruel because I keep making it rain.

---

### Post by CaveRat on 2006-10-07
I have an 80 gig in my system and I have so much left over space I don't ever think I will use it all. Of course I'm not a big gamer either. I was really surprised how much less space is taken up by Ubuntu as compared to Windows. My /usr is 35 gig with 30.18 still free. My /home is 33 gig and 29.56 still free. I have lots of space to play with. 
I am curious if Edgy will take up more space than Daper once it is released as stable?

---

### Post by stansaraczewski on 2006-10-08
Roaming around this forum reveals that there is a bit of controversy on how to copy an existing disk to a new larger one. DD or CP ?

When I display my existing 80gb drive in Gparted the Resize/Move option in the heading is grayed out, unavailable. Is that because I need to boot off of a cd ?

I haven't installed the new 300gb drive yet - am in the process of learning all that I can first so that there will be fewest surprises.

---

### Post by CatKiller on 2006-10-08
> **stansaraczewski said:**
> Roaming around this forum reveals that there is a bit of controversy on how to copy an existing disk to a new larger one. DD or CP ?

cp will copy the stuff that's on a partition - the partition has to be mounted for this.

dd will copy **everything**, MBR and partition table and all. The partition probably shouldn't be mounted for this.

> When I display my existing 80gb drive in Gparted the Resize/Move option in the heading is grayed out, unavailable. Is that because I need to boot off of a cd ?

Yes. You don't want to be moving or resizing a partition that's in use. So you **could** in principle, move or resize data partitions that you've unmounted, but not your / or /home partitions. Best to boot off the live cd, since then none of your partitions will be mounted, with the exception of your swap partition, which can be unmounted with **sudo swapoff -a**.

> I haven't installed the new 300gb drive yet - am in the process of learning all that I can first so that there will be fewest surprises.

That's good practise. You don't want to get halfway-through and then discover that you've done something wrong.

---

### Post by stansaraczewski on 2006-10-08
It's like starting a recipe - make sure you have all the ingredients up front. 

I've seen the term 'Live CD' in relation to partition resizing - is that the distro cd I got in the mail ? 

I didn't pay much attention to what options were presented when I initially installed other than selecting the one to install Ubuntu.

---

### Post by CatKiller on 2006-10-08
> **stansaraczewski said:**
> I've seen the term 'Live CD' in relation to partition resizing - is that the distro cd I got in the mail ? 

Yes. It includes the utility GPartEd, which is used during the install process to partition the drives.

[GParted]("http://gparted.sourceforge.net/") does have its own Live cd that may have a later version of gparted than the Ubuntu Live cd does, which may give it more features.

---

### Post by stansaraczewski on 2006-10-08
That makes it handy (having the utility on the CD). 

If I install the new drive, boot normally from the existing 80gb drive, then copy the contents of the 80gb drive to the new one, can't I just 'unmount' the new one then partition it ?

---

### Post by CatKiller on 2006-10-08
It depends on how you're copying. If you want to use cp (or tar) to do the copy, then you'll need to make the partitions first, so that you have somewhere to copy the data to. You can do this booted off your hard drive, should you wish. So you'd make the partitions, mount the partitions, copy the data, unmount the partitions. But the new drive will not be bootable by this method, so then you'd need to install GRUB to the MBR of the new drive and so on.

It's this last step that makes me prefer the dd method. You get all of the GRUB stuff for free.

---

### Post by stansaraczewski on 2006-10-08
Your method (dd) sounds best.

Thanks again for all your input.

---


---
title: "how to install windows xp in ubuntu 10.10"
date: 2011-02-02
forum: Desktop Environments
---

### Post by subhanil on 2011-02-02
as i am a teacher ipod touch helps me to manage my notes in the ibooks software which i used to do through windows xp by itunes;  now after installing ubuntu without partition( i have only ubuntu in my netbook's hard disk) i am not able to do anything with my ipod as it doesn't support ubuntu; i need windows xp to run in ubuntu 10.10....please help how to do this

---

### Post by JRV on 2011-02-02
In Ubuntu use gparted to move the Ubuntu partition up and leave room at the beginning of the hard disk.

Install XP in the empty space.

Now you will only be able to boot into Windows,
you will need to re-install grub2.

Download the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know to fix grub2.

---

### Post by wgbuntu on 2011-02-25
Rescatux didn't work for me. Any suggestions would be welcome.

---

### Post by 3Miro on 2011-02-25
> **wgbuntu said:**
> Rescatux didn't work for me. Any suggestions would be welcome.

Are you the original poster or do you simply have a similar issue.

If you need windows XP for iPod and iTunes only, then I suggest you install Virtual Box (get it form the [http://www.virtualbox.org/](http://www.virtualbox.org/) so that you can use the USB ports).

---

### Post by Terry of Astoria on 2011-02-25
> **JRV said:**
> In Ubuntu use gparted to move the Ubuntu partition up and leave room at the beginning of the hard disk.

Since you can't edit an active, mounted  partition, You'll have to do that from the Live CD. It should work, but will take time and you can assume it's somewhat risky.
> **JRV said:**
> 
Install XP in the empty space.

Now you will only be able to boot into Windows,
you will need to re-install grub2.

Download the Rescatux disk from this site: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot this live CD and follow the prompts.

This is the easiest way I know to fix grub2.
That seems doable, and probably the best if not the easiest way to do it.

On the other hand, **the Virtualbox method could be attractively quick and easy. However, you'll need a machine with a sufficient amount of RAM and processor power** or it'll just poop out. I've tried doing that on a 1.8 GHz computer with 1 Gig of RAM and it just wasn't going to happen . . .
  **Also it is entirely within the realm of reality that an Ipod could be administered from within Ubuntu. I'm sure I've done it a few times. . .** 
I guess you could search the forums here. 
What model is your ipod? There is a model number usually beginning with "A" on the back  . .

---


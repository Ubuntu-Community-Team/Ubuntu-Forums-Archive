---
title: "using dd to copy Ubuntu from one memory stick to another"
date: 2009-04-10
forum: General Help
---

### Post by MountainX on 2009-04-10
How can I use dd to copy an Ubuntu installation from a 4 GB USB flash drive to a 16 GB SDHC card? 

I know a little about dd, but I have not used it to do anything like this task.

---

### Post by dcstar on 2009-04-11
> **MountainX said:**
> How can I use dd to copy an Ubuntu installation from a 4 GB USB flash drive to a 16 GB SDHC card? 

I know a little about dd, but I have not used it to do anything like this task.

Boot off a Live CD and use the Partition Manager to Copy/Paste the partition, and then restore Grub onto the new drive (search for detailed instructions).

You will also probably have to manually edit the /boot/grub/menu.lst file to reflect the different drive.

---

### Post by MountainX on 2009-04-11
Thank you. Is it safe to asssume that I can put the 4 GB Ubuntu partition on the 16 GB SDHC card and still use the card in a camera (using the rest of the space for another partition)?

---

### Post by lensman3 on 2009-04-11
dd if=<input location> of=<output location>

That's it. if->input file or device....
           of->output file or device........

"cat" will work too, as will "cp -R"

---

### Post by MountainX on 2009-04-11
> **lensman3 said:**
> dd if=<input location> of=<output location>

That's it. if->input file or device....
           of->output file or device........

"cat" will work too, as will "cp -R"

Thanks. I know the basics of dd, but what I do not know is what happens to the remainder of the 16 GB SDHC card after I use dd to copy 4 GB onto it. I also do not know which other parameter values I should use (such as block size, starting position, etc.). If I am going to use dd, I hope someone will give me specific details that will work for the situation I mentioned. I'm hoping to avoid learning by mistakes :)

I would like the rest of the SDHC card to be accessible by my camera after I install a bootable Ubuntu partition on it.

---

### Post by dcstar on 2009-04-11
> **MountainX said:**
> 
........
I would like the rest of the SDHC card to be accessible by my camera after I install a bootable Ubuntu partition on it.

Then shrink the existing partition to make room for the Ubuntu partition.

---


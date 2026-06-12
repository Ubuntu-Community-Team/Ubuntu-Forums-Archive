---
title: "Dell mini 9, Jaunty, Hardy, GRUB... I screwed something"
date: 2009-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-04-17
A couple of days ago, I thought it would be fun to try out Jaunty UNR on my mini 9. It primarily runs Dell's 8.04.1 Hardy. Anyway, so I make the UNR thumb-drive and boot into it as "live" so I can try it and make sure it works before I install it. I ran nicely and smoothly so I thought, I'll install it as dual boot. 

So that is what I did. It asked how I wanted my drive partitioned. I set it up as 5GB of my 16GB drive for jaunty, and left the rest for hardy. Finished the install and all went well. Booted into jaunty a few times and some fun tinkering with it. I soon discovered that for my needs, I really didn't need jaunty. And since it was sorta starting to act funny (gnome would not start on boot up and neither would metacity) I decided to remove it.

So I shut it down and boot into hardy. No problems getting in everything was just the way I left it. From hardy I opened GParted, and selected my drive. It showed the partitions I expected. 1)~25MB, Dell diagnostic. 2)~10GB hardy. 3)~5GB jaunty 4)~a fewMB of something I cannot remember that was created when jaunty installed. So then I merged #3 and #4 and reformatted, getting rid of jaunty. Then I tried to merge the 5GB back together with the rest of the drive and it would not let me. Oh well, not a big deal. So I finished some other tasks while I was on there, and then shut it down.

Now when I try to boot up, I get this:
```
GRUB Loading stage1.5.


GRUB Loading, please wait...
Error 22
```

It will not let me boot back into my hardy OS. Can someone help me please??

---

### Post by armandh on 2009-04-17
and that is when the drive with grub went away
the MBR is ok it just cant find the GRand Unified Bootloader

I would use 9.04 on a memory stick to recover any files and then hit install

---

### Post by Arndtwe on 2009-04-17
I would like to be able to keep Hardy... I am actually running off of a thumb drive (9.04 jaunty UNR) to write this. Is the anything I can do to merge the 5GB back, and have my system back the way it was before I tried any of this? Or, at least get my system back to the way it was?

P.S. I did have the idea of re-installing jaunty, but when it gets to the partitioning part, it wants me to make yet another partition. It will not letme use the empty 5GB...

---

### Post by Arndtwe on 2009-04-17
I just had an idea!! But I don't know if it will work...

What if I were to make an .ISO or .IMG file of the Hardy partition? Would I then be able to install that image on a thumb drive using something like UNetBootin and install it on the system over all the partitions, essentially putting everything back the way it was?

---

### Post by armandh on 2009-04-17
using 9.04 on the memory stick be sure the partition is gone [not just reformated]

then install using [guided-largest-unpartitioned-space]option

you may need to use a partition editor on usb stick to clean up the disk.

---

### Post by WcWofEleven on 2009-04-17
Based on the first reply, I'm fairly sure that you can repair by simply Googling a way to install GRUB without reinstalling, doing so, and then manually configuring GRUB to boot to your old Hardy partition.

---

### Post by Brandon Williams on 2009-04-18
The most likely problem is that grub is looking for its stage2 boot info on the partition that you got rid of. Boot off of the stick and reinstall grub, making sure that it knows to look at the hardy drive to find its stage2 boot data.

---

### Post by Arndtwe on 2009-04-18
armandh: I'm not entirely certain as to what  you are telling me to do here. Would you please emphasize?

Brandon: How exactly does one go about reinstalling grub, ans configure it correctly?

---

### Post by Brandon Williams on 2009-04-18
> **Arndtwe said:**
> Brandon: How exactly does one go about reinstalling grub, and configure it correctly?

After booting off of your UNR thumb drive, open a terminal. At the terminal, run grub:
```

$ sudo grub
grub> find /boot/grub/stage2
 (hd0,1)
grub> root (hd0,1)
grub> setup (hd0)
grub> quit

```
Make sure that the values you use for the root and setup commands match the output from the find command. Take note of the fact that setup just wants (hd0), not the full (hd0,1).

These commands will install the stage1 boot loader to the MBR on the same disk as your root partition, and it will tell stage1 to look for the stage2 boot loader on correct partition.

---

### Post by Arndtwe on 2009-04-18
Success!! I have now merged my partitions and re-configured grub. Thank you Brandon for your excellent help!

---


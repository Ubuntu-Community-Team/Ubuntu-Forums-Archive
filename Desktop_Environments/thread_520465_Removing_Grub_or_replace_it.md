---
title: "Removing Grub *or replace it*"
date: 2007-08-08
forum: Desktop Environments
---

### Post by reflexion on 2007-08-08
Hi, I want to remove grub.

Here is my situation: I recently got a big problem with grub ([see link]("http://ubuntuforums.org/showthread.php?t=518814&page=4")) but I managed to fix it. I have windows on my primary drive and linux on my portable drive. 

In bios, if I select my windows drive to boot first, it works like a charm, but if I put my portable drive first, Grub pops up and I cant get into any partition. It says: error 22 (I think) "cant find partition" or "this partition does not exists".

I tryed to put my windows cd and do a "fixmbr" command, but when I get into the recovery console, it asks me which Windows partition I want to repair. Because of this, I cant fix the ubuntu mbr.

what should I do?

thank you

---

### Post by guguma on 2007-08-08
You can remove Grub or install it elsewhere using an alternate install cd.

Also you can boot Ubuntu using NTLOADER.

Here is how:

somehow manage to boot into ubuntu. Open Terminal,

install Grub into the Ubuntu Partition ex. hda4

sudo dd if=/dev/<xxx> of=bootsect.lnx bs=512 count=1

<xxx> is hda4 in this example.

copy the file bootsect.lnx to your windows c: drive.

Open boot.ini file and then add c:\bootsect.lnx "Ubuntu" at the end of it.

Now you can access GRUB from NTLOADER.

---

### Post by reflexion on 2007-08-08
hmmmm really sorry, but I didnt get all of this.

what do you mean when you say "boot ubuntu  using NTLOADER"


and what is this command "
sudo dd if=/dev/<xxx> of=bootsect.lnx bs=512 count=1"?

---

### Post by reflexion on 2007-08-08
help???

please!


Nobody?

---

### Post by reflexion on 2007-08-09
well thank you all for your help, but I managed to solve it on my own.

here was the problem:

when I was selecting my portable drive for first boot, it was now the primary harddrive and therefor was name hd0.

But grub was seeing it being hd1 and vice versa for windows.

So on the Grub boot screen, I pressed "e" on my ubuntu kernel and changed the "hd1,2" to "hdo,2" and hit "b" (for "boot").

Guess what ? -- It worked.

Back in ubuntu, I edited menu.lst and swapped my hard drive letters.


All things back to normal.

---


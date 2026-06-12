---
title: "Updates messed up computer?"
date: 2005-05-23
forum: Desktop Environments
---

### Post by sc3252 on 2005-05-23
I am not sure if it was from the updates, but today I installed some updates that had poped up and a few hours later i decided to restart my computer and now I get a kernel panic when trying to start up my computer, The only reason I am connecting the updates becuase I remember seeing something about updating kernel headers and some other stuff in the update relating to kernel stuff.  Has anyone else had this problem.  I will read the full output and post it in a sec.

---

### Post by sc3252 on 2005-05-23
[update]
This is the mesage that I get "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"

---

### Post by pdk001 on 2005-05-24
i had a some problem since updating kernel header, can't automatically multiple booting with win, so i did format and re-install linux..

---

### Post by sc3252 on 2005-05-24
Is there anyway to get around this with some grub command?  Or am I stuck with reinstalling?  If reinstalling is the case you can bet I am rethinking if I should even install linux. :mad: Lucky me the update was today and not yesterday since I just turned in my finnal SRP today and printed it 5/22.  Well I guess I will just keep windows since I really cant deal with these kinds of problems right now(I really did think ubuntu was my distro ](*,) )

Edit: Also I have one more thing to say, updating kernels without creating a backup of the last one is a stupid practice, just follow fedora's example here.  When ever fedora updates there kernel they creat another entry in grub and let you delete the last one if it works properly.

---

### Post by mdbarton on 2005-05-25
had the same thing.  Fortunately I had already taken the precaution of creating a boot floppy.  Just copied the menu.lst file from the floppy and I was sailing again.  Suggest you create one if you haven't.

However I agree - the update should not have hosed the grub configuration!

---

### Post by salacious_crumb on 2005-05-25
Could you post your menu.lst from your boot floppy?  I've got the same problem as the guys above.  I used knoppix to get in and poke around, but I can't find what changed in my menu.lst.

---

### Post by DaGGer on 2005-05-25
well like i've been told when i first started using linux...don't fix what isn't broken....a friend told me not bother updating if there is nothing wrong with my computer....so i have only updated about 3 times just because i can't help it and well its fine for right now...

---

### Post by pappo on 2005-05-25
If you can get to your Grub menu, you should have some previous kernels listed there.
Try using one of them to boot your machine.  If it boots then, you can remove the new kernel from your system with synaptic, or just edit your grub file to remove it from the menu.

---


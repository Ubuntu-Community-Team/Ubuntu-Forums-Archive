---
title: "Help Please"
date: 2009-03-04
forum: General Help
---

### Post by Jack99 on 2009-03-04
[I]I've tried Ubuntu 8.10 , about 3 times in the last week , and every time i load it up either via the Wubi Installer or via a Dual Boot , i find it crashes , its slow , and when i tried to change the skin and the screen resolution ..again it would crash .. also after updating the software , it would come up saying Connection Lost ( I have a wired DSL D-Link Router) , so i dont understand whats going on , bit of a shame really as Im looking to switch over to Linux / Ubuntu from Vista .

Also i have a 250 Gigs partition that i made within Vista to keep all my music / files /vids etc etc ...but when ive not got Vista installed , Ubuntu says it cant read the partition ...bit of a bugger really cos if i do swap over to Ubuntu i would want to use that partition for my music and other files .

so if anyone has any tips please lol

I'm new here by the way 

Thanx Jack.
[/I]

---

### Post by joey-elijah on 2009-03-04
It always helps to state the problem in the thread title.

You say you've installed via WUBI and dual booting. Which are you having issues with? Are you still using both? If you're competent enough to have created a partition then i would remove WUBI Ubuntu from within Windows and go with the dedicated partition option. Also, which version of Ubuntu are you using?

> ***but when ive not got Vista installed , Ubuntu says it cant read the partition ...***If you've installed via Wubi, you need windows as it uses the Windows boot loader.

If you've installed it via a dual boot it may be writing the GRUB files to the MBR on the Windows Partition.

to access your files from a WUBI install: - 

*The Windows partition where you installed Wubi is available as /host within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media *

> ***i find it crashes , its slow , and when i tried to change the skin and the screen resolution ..again it would crash***

Well it certainly shouldn't be doing that. It sounds like you may not have your graphics/card set up properly? Has a pop-up, er, popped up asking you to enable restricted drivers?

---

### Post by Jack99 on 2009-03-04
[I]ok i had a USB hub plugged in so thats why i was getting the error when trying to boot Ubuntu 8.10 , but now thats ok as ive taken it out .

The other issue im having is this , I have Vista and Ubuntu 8.18 on a dual boot , thats all good, 


The main issue i have is that i made a 250 Gig Partition within Vista and i keep all my files on it  ..films  / music / pics etc etc  , the thing is , Last week i dumped vista ( as im looking to stop using it and cross over to linux ) and installed Ubuntu ...but when i tried to get my files from the 250 partition i made with vista it wouldnt let me , it said it couldnt be mounted ...so im asking is there any way to use that partition from only having Ubuntu installed 




Ok well I'm gonna go away and try to sort it out , and thanx for the quick response 


Thanx
[/I]

---

### Post by joey-elijah on 2009-03-04
> **Jack99 said:**
> ***so im asking is there any way to use that partition from only having Ubuntu installed***

Yes there is! I have partitions with music on that are shared between Windows and Ubuntu and i can access them fine. All you need to do is install the **NTFS configuration tool** from *add/remove* (Applications > Add/Remove) and you're good to go!

(Sometimes a Windows partition can refuse to mount if it was in use and then 'uncleanly' shut down (i.e BSOD, hitting restart without windows shutting down, etc). These can be sorted out by either logging back into windows and then logging out so everything is unmounted 'cleanly' or by force mounting the drives through the command line in Ubuntu. If you don't have windows anymore, this doesn't apply.)

---

### Post by Jack99 on 2009-03-04
> **joey-elijah said:**
> Yes there is! I have partitions with music on that are shared between Windows and Ubuntu and i can access them fine. All you need to do is install the **NTFS configuration tool** from *add/remove* (Applications > Add/Remove) and you're good to go!

(Sometimes a Windows partition can refuse to mount if it was in use and then 'uncleanly' shut down (i.e BSOD, hitting restart without windows shutting down, etc). These can be sorted out by either logging back into windows and then logging out so everything is unmounted 'cleanly' or by force mounting the drives through the command line in Ubuntu. If you don't have windows anymore, this doesn't apply.)



Yeah i went and had a look for the NTFS configuration tool , it is there , but im still unable to access the partition  , it tells me " You are not privileged to mount the volume 'BkUp Drive'. " , so im a bit lost.

So looks like that NTFS Tool dont work for evryone then eh lol

---

### Post by Jack99 on 2009-03-15
Oh and thanx  for all the dedicated help ...it was unparalleled

---


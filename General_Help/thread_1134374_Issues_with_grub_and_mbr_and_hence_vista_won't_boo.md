---
title: "Issues with grub and mbr and hence vista won't boot"
date: 2009-04-23
forum: General Help
---

### Post by lgp171188 on 2009-04-23
I had a triple boot machine - OpenSolaris 2008.11, Ubuntu Hardy and Windows Vista Home Premium with OpenSolaris grub as the only grub install and I added entries in it to boot ubuntu. 

A few days back I formatted the Ubuntu Hardy / partition and installed intrepid without installing grub hoping that I will be able to boot ubuntu from the opensolaris grub command prompt as I was doing with hardy installationm but unfortunately couldn't.

So I installed intrepid with its grub and chainloaded the opensolaris grub. I also in the process of finding out how to make it work, did a install-mbr on my hdd.

The next time I tried to boot into Windows Vista (a couple of days later), I get winload.exe missing or corrupt error and am unable to boot into the OS.

Could the install-mbr or installing multiple grubs and chainloading them have affected the vista installation?

Is there any way to undo the damage?

---

### Post by meierfra. on 2009-04-23
> The next time I tried to boot into Windows Vista (a couple of days later), I get winload.exe missing or corrupt error and am unable to boot into the OS.


Did you resize the Windows Vista partition?

Try this: Boot from  the Vista DVD. After choosing your favorite language, choose "Repair Computer".

If the DVD offers to repair  a  problem, say "yes".
Otherwise choose "Start Up Repair" at the next screen.

If you don't have a Vista DVD, you can get a Vista Repair CD from [here]("http://www.pcworld.com/downloads/file/fid,71039/description.html")

Usually, this is enough  to fix the "winload.exe" error. 
If this does not work, come back here and we'll have to have a closer look at your system

---


---
title: "Grub Error 17 (noob)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by adambaz on 2005-10-13
Hello, i installed ubuntu about 8 months ago, and used it regulally until i had to start using windows again due to incompatibility with software i use at college.

I stopped using ubuntu since, and recently i decided i no longer needed ubuntu on my system (3 partitions - Windows, Linux, Media)

Upon formatting the linux partition i get error 17 when i try to boot and i cannot even boot into windows anymore.

I have a live ubuntu disk, but just need the directions on what to do.

Thanks a lot for your help in advance.

Adam Bailey

---

### Post by solstice on 2005-10-13
i am a noob too. I thought the boot menu was stored on the main boot record portion of hd0, but I could be wrong. Are you getting a menu on which system to boot?

If not, you will probably just need to fix the main boot record.

Like I said, I'm not sure. Figured I'd say something since no one else has yet.

---

### Post by elijah_snow on 2005-10-13
Hi Adam

I think the problem is that your computer is still looking at that partition for instructions on how to boot (because that's where grub was installed). So now you have to tell it to look elsewhere. 

Do you have your Windows install disk? I think you can boot into "rescue mode" and type the command "fixmbr" (where mbr means Master Boot Record).

After doing this, your computer should boot into Windows normally.

---

### Post by Ulrik on 2005-10-13
The Grub files lived in /boot, which was most likely in the linux partition you reformatted. I only know two solutions to this:

1. Reinstall Ubuntu/Grub and make sure to mount /boot to a seperate (tiny) boot partition. When you are sure everything works, you can then remove the rest of Ubuntu as you please without causing disaster. Or,

2. Reinstall Windows

Someone may have e more elegant solution.

Edit: As elijah_snow, who beat me to answer this post by 2 minutes, clearly does.

---

### Post by dumshi on 2007-09-20
Same error pop'ed up when i re-started my Ubuntu the other day. 

this is how i solved it.

When in GRUB boot menu, Choose the OS you want to boot to and Press "e" key. That will bring you to edit mode.

If you already know which partation your Ubuntu is on then this is where you manually re-confirm and edit where to look for Ubuntu.

If you don't know which partation your Ubuntu is on then restart your PC and in GRUB menu  press "c" key. That should bring you to GRUB command line and type "find /boot/grub/stage1". This should show you something like:  (hd0,1). Meaning Ubuntu is in HardDrive 0's partition 1.


This technique also solves some VISTA related boot issues.. i.e. if you can't load VISTA boot manager Select "other Operating System" press "e" and then change the Partition your VISTA (or XP) is on. 

Keep in mind that this is not a Complete solution. It's just a temporary fix, just to boot into Ubuntu (and have controls back). Once into Ubuntu edit file /boot/grub/menu.lst and change the Partation number there.

Hope this helps..

---


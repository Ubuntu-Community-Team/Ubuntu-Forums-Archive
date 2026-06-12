---
title: "unistaling"
date: 2008-12-26
forum: General Help
---

### Post by hezy00 on 2008-12-26
supporters hello,
I sent this messege before, I just have to make clear one thing. I have to uninstall 7.10. I have the instalation image on cd. Now, as far as I know uninstalling is made with live cd (which I don't know what is it and how you get it at all). What do I have to do? Do I have to use the instalation cd and turn it to live cd? Do I have to download it? I'll be greatfull for your help.
Hezy.

---

### Post by jerome1232 on 2008-12-26
Are you dual booting or do you just want to reinstall Windows.

If you have a current dual boot and want to remove Ubuntu and make Windows the only OS you will need a Windows cd to restore the MBR and then just use the Windows partition editor to delete the Ubuntu partition.

If you want to just remove Ubuntu and install Windows then you'll need the Windows install cd, just stick it in wipe the disk and install Windows.

---

### Post by hezy00 on 2008-12-26
No windows.... it's doual booting with 8.10. That's why I want to unistall it.

---

### Post by jerome1232 on 2008-12-26
oooooh okay, then really all you need to to is remove 7.10's partition using gparted and make sure 8.10 is the one that's in charge of grub.

to install gparted, once installed it'll be under System->Administration->Partition Editor
```
sudo apt-get install gparted
```
If you have a question about what partition to remove post a screenshot of gparted and ask away.

To make sure 8.10 is the one managing grub I believe running this command from the 8.10 install will do the trick.
```
sudo grub-install /dev/sda
```

---

### Post by hezy00 on 2008-12-27
is "charge of grub" meen the started os?

---

### Post by jerome1232 on 2008-12-27
> **hezy00 said:**
> is "charge of grub" meen the started os?

Now only a portion of grub is stored in what's called the Master Boot Record, it points to where the rest of Grub is installed (Usually /boot).

Now if your Grub is pointing to 7.10's /boot and you remove that partition, grub will fail at stage 1 and never load 8.10. If you run that grub install command from within 8.10 that'll make sure grub is pointing at 8.10's /boot and that grub will load after you wipe out 7.10's partition.

I hope that makes sense.

---


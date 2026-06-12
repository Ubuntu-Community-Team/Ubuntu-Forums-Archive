---
title: "So I Disabled ACPI...."
date: 2008-12-30
forum: General Help
---

### Post by sosaudio1 on 2008-12-30
Due to boot issues and the system locking up at boot time, I edited grub to start without ACPI.

Now I when I shut down, it won't turn off. If I edit the /etc/modules with the APM line as suggested here [http://ubuntuforums.org/showthread.php?t=554850]("http://ubuntuforums.org/showthread.php?t=554850") will it shut off?

---

### Post by eBoxNet on 2008-12-30
i think it will..

except if you disable over bios 2.
in that case i think it wont shut off.

---

### Post by sosaudio1 on 2008-12-30
> **eBoxNet said:**
> i think it will..

**except if you disable over bios 2.**
in that case i think it wont shut off.

So are you saying that if I disable it in the BiOS it will not shut down?
I understand how that would work. So I wont disable the BiOS option

Thanks

---

### Post by eBoxNet on 2008-12-30
yeap.thats what i am saying ;)

---

### Post by sosaudio1 on 2008-12-30
> **eBoxNet said:**
> yeap.thats what i am saying ;)

Awesome

Thanks

---

### Post by Titan8990 on 2008-12-30
It's not that it won't shut off, it just won't do it itself.

---

### Post by sosaudio1 on 2008-12-30
> **Titan8990 said:**
> It's not that it won't shut off, it just won't do it itself.

and that is what editing /etc/modules fixes then?

---

### Post by sosaudio1 on 2008-12-30
> **sosaudio1 said:**
> and that is what editing /etc/modules fixes then?


Doesnt shut off....


I added that line to /etc/modules and still have the problem where the computer stays powered up even though it has gone through the shutdown process....hdd's spin down and I have progress screen that is empty.

Here is the guide I followed

 [Look at the bottom of the page for the changes I made]("http://ubuntuforums.org/showthread.php?t=317554&highlight=acpi")

Now also in looking at the Grub wiki I saw that if you add the lines to the commented line #kopt in menu.lst, if there is a grub update that happens, it will leave this alone...tested and know that if you work on the lines after the ## ## End Default Options ## and perform a grub update, it will wipe out your changes...but I digress....so I wanted to make sure that ACPI is gone...this seems to have helped the PC in the area of speed and boot times. 

To circle back around. I was having some strange lock-ups on boot and after working with the 915resolution file for my intel 845G gfx, I found the problem was not there....hence the disabling of ACPI. Since then, my hardlocks on reboot have not happened....everyone...find wood, knock three times and then cross fingers...thank you for your participation.

Is there a script that I can build or an addition somewhere that will say something like.....disks have halted, system is down, action is power off?

Or, is there another possibility.

System is Linux Mint 5 or AKA Ubuntu 8.04

and is a Dell dimension 2400

Talk amongst yourselves or as House would say...."GO!" (those that do not know look up show on USA or HULU.com called House. It rocks)

And in House fashion, I am going to bed now. But do feel free to beat the problem to death in order to help the whole site get an idea of what this is doing.

Thanks in advance
Rich

---

### Post by sosaudio1 on 2008-12-30
> **sosaudio1 said:**
> Doesnt shut off....


I added that line to /etc/modules and still have the problem where the computer stays powered up even though it has gone through the shutdown process....hdd's spin down and I have progress screen that is empty.

Here is the guide I followed

 [Look at the bottom of the page for the changes I made]("http://ubuntuforums.org/showthread.php?t=317554&highlight=acpi")

Now also in looking at the Grub wiki I saw that if you add the lines to the commented line #kopt in menu.lst, if there is a grub update that happens, it will leave this alone...tested and know that if you work on the lines after the ## ## End Default Options ## and perform a grub update, it will wipe out your changes...but I digress....so I wanted to make sure that ACPI is gone...this seems to have helped the PC in the area of speed and boot times. 

To circle back around. I was having some strange lock-ups on boot and after working with the 915resolution file for my intel 845G gfx, I found the problem was not there....hence the disabling of ACPI. Since then, my hardlocks on reboot have not happened....everyone...find wood, knock three times and then cross fingers...thank you for your participation.

Is there a script that I can build or an addition somewhere that will say something like.....disks have halted, system is down, action is power off?

Or, is there another possibility.

System is Linux Mint 5 or AKA Ubuntu 8.04

and is a Dell dimension 2400

Talk amongst yourselves or as House would say...."GO!" (those that do not know look up show on USA or HULU.com called House. It rocks)

And in House fashion, I am going to bed now. But do feel free to beat the problem to death in order to help the whole site get an idea of what this is doing.

Thanks in advance
Rich

OK so I am a moron, the /etc/modules needs a full reboot apparently before it follows the rules. So it does shut down using that addition....however....even with ACPI disabled, I am still hitting that complete lock up no boot condition....weird thing is, I can hit escape and pretend I know what I am doing to the grub boot line and whether it takes a new command or spits it out, it boots...most times....for example in the e is for edit mode, you can hit tab and get a list of commands, I said at the end of VGA=773 testvbe and I think it did not because there was no cool text or anything to let me know that it was testing video...but....it booted....I am still not convinced that killing ACPI was a bad thing....still testing. PLEASE PLEASE PLEASE, see if you can throw out some checks that I can run to help diagnose and get this system screaming fast.

Thanks
Rich

---


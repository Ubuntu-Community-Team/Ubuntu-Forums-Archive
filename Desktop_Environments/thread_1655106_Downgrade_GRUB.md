---
title: "Downgrade GRUB"
date: 2010-12-29
forum: Desktop Environments
---

### Post by raunhar on 2010-12-29
I use dual boot with windows 7.
I find editing old version of GRUB (that comes with Ubuntu 9.04) very easy.

The older versions have GRUB 2, which is not easily editable, (like editing boot options, disbling old kernel headers etc.).

Is there anyway that after installing 10.10 directly, I can downgrade GRUB to 1.5 version.

---

### Post by drs305 on 2010-12-29
Although I would suggest sticking with G2, if you want to revert to Grub Legacy (0.97) you can follow the instructions from the community doc:
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202")

There is no Grub 1.5. It went from 0.97 to 1.96 (Grub 2).

---

### Post by raunhar on 2010-12-29
Thanks a lot.

I saw later that itis GRUB 1 not 1.5, but stage 1.5

I will follow this and update when done.

Thanks again.
Wishing you a Very Happy 2011.

---

### Post by mister_p_1998 on 2011-02-08
This sounds like what I want to do, I want to do a dual-boot system with Hardy (grub) and Lucid (Grub2)
So I guess if I convert to old grub it'll boot Hardy ok, or can I boot hardy with grub2?

---

### Post by drs305 on 2011-02-08
> **mister_p_1998 said:**
> This sounds like what I want to do, I want to do a dual-boot system with Hardy (grub) and Lucid (Grub2)
So I guess if I convert to old grub it'll boot Hardy ok, or can I boot hardy with grub2?

You should be able to boot Hardy with Grub 2. Run "sudo update-grub" after you install it and G2 should find it. 

The only caution is that you don't want to let the Hardy installation install Grub. Earlier versions of Ubuntu had an "Advanced" tab as the last installation step. Clicking that gave you some Grub options - you would choose to not install Grub. I can't be sure that option was available all the way back in Hardy though. 

If Grub legacy was installed, you could always reinstall G2 from your Lucid OS or the Lucid LiveCD.

---

### Post by raunhar on 2011-02-18
I followed the steps for Downgrading GRUB .
Now I am able to boot to ubuntu but cannot find the Windows option on boot menu.

It is dual boot machine, with Ubuntu & Win XP.

If I keep GRUB 1.97, then how do I reinstall it after re-installing Win XP (as windows gets broken regularly).
For GRUB, i used to run the GRUB CD and it used to get installed.

---

### Post by drs305 on 2011-02-18
raunhar,

If you have a working Grub 2 setup and then reinstall Windows, you should still have all the Grub 2 files on your Ubuntu installation. All you need to do at that point is point the MBR back to the Grub 2 files. 

You can do this by mounting your Ubuntu partition from the LiveCD, then reinstalling grub-pc. (Actually, the term 'reinstalling' is a bit misleadings, as only a few files are recreated).

```
sudo mount /dev/sdXY /mnt  # mount your Ubuntu partition - such as /dev/sda5
sudo grub-install --root-directory=/mnt /dev/sdX # Don't include the partition number, example: /dev/sda 
```

---

### Post by raunhar on 2011-02-19
In this case, are these steps to be followed:
Insert the Ubuntu 10.10 CD . reboot the PC . The installer runs on boot up.
There are few options shown:
Try Ubuntu
Install
Boot from First boot device.....

Which option is to be selected.

---

### Post by drs305 on 2011-02-19
> **raunhar said:**
> 
Which option is to be selected.

You would select "Try Ubuntu". Once you get to the Desktop, open a terminal via the menu (Applications, Accessories, Terminal) and then run the commands.

---


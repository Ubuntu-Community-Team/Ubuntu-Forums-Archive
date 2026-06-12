---
title: "Compiling 2.6.15(and .1) cannot load new kernel"
date: 2006-01-18
forum: General Help
---

### Post by Xandor on 2006-01-18
I am using Kubuntu 5.10 with 2.6.12-10-386 currently. I am trying to update to either 2.6.15 or 2.6.15.1 neither of which are working properly. On 2.6.15 I get an error saying cannot load "/lib/modules/2.6.15/modules.dep" It says that this file or directory does not exist, though it does. This is with an initrd file I created though I'm sure the file will/does not work because I created it while using 2.6.12-9-386(9 not 10) so I'm assuming it saves information for that kernel. If I use no initrd file it says that it cannot mount /dev/hda2 or unknown-disk(0,0) (something like that) It tells me to use an appropriate root= argument in my GRUB loader. In my GRUB loader I put root=/dev/hda2 which is the correct device. It is the same device I use for 2.6.12-9/10 with the same options other than the initrd file which is used for my working kernels. I did have some module warnings saying some are deprecated although I tried using make-kpkg. And when I tried rebooting into the new kernel it hung at "Uncompressing Linux.... OK Booting Kernel" And never did anything. Any help is appreciated, sorry for the vagueness, I'm on a windows machine at the moment at can't get exact names or error messages.

---

### Post by emperon on 2006-01-19
I am not experienced with kernel compiling. But through the searches I made in this forum, I realized that we should have really good reasons to update the Kernel if we are using ubuntu/kubuntu. Since the system is optimized  and tested on the standard kernel coming with the distro. I say if it is not curicial for you stay with 2.6.10 untill dapper arrives

---

### Post by tseliot on 2006-01-19
[QUOTE=Xandor]I am using Kubuntu 5.10 with 2.6.12-10-386 currently. I am trying to update to either 2.6.15 or 2.6.15.1 neither of which are working properly. On 2.6.15 I get an error saying cannot load "/lib/modules/2.6.15/modules.dep" It says that this file or directory does not exist, though it does. This is with an initrd file I created though I'm sure the file will/does not work because I created it while using 2.6.12-9-386(9 not 10) so I'm assuming it saves information for that kernel. If I use no initrd file it says that it cannot mount /dev/hda2 or unknown-disk(0,0) (something like that) It tells me to use an appropriate root= argument in my GRUB loader. In my GRUB loader I put root=/dev/hda2 which is the correct device. It is the same device I use for 2.6.12-9/10 with the same options other than the initrd file which is used for my working kernels. I did have some module warnings saying some are deprecated although I tried using mkkernelimage or something like that, it's the program Ubuntu uses to make the precompiled debian packages of the kernels. And when I tried rebooting into the new kernel it hung at "Uncompressing Linux.... OK Booting Kernel" And never did anything.
Any help is appreciated, sorry for the vagueness, I'm on a windows machine at the moment at can't get exact names or error messages.[/QUOTE]
You can follow my guide ("Kernel Compilation for Newbies") and recompile your kernel.

You can find the link to my guide in my signature (which is at the end of my post)

---

### Post by Xandor on 2006-01-19
[QUOTE=emperon]I say if it is not curicial for you stay with 2.6.10 untill dapper arrives[/QUOTE]

I am updating to get the PCI AC'97 support which, acording to the driver I downloaded, must be built into the kernel. 2.6.12-10 does not have it built in but 2.6.15(.1) both have it built in. I have made some progress on getting it to work. Now the kernel will load but the Xorg system will not. If I log in and run the command startx it gives me an error saying that NVIDIA returned an error that there is a screen but it has no configuration. Then X says that there is no screen at all. I'm sure X said this because NVIDIA couldn't load my screen. I have two ideas, one it's just a kernel configuration error but I have gone through it many times and changed many settings but to no avail. I also think it MIGHT be the NVIDIA driver needing to be recompiled with the new kernel's source.

I have looked at your guide and will try it out. Again, I am not on my Linux box so I can't do it now, but I get out of school in a couple of hours and will try it then and let you know. Thanks.

---

### Post by ArponerO on 2006-01-20
I had the same problem with my laptop, specially with the SATA module. The solution: put it into the kernel, i.e. in the .config file CONFIG_SCSI_SATA=y

Hope this helps

---

### Post by Xandor on 2006-01-20
Well, isn't SATA for SCSI drives, which if I remember correctly is another type of connection or something of that type. Meaning that since all of my drives are PCI they cannot be SCSI, all though I could be very mistaken. I will try compiling it again using make-pkpg oldconfig and then adding the NVIDIA and AC97 modules. If that still doesn't work I will recompile 2.6.12-10 with the AC97 module hoping that it will work because I know that 2.6.12-10 works on my computer. Also, if anyone knows a way of postcompiling the AC97 as a module and it works that would be very nice. One more thing, what is the purpose of the initrd file? How do I know whether I should use it or not?

---

### Post by pelle.k on 2006-01-20
Of course "nvidia" driver can't load X if you've compiled a new kernel! Didn't you read tseliots guide? Change in xorg.conf to "vesa".
I don't understand why your AC97 have to be built into the kernel... resaons?
Download your linux-headers and compile the newest alsa build for your current kernel instead.
Need instructions?

---

### Post by Xandor on 2006-01-20
I thought his instructions were saying either nvidia ati or vesa. And the sound is working ALSA is updated but there are particular codecs I am needing. I will try the xorg configuration. Thanks.

--EDIT--
Alright I tried vesa and it still didn't work I tried nv and it worked. Now I just have to compile again to enable DMA for my harddrive because it's so slow. Then I should be good.

---

### Post by pelle.k on 2006-01-21
Sorry if my last post sounded a bit harsh. That was not my intention....
Yeah, "nv" should do it too. Vesa is a worst case scenario solution.
I really dont think ALSA have to be compiled into the kernel. Modules should be enough in most cases. Strange codecs or not. I'm using a realtek HD sound card (azalia codec) wich made the boot process stop at hotplug, but with updated ALSA from their site i'm 100% satisfied.

tseliots guide is a must-have. I usually go for a kernel with con kolivas patch. I can't speak for everyone, but i usually do the following changes in menuconfig:

Processor type and features -> Processor family -> <your cpu model of course!>
                                               -> Dynamic tick timer "on"
                                               -> Preemption model -> "desktop"

File systems  (important!!)    -> <The filesystem you boot with as "*" instead of "M">

Kernel Hacking                       -> Kernel debugging "off"

Device drivers                        -> ATA/ATAPI/MFM.... -> Enable DMA only for disks "off"

Happy tweaking :D

---

### Post by Xandor on 2006-01-26
Okay, I have done all of those things and it still runs slower than hell. I have done everything I can think of and it just won't run smothly. Once it's loaded a program into my RAM the program runs just fine, but if it loads something from the harddrive than it's way too slow.
Also, I have no support for my sound card on the new kernel. KMix says it's using the Dummy sound card which I have turned off in the kernel configuration so I'm kind of confused on that. I have a VIA 8236 or something like that with AC97 chip set.

---


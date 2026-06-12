---
title: "I've misplaced my Nvidia module..."
date: 2008-12-03
forum: General Help
---

### Post by version7x on 2008-12-03
My nvidia module has fallen and it cant get up!

On a clean install of 8.10, nvidia came up perfectly using the nvidia-glx-177 package.  After a couple weeks of blissful computing, I reboot and no compiz, awn, etc.  I found that the nvidia driver was not loaded...

$ sudo modprobe nvidia
FATAL: Error inserting nvidia (/lib/modules/2.6.27-9-generic/updates/dkms/nvidia.ko): No such device
$ ls /lib/modules/2.6.27-9-generic/updates/dkms/
nvidia.ko

Here's the graphics info from lspci:
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

This is on my dell optiplex 755.

Other (not so) relevant info:
$ dmesg |grep nvidia
[   15.316409] nvidia: module license 'NVIDIA' taints kernel.
$ sudo grep -i "nvidia" /var/log/messages
Dec  3 08:16:07 my-computer kernel: [   15.312586] NVRM: No NVIDIA graphics adapter found!


I've had this problem before with other dell/nvidia/ubuntu combos, nvidia one day, gone the next. Usually, however, i've changed the kernel or something.


Any suggestions?

Thanks!!!

---

### Post by Usufruct on 2008-12-03
So your nVidia card isn't showing up in lspci?  What nVidia card are you using?

---

### Post by version7x on 2008-12-03
No, I've got a non Nvidia inegrated card showing up in lspci...

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)



Its the standard on board dell card for the chipset.  It does have an nvidia gpu and it worked during the initial install, but now I can't load the nvidia module.

Does that help?

---

### Post by s_raiguel on 2008-12-03
I don't know if this is relevant, but my proprietary Ndvidia driver refused to work, then disappeared after I started trying to install different Nvidia drivers using Synaptic in 8.04. Even the "hardware drivers" app under Administration showed 'no proprietary drivers' on the system, although Synaptic clearly showed that the new-glx driver and Nvidia kernel were supposed to be installed. Only the open-source nv driver would actually run, and this was unacceptable because of lack of open GL support and the fact that it continuously runs the cooling fan at full power even when the GPL is idling. The way I finally got a real Nvidia driver installed again was by downloading the latest driver from Nvidia themselves, and installing it as per the instructions on the "Nvidia Manual" page of the community documentation. Now, everything is back to normal, with 3D game support, control over Nvidia server settings, etc. The only glitch I've noticed is that the text on my login screen is very, very small for some reason.

---

### Post by version7x on 2008-12-03
thats a bummer!  a whole lot of work for something that should be automatic.

I've personally tried completely removing all nvidia-glx-177* packages in synaptic and reinstalling.  I've also tried with envyng.  I guess my last step is trying your route with nvidia themselves.

I'll give that a try and post my results

---

### Post by version7x on 2008-12-03
Yeah - no dice. Believe it or not, the nvidia.blah.blah.run script actually said the same thing... about the nvidia.ko module...

It also said that there may be framebuffer support in the kernel that needs to be disabled or that the version of gcc on the system is different than the one used to compile the kernel.

Now I'm really lost!!!!

---

### Post by s_raiguel on 2008-12-03
Boy, what's the deal with the Ubuntu server, it's really slow at the moment? Anyway, are you sure that the Nvidia kernel is installed? It's also possible you have a version mismatch. The Nvidia kernel has to match the driver version. Take a look at your syslog and see if there's some statement like "NVRM: RM/client version mismatch!". Apparently this can happen if you've installed 3rd-party drivers at some point. This was what seemed to have happened to me; I'd tried the Envy driver set, and hadn't uninstalled them completely before trying to go back to the "new-glx". 
As per the instructions on the Nvidia Manual page, you may even have to install Linux scource and recompile. Even if this is unsuccessful, then when you run the downloaded Nvidia driver-installation script, it will detect any mismatch and offer to compile the correct kernel for you (but you may have to have the Linux-source package installed, not sure). That seemed to be the step that finally cured my driver problem, and the rest of the installation went without a hitch. As I say, I'm pretty green at this myself, but this is what I've gathered from the doc pages and my own experience.

---

### Post by version7x on 2009-01-19
I'm guessing it was something like the mismatch issue.  Soon after this post, I was prompted to do an update and afterwards, the issue dissapeared. 


Everything has been going well for about a month now and no nvidia modules have tried any magic on me!

Thanks for the insight!

---


---
title: "No, I can't take it!"
date: 2009-03-24
forum: Desktop Environments
---

### Post by linuxisevolution on 2009-03-24
I am going to go crazy. I might lose my mind. 3 hours, and I still can't figure this out. My problem(since I choose a completely random title) is that I cannot get xorg+ drivers configured correctly. I have the geforce 8600Gt card. It used to work correctly but now I can't run any 3d app including compiz and my screen is stuck in 840x600 resolution.:(

Why?
[B]
UPDATES[/B] I'll never update again.

The story is the updates installed a new (bad) kernel. I actually liked this kernel so went ahead and downloaded the nvidia drivers from nvidia's website. The drivers installed fine, but then I had no sound. :(. So I had to switch back to the old kernel -but when I did my graphics were broken and for the life of me I cannot get it back! I have tried:
[B]
Installing newest drivers from nvidia's site.
Using ENVYNG to uninstall and reinstall drivers repeatedly....
Using synaptic to figure something out.
Talking to my graphics card to see if I could persuade it into letting me play enemy territory, just once.(lol)[/B]

So how do I remove ALL drivers that could cause this problem and somehow start over and install the drivers via gnome's thingy?

Thanks and please help! I am probably just being an idiot here, and it's probably just a simple fix. :(

~written in 840x600 resolution.

(the submit button below is big enough to be a grape fruit.)

---

### Post by linuxisevolution on 2009-03-24
Would someone PLEASE help?

---

### Post by guitar_man on 2009-03-24
run the recovery mode sir,I've experience this problem.Your using jaunty.am I right?

---

### Post by Monsieur Gonzalez on 2009-03-25
Running the installer from NVIDIA increases the risk of messing things up.. unless you have a real good reason, don't. If there's a problem with an updated kernel, you should have the old one in GRUB; boot with the old one and check what the problem is.

If you're using Jaunty, then ask in the right forum, otherwise: 

1st - Try to get rid of the NVIDIA installer the same way you installed it, only, this time, add the --uninstall option (sudo sh NVIDIA-Linux-WHATEVER-pkg0.run --uninstall).

2nd - Reboot and use ENVYNG to install the NVIDIA drivers.

---

### Post by linuxisevolution on 2009-03-25
envyng is horrid, never use it. It will mess things up on a level that you don't even know...

I had to remove all traces of the nvidia driver from /usr/nvidia and my rc.d and then I installed with the nvidia installer again. It's working now. 

I ran the recovery mode a hundred times. I am not a noob, I know mostly what to do, but I never ever thought a driver could remind me so much of widnows.

---

### Post by Monsieur Gonzalez on 2009-03-25
I'm glad you sorted it out. Never had a problem with Envyng, I guess I've been lucky!!!

---

### Post by inobe on 2009-03-25
> **linuxisevolution said:**
> envyng is horrid, never use it. It will mess things up on a level that you don't even know...

I had to remove all traces of the nvidia driver from /usr/nvidia and my rc.d and then I installed with the nvidia installer again. It's working now. 

I ran the recovery mode a hundred times. I am not a noob, I know mostly what to do, but I never ever thought a driver could remind me so much of widnows.

that's fantastic, i am glad you have it setup linuxisevolution .

keep up with the great work :)

---

### Post by markbuntu on 2009-03-26
Just remember Kernel updates can break with proprietary drivers from nvidia and ati due to DKMS issues if old drivers are not removed completely before updating/installing a new driver.

---

### Post by linuxisevolution on 2009-03-29
Thanks for the support. Hopefully my thread will be useful to others :)

---


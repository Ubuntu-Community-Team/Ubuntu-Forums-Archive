---
title: "(No luck) Installing Carolina Puppy Linux to usb"
date: 2014-06-25
forum: Debian
---

### Post by Michael_Delabruere on 2014-06-25
I'm running windows on my current pc but am decently familiar with linux (hence the forum account).
I recently attempted to install Carolina (a fork of Saluki) Puppy Linux on a freshly formatted fat32 drive using Unetbootin.
I had done the same procedure for Slacko and Lucid Puppy before so I was surprised to see my efforts fail this time.
When my laptop booted into the usb containing the Unetbootin created lina-1.2.iso, it first looked for the drivers, no problem, and then looking for the puppy files.....[COLOR=#ffd700].....[/COLOR][COLOR=#ff0000]...[/COLOR]
and then proceeded to tell me that it had failed to locate the puppy_lina_1.2.sfs. Slightly panicked, I booted into windows, checked and there was the exact specified file in the root directory. I looked online and realized a live-cd would do the trick. I plopped in a fresh rewritable cd and asked windows to burn the disk... ejected. Try again... ejected. Darg.
Not to worry! I loaded a Virtual Machine, passing the Splash screen and then blue Windows crash screen; cursed? So I loaded another lucid puppy drive with the failed attempt still connected. Like in a tutorial [here]("https://www.youtube.com/watch?v=ilGBGLejvfM"), created a fat32 partition along a smaller linux-swap partition. I flagged the fat as boot and dragged the contents of the lina-1.2.iso into the drive. I then used Grub4dos to make it bootable and rebooted away!
To not repeat myself, it had the same effect Unetbootin had. Sorry if this is a garbled plea, and more sorry if I *am* cursed and will wander, never finding lina1.2.sfs.

---

### Post by Michael_Delabruere on 2014-06-27
In all the time spent despairing over a usb, I did not have access to another computer. Though the desktop was dead (I was using my laptop), I created a live-cd and usb easily at another desktop. Sorry to flap like a fish. I hope I haven't wasted anybody's time.

---


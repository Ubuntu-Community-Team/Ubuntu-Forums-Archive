---
title: "loading ubuntu boot loader after installing windows"
date: 2009-06-04
forum: General Help
---

### Post by feistybee on 2009-06-04
Dear fellas,

I have both Vista and Jaunty now. Now am going to reinstall Vista. So the boot loader will be modified. 

Now my Jaunty is fully loaded and I dont want to disturb my settings. So after installing Vista, how I can dual boot and select Ubuntu.

Is there anyway? or I need to reinstall Jaunty also? Please help.

---

### Post by vodnguyen on 2009-06-04
@feistybee : I think you have the same problem with me, and here is my solution.
1. Boot up your computer with a live CD.
2. Open terminal and take the root permission : **sudo -i**
3. Get into the grub controller : **grub**.
4. Type "**find /boot/grub/stage1**" without quotes, you will see somthing similar with "(hd0)" or "(hd0,3). This is where grub installed.
5. Type "**root (hd0,3)**". (hd0,3) is the text apear when you type command find ... above.
6. Type "**setup (hd0)**".
7. Type "**quit**".
8. Restart your system and wait for a lucky chance ;)

PS: All the command in bold will be typed without quotes :D. I just careful ... so don't think anything else. And forgive me for the bad English :p

---

### Post by bumanie on 2009-06-04
follow [this thread]("http://ubuntuforums.org/showthread.php?t=224351") - use a live ubuntu cd to boot from. Alternatively, you can use super grub disk from [here]("http://sites.google.com/site/supergrubdiskmirrorlist/")

---

### Post by feistybee on 2009-06-04
gr8!!! Thanks a lot. I will try this.

---

### Post by feistybee on 2009-06-05
The following worked. I got my jaunty back :)

1. Booted from jaunty live CD.
2. sudo grub
3. find /boot/grub/stage1
   it displayed (hd0, 4)
4. root (hd0, 4)
5. setup (hd0)
6. quit

Restarted. And everything is fine. Thx a lot for the support

---


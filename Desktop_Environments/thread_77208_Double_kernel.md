---
title: "Double kernel"
date: 2005-10-16
forum: Desktop Environments
---

### Post by Owdy on 2005-10-16
Grub menu shows 2 kernels: 2.6.12-8-386 and 2.6.12-9-386. CAn i safely remove that oldone? From grub and from whole system?

---

### Post by Rob2687 on 2005-10-16
yes, just remove it in synaptic or whatever.

---

### Post by tim1 on 2005-10-16
Short answer: Yes you can.

Long answer: If you want really want to make sure everything will work fine, check which kernel you are running (with uname -r), and if you're already running the new one and there are no problems you can safely remove the old one. If you're still running the old one reboot your computer with the new kernel and check then if everything works and remove the old one.

By the way, if you remove the kernel through apt/dpkg/synaptic you don't have to remove the grub entry manually, it should be done by the package management system.

greets, tim

---

### Post by Owdy on 2005-10-16
Yes i have been using that newer kernel all the time. Okay, i remove oldone then :)

---

### Post by Owdy on 2005-10-16
Great. Now it says X-server in wrongly configured and wont start Gnome. :(
I removed old kernel and installed newer linux headers. Any ideas how to fix that?

---

### Post by Owdy on 2005-10-16
It says Error:API mismatch. And something about wrong NVIDIA kernels.

---

### Post by Lord Illidan on 2005-10-16
Boot failsafe.. and change the xorg.conf to vesa

Then, reinstall the ncidia drivers with synaptic...or build them from scratch!

---

### Post by Owdy on 2005-10-16
I dont have any idea how to do that. Completely noob.

---

### Post by Owdy on 2005-10-16
It was this linux-restricted-modules-2.6.12-9-386-nvidia-legacy
I removed that and x works.

---

### Post by seldenthuis on 2005-10-16
When you removed linux-restricted-modules-2.6.12-9-386-nvidia-legacy, you removed the kernel modules needed for 3D hardware acceleration. You have to install linux-restricted-modules-2.6.12-9-**686**-nvidia-legacy to het the right kernel modules again. The easiest way to do that is to simply run 'sudo apt-get install nvidia-glx-legacy'. apt-get will then automatically select the right packages for you.

---

### Post by Owdy on 2005-10-16
Right, now my 2.6.12-9-k7 kernel wont work anymore. :P

---

### Post by seldenthuis on 2005-10-16
Whoops. Sorry. Misread your post. Thought you had the 686-kernel installed.

You do need linux-restricted-modules-2.6.12-9-k7-nvidia-legacy package to get your 3D acceleration working though.

---

### Post by Owdy on 2005-10-16
No, i installed that and x wont start. How do i remove that from command line?

---

### Post by seldenthuis on 2005-10-16
Hmm... strange.

You can remove it with 'sudo apt-get remove linux-restricted-modules-2.6.12-9-k7-nvidia-legacy'.

---

### Post by Owdy on 2005-10-16
How can i reinstall ndvia driver in command line? That didnt fix it :(

[http://ubuntuforums.org/showthread.php?p=419111#post419111](http://ubuntuforums.org/showthread.php?p=419111#post419111)

---


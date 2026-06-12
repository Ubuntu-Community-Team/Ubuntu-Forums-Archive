---
title: "Problem with Virtualbox OSE"
date: 2009-02-10
forum: Desktop Environments
---

### Post by Arminius on 2009-02-10
I'm trying to run xp inside of Ubuntu, and I'm using virtualbox ose, if there's a better application for making VM then please let me know.
but the problem I'm having with Virtual box ose is that when I try to start the XP it says this

VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot.
VBox status code: -4011 (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

so how do I disable the KVM kernel extension and recompile my kernel?

---

### Post by jbrown96 on 2009-02-10
Have you tried to install another virtualization product? KVM is the Kernel Virtual Manager; it's the virtualization system built into the kernel. I would absolutely you NOT use it. Try searching in Synaptic for DKMS. Install it if you don't already have it. DKMS is Dynamic Kernel-mode setting; it's very cool because it will automatically trigger the kernel to be rebuilt when changes are made. Now search for KVM and remove anything that seems related. Reboot and you should be set. 


I really like Open-source software, but virtualization is one area where I don't support it yet. I think that Virtualbox is the best solution, but I would go for the closed-source version. Download the appropriate .deb file from virtualbox.org

---

### Post by Arminius on 2009-02-10
ok, thanks for that, I found KVM and uninstalled it, but when I looked up DKMS I found it was already installed, I looked for it in the applications menu and couldn't find it, went to the menu settings to see if it was hiding there and still nothing.

so how do I access DKMS to tell it to reset the kernel?

---

### Post by Arminius on 2009-02-10
while knowing about the DKMS might be good for a newb I've reset my comp and now virtual box seems to be running fine, but now the problem is that XP Home setup does it's thing then it comes up with

Windows XP Home Edition Setup
=============================
Setup did not find any hard disk drives in your computer.
make sure any hard disk drives are powered on and properly connected to your computer, and that any disk related hardware configuration is correct.
This may involve running a manufacture-supplied diagnostic or setup program.
Setup cannot continue to quid setup press F3

and F3 is all you can press, so I don't see how there's anything wrong with the hard drive since I'm currently using them to run ubuntu and type on here.

so any advice?

---

### Post by Arminius on 2009-02-10
ok solved it, for those who come after me you go to virtual box ose gui
click on settings
then hard disks, and the plus button which says add attachment :)

---

### Post by Arminius on 2009-02-10
how do I mark this thread as solved? newb here :)

---


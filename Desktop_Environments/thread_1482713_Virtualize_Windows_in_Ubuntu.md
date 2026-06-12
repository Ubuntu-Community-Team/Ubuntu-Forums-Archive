---
title: "Virtualize Windows in Ubuntu"
date: 2010-05-13
forum: Desktop Environments
---

### Post by claytontlewis on 2010-05-13
I'm so sold on 10.04 that I don't really want to ever have to boot into Windows again. Unfortunately I also love my Zune. I'm trying to set it up so I can run Windows inside of Ubuntu, but I'm having problems. Ubuntu and Windows are installed on different hard drives and I'd like to be able to boot the Windows installation from inside Ubuntu. I tried to do this with Virtual Box but couldn't figure out how to tell it I already had a Windows installation. So my question unto the masses: Is this even possible?

---

### Post by a-user on 2010-05-14
i dont know how you may accomplish it the best way. but regarding virtualbox you have to install windows onto a virtualbox drive. virtualbox cannot take an existing windows partition to boot it.

---

### Post by claytontlewis on 2010-05-14
Is there perhaps another application that could do this?

---

### Post by squab on 2010-05-14
The whole idea of virtual computers is the separation of the physical from the virtual. A virtual computer is designed to run on any hardware.

On my computer I dual boot windows 7 and ubuntu but i also have a virual XP machine for the single purpuse of watching netflix instant watch on ubuntu. The XP machine takes 2.8gb of my hard-drive.

---

### Post by _0R10N on 2010-05-15
I don't think that there's a way to accomplish what you're trying to do, at I'll tell you why. When you work with virtualization and virtualized environments, your OS is installed inside the virtual machine (a virtual disk, specifically). Then the details of the installation are specific to the underlaying virtual machine. When you install an OS as another OS on your system, the same way, it will depend on the underlaying hardware of your PC.

I don't see a way to move your Windows FileSystem into a Virtual Disk. Even if there is a way to do that, you shouldn't expect it'll work reliably.

The best thing you can do (and the safer, also) is to create a new virtual machine, install Windows on it, and then move your files from the original Windows to the virtualized one.

---

### Post by snowpine on 2010-05-15
> **claytontlewis said:**
> I'm so sold on 10.04 that I don't really want to ever have to boot into Windows again. Unfortunately I also love my Zune. I'm trying to set it up so I can run Windows inside of Ubuntu, but I'm having problems. Ubuntu and Windows are installed on different hard drives and I'd like to be able to boot the Windows installation from inside Ubuntu. I tried to do this with Virtual Box but couldn't figure out how to tell it I already had a Windows installation. So my question unto the masses: Is this even possible?

The easiest method is to purchase an additional Windows license, create a virtual machine in Ubuntu (using VirtualBox or similar), and install Windows onto the virtual machine as you would to any other computer.

Of course, the even easier solution would be to get your Zune working natively in Linux. Since I do not know what a Zune is, or what errors you've encountered trying to get it working, I suggest the Search feature at the top right of the screen. Linux users are a resourceful bunch and I'm sure you are not the first user with this question. Good luck! :)

---


---
title: "Need help with VirtualBox 214OSE with USB"
date: 2009-05-07
forum: General Help
---

### Post by bushmaster2000 on 2009-05-07
Hi, i'm running Ubuntu 9.04 and Virtualbox 2.1.4 OSE and have a WIndowsXP virtual machine with the windows add-on software that enables all the cool stuff.

I have an Adaptec USB device and software that's for XP.  It allows me to plug a video source into it and the software runs and shows the video on the screen.  Honestly I use it to play xbox on my laptop when i have no other option when i'm traveling.

So far i haven't been able to figure out how to pass through USB devices from Ubuntu to the XP Virtual machine.  I startd with a basic USB hard drive and XP doesn't see that.  I also have a flash drive reader I want to use within XP as well.

I did see there's some type of procedure for creating a USBUsers group and adding your user account to it and then editing a permissions file, the problem is my Ubuntu doesn't have that file in the directory so there's nothing to edit.

Any help would be appreciated.  Traveling in a few weeks so I need to get this working.

---

### Post by bushmaster2000 on 2009-05-07
I fixed it, you need VirtualBox 2..2.2 and it's insanely easy to pass through USB to the guest XP system.  The setup options are all there and there's a USB icon on the botton of the virtual window so you can pick what you want to mount.  Easy easy.

I was just confused between the difference of the OSE version and the 'non-free' 2..2.2 version which is also free.. a little confusing but it's all worked out.

Bottom line is if you need to share USB stuff, get vbox 2.2.2

---


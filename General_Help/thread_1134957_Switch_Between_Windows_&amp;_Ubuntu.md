---
title: "Switch Between Windows &amp; Ubuntu?"
date: 2009-04-24
forum: General Help
---

### Post by Paul22 on 2009-04-24
Hi there

I just installed Ubuntu within Windows XP using the Wubi installer. Now here's a weird question:

I log into my PC remotely via VNC / Remote Desktop *extremely* often on a day to day basis, and rely on using my desktop computer remotely. Is there a way to flip back and forth between Windows and Ubuntu without having to physically be present during boot time (to press up or down and enter)?

Hmm, that's odd. When I was in Ubuntu, I could see a boot loader ini file in C:\. But now that I'm in Windows, it's not there, even though showing of Hidden Files *is* enabled.

Does anyone know of a way to switch between OS's without physically being at the machine?

---

### Post by Peter09 on 2009-04-24
Well I'm not an expert on Wubi but I am pretty sure that you will only have one operating system booted at any one time, to switch between O/S will require a reboot.

The best way to do this would be to run one of the systems (Ubuntu) as a host and run the other within a virtual machine, using say VirtualBox. This would give you what you want. It also means that switching between windows and Linux is just a matter of switching between a 'desktop window'.

---

### Post by Paul22 on 2009-04-24
Woops, to clarify, rebooting my PC is fine. I can always do that remotely with a few simple clicks. Having to physically stand at my computer, press the down and enter keys on my keyboard DURING bootup is the problem, since I will be dozens of miles away from the PC.

Is there a way to say "Hey Windows XP, next time you reboot, go into Ubuntu automatically.... Hey Ubuntu, next time you reboot, go into Windows automatically." (Though the later won't be necessary since there's a 30 second timeout to automatically choose Windows).

Is there a way to do that? Just to say "Restart Windows, and automatically choose Ubuntu during bootup"?

---

### Post by Peter09 on 2009-04-24
Not a simple method that will not leave you open to a crash. Once you have started a reboot you pretty much lose control of the machine.

---

### Post by Paul22 on 2009-04-24
> **Peter09 said:**
> Not a simple method that will not leave you open to a crash. Once you have started a reboot you pretty much lose control of the machine.

A) Right, I mean, is there a way to modify the boot loader from within Windows before restarting? Like in my first post, I could see the boot loader ini file from Ubuntu. At worst,  I suppose I could make Ubuntu default and then modify that file to be Windows default when I need to switch?

B) Ok, simpler question: right now after 30 seconds of not picking an option during boot, Windows is automatically selected. Let's say I wanted to change that so that Ubuntu was default. How do I do that?

---

### Post by Peter09 on 2009-04-24
Well I guess (although not sure for Wubi) that there will be options in the bootloader to define which is the default boot system. The risk is that a mistype will stop the boot process altogether :(

---

### Post by Paul22 on 2009-04-24
Ahh, here we go:

[http://www.wallpaperama.com/forums/simple-easy-tutorial-change-default-boot-loader-windows-t57.html](http://www.wallpaperama.com/forums/simple-easy-tutorial-change-default-boot-loader-windows-t57.html)

So even though boot.ini is not shown, I can still use Run C:\boot.ini to access it. Here's what I have:

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

```I assume C:\wubildr.mbr = "Ubuntu" is the boot file for Ubuntu? So I can just move it up to the first line after OS and have it work?

(Don't want to try it just yet since I'm already away from home for the day.) Will this work?

---

### Post by Monotoko on 2009-04-24
To see the boot.ini file in Windows, you have to check the box below "Show hidden files and folders" which will be "Show protected operating system files" or something like that (havent used Windows in a while)

---

### Post by Peter09 on 2009-04-24
Mmm I suspect that the line that starts **default=** is the one that defines the default boot system. But I am on dodgy ground here

---

### Post by Paul22 on 2009-04-24
> **monotoko said:**
> to see the boot.ini file in windows, you have to check the box below "show hidden files and folders" which will be "show protected operating system files" or something like that (havent used windows in a while)

Oh  thanks!

---

### Post by Paul22 on 2009-04-24
So I suppose something like:

```
[boot loader]
timeout=30
default=C:\wubildr.mbr = "Ubuntu"
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
```

I'm just not sure if that C:\wubi file can actually work like this

---

### Post by Peter09 on 2009-04-24
Agreed that looks extremely risky as C:/ is not defined until somewhere in windows - but I do not know at what point.....

Getting it wrong may give you an un-bootable machine.

---

### Post by bodhi.zazen on 2009-04-24
Another suggestion ;

Simply use virtualization, you can use windows within Ubuntu with Virtualbox or vmware or KVM.

---

### Post by jamessnell on 2009-04-24
> **Paul22 said:**
> ...

Is there a way to say "Hey Windows XP, next time you reboot, go into Ubuntu automatically.... Hey Ubuntu, next time you reboot, go into Windows automatically." (Though the later won't be necessary since there's a 30 second timeout to automatically choose Windows).

Is there a way to do that? Just to say "Restart Windows, and automatically choose Ubuntu during bootup"?

I used to use a feature from lilo that provided this functionality. It was a part of SuSE way back in the day. I haven't seen the same thing provided with GRUB though.. Nor do I know of a way to do that with the Windows bootloader, however I suspect if you had read/write support for your grub menu file in both OSes, you could just change the default each time.. There's an ext2 driver for windows (that'll mount ext3, just it won't be journalled).

---

### Post by Paul22 on 2009-04-24
> **Peter09 said:**
> Agreed that looks extremely risky as C:/ is not defined until somewhere in windows - but I do not know at what point.....

Getting it wrong may give you an un-bootable machine.

- Well, this is installed via Wubi, so Ubuntu is just a "file within Windows". So is it possible that the "C" drive for the Ubuntu installation will act differently, and allow it to be found (where it normally wouldn't be with a real Ubuntu partition)?

- Also, if I did completely screw up my desktop, how could I fix it (aside from reinstalling Windows on top of the current installation, I suppose)? I backed up all my important data yesterday onto a few DVD-Rs so I'm ok on that front, if something does break. If Windows does break, is there a way to somehow get into DOS and edit the boot.ini manually, and fix it?

---

### Post by jamessnell on 2009-04-24
What I was suggesting would work. 

Do you not like the notion of editing your grub menu file each time you want to change the default boot target?

---

### Post by Monotoko on 2009-04-24
A duelboot using GRUB would be a far less risky way to do what you want to do, and we could all help you more with that (because what your asking for at the moment is help getting Windows bootloader to do this - whilst i hope a lot of us would try to help as much as possible, our expertise are not in Windows)

Besides, duel-booting using GRUB is a better way to do things.

---

### Post by jamessnell on 2009-04-24
> **Monotoko said:**
> A duelboot using GRUB would be a far less risky way to do what you want to do, and we could all help you more with that (because what your asking for at the moment is help getting Windows bootloader to do this - whilst i hope a lot of us would try to help as much as possible, our expertise are not in Windows)

Besides, duel-booting using GRUB is a better way to do things.

So say we all!

---

### Post by Paul22 on 2009-04-24
> **jamessnell said:**
> What I was suggesting would work. 

Do you not like the notion of editing your grub menu file each time you want to change the default boot target?

Sorry, I just didn't know what this was hehe. Ok since this would be a better option:

> **jamessnell said:**
> I used to use a feature from lilo that provided this functionality. It was a part of SuSE way back in the day. I haven't seen the same thing provided with GRUB though.. Nor do I know of a way to do that with the Windows bootloader, however I suspect if you had read/write support for your grub menu file in both OSes, you could just change the default each time.. There's an ext2 driver for windows (that'll mount ext3, just it won't be journalled).
 
Can you elaborate a bit on the GRUB? I admit, I am a Linux newbie. I've been using it for school projects for the past year or so, but this is the first time (yesterday) I've ever installed it on my own PC. (:

---

### Post by jamessnell on 2009-04-24
> **Paul22 said:**
> Sorry, I just didn't know what this was hehe. Ok since this would be a better option:


 
Can you elaborate a bit on the GRUB? I admit, I am a Linux newbie. I've been using it for school projects for the past year or so, but this is the first time (yesterday) I've ever installed it on my own PC. (:

No prob, we all have to learn it somewhere ;)

Here's a good overview of [GRUB](http://www.gnu.org/software/grub/).

In short GRUB is a tool that you can use to manage how your computer boots. So suppose you have 2 hard drives and each has a different operating system setup on it.. Then you could select what system to boot by how you order the drives.. Grub provides a means of changing one drive so that it doesn't boot right away, but rather gives you a menu that you can use to select what drive to boot from.

The uses of grub can get more and more complex, but it's key to note that grub has no brains, you need to configure it by editing a configuration file.. But one of the parameters it keeps in it's config file is what system to boot by default.. So you can edit that file to change that default whenever you like...

There's a start for you...

---


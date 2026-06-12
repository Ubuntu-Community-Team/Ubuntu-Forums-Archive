---
title: "iPhone sync in VBox?"
date: 2009-06-23
forum: General Help
---

### Post by ahndoruuu on 2009-06-23
My parents' computer (which runs Windows XP) got pretty messed up.
Multiple virus issues, and eventually the sound stopped working, despite my best efforts to fix it.  I was thinking it might be hardware related so I decided to run the Ubuntu liveCD that I have from installing Ubuntu on my personal computer

and miraculously the sound worked! The wireless card instantly worked. Everything just worked.  So I told my mom to let me install Ubuntu and the benefits that would be reaped.  She sounded skeptical about it being free but said she didn't care as long as she can use iTunes, including purchasing from the iTunes store and synching her iPhone 3G.

I browsed around and found Wine support for iTunes is buggy and unstable at best.
I found a few posts regarding running iTunes on Vbox and the issues resulting but they were referring to older versions.  

So is there any possible way to run a fully-functional version of iTunes under a virtual machine or emulation software in Ubuntu Jaunty?

---

### Post by starcraft.man on 2009-06-23
I don't think you quite get how virtual machines work. A virtual machine creates a complete simulated computer. In essence, it pretends to be a real machine, then you can install whatever operating system inside of it you want. Like a ROM emulator, only much better performance assuming you have a recent Core 2 or better machine with the hardware virtualization. Even without that you can get acceptable performance.

I recommend the user [manual]("http://www.virtualbox.org/wiki/Downloads"). Best to understand before doing.

I'd also like to note, if you install Windows in a virtual machine you should understand, it will behave just like real Windows. It can get viruses, it can run iTunes and any other app, and it will need to be activated by license.

Once windows is installed, you can pass through any USB device (I assume it works with Linux, I don't do such syncs, I imagine it just uses the mass storage USB driver) from Linux to Windows in the VM. I don't see any reason iTunes wouldn't work once it's set up correctly.

Read the manual, I don't have a better guide off hand at the moment.

Edit: Oh and to note, you can install it from the repos. It's listed as virtualbox-ose. Just go to add/remove in the applications menu, select all applications and search for virtual box. Or use synaptic or a terminal to install the package.

---

### Post by ahndoruuu on 2009-06-23
Oh I do understand how a virtual machine works, I've just read that there are still problems when syncing an iPhone over it.

I guess i'll try it on my machine because my mom won't let me install ubuntu on this computer until she's sure she can use itunes.

---

### Post by starcraft.man on 2009-06-23
> **ahndoruuu said:**
> Oh I do understand how a virtual machine works, I've just read that there are still problems when syncing an iPhone over it.

Oh ok, guess I misread your post, maybe I'm too tired. Well, I can't comment on iPhone. I don't use any apple products, not even an iPod. I don't know of a reason it wouldn't sync inside a VM long as the USB was passed through fine. Though to be honest, if it didn't work I wouldn't be surprised. Apple has gone out of their way over the years to break things, like when they change third party jacks for no reason or changed the hashes because a few guys reverse engineered them for support. I've always been amazed by how abusive they can be to customers without retaliation.

---

### Post by kemargrant on 2009-06-29
Vbox and my iphone 2g work just fine. 
I have synced,restored,jailbreaked, and unlocked my iphone using windows XP in VirtualBox on my Ubuntu machine. When you are configuring VB you just need to make sure you pass the usb connection from your iphone to the Virtualized Xp before starting the virtualized Xp for a smooth jailbreak/restore.
You can do that by going to Settings, and then Usb in Virtualbox. Then simply add the usb connection of your iphone. 
*Note the iphone has 3 usb connection types.If you are jailbreaking/restoring/unlocking your phone, making sure these connections are already added will make your life_** MUCH**_ easier.
1.Recovery mode
2.DFU mode
3.Regular usb mode

---


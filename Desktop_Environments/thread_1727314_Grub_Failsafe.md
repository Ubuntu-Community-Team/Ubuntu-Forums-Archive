---
title: "Grub Failsafe"
date: 2011-04-12
forum: Desktop Environments
---

### Post by Geffers on 2011-04-12
My daughter has just bought a new HP laptop with Windows 7

So as to safeguard warranty issues I installed Ubuntu onto a USB stick so that she can use that rather than alter her existing HD.

Used my 18 month old HP to install onto the stick, worked fine, checked stick in two different Acer netbooks, Ubuntu booted fine.

Wont boot for new machine, gets the screen display that battery state is being checked then just a blank screen and cursor.

If I try the 'Update Grub Bootloader' from the failsafe menu option will it alter my main HD MBR or will it be the USB sticks MBR OR is the bootloader the /boot/grub files.

Geffers

---

### Post by wilee-nilee on 2011-04-12
Don't upgrade grub, you haven't identified first if it is a loaded iso on the thumb or a full install. Actually you are not safe guarding by installing Ubuntu on the usb if there is a problem knowing how to fix it wont be effected by this setup.

As far as getting the usb to boot, power on the computer and tap any key immediately to get the first boot menu if this is just the ISO loaded on the usb, hit f6 and try nomodeset.

If Ubuntu is installed on the thumb=full install hit e at the grub menu and put nomodeset after splash in the kernel line, and boot in and look for a missing graphic driver in menu-system-admin-additional drivers.

So you can see here that stating exactly what type of install goes a long ways here.;)

---

### Post by Kirboosy on 2011-04-12
[COLOR=black][FONT=Verdana]What I would do in this situation is pull the harddrive from your daughters computer temporarily. While the drive is disconnected plug in your thumbdrive and install Ubuntu on it. (This way Ubuntu is setup for the correct hardware) Also since the hard drive is pulled GRUB won’t mess with the hard drive. You might want to try and LiveCD in the computer and see if the LiveCD will work correctly before you do all this[/FONT][/COLOR][COLOR=black][FONT=Verdana]. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]If it doesn't work then there must be a driver/support issue of some sort with the computer. Then you might need to try and Alternate Install CD...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]As for the warranty issue. I made sure to leave the regular partitions (windows, and recovery) on there and then add Ubuntu on. That way if for any reason I need to send it back to the manufacturer I can restore it to the factory settings and the manufacturer can't complain about Linux.[/FONT][/COLOR]
 
~Caboose

---

### Post by Geffers on 2011-04-12
> **wilee-nilee said:**
> Don't upgrade grub, you haven't identified first if it is a loaded iso on the thumb or a full install. Actually you are not safe guarding by installing Ubuntu on the usb if there is a problem knowing how to fix it wont be effected by this setup.

As far as getting the usb to boot, power on the computer and tap any key immediately to get the first boot menu if this is just the ISO loaded on the usb, hit f6 and try nomodeset.

If Ubuntu is installed on the thumb=full install hit e at the grub menu and put nomodeset after splash in the kernel line, and boot in and look for a missing graphic driver in menu-system-admin-additional drivers.

So you can see here that stating exactly what type of install goes a long ways here.;)

It was a full install to the USB with the bootloader installed to the USB and not an internal HD.

Done this way so that if USB not installed computer boots as supplied but when USB installed BIOS boot menu allows options.

Re your suggestion of hitting the E key, I've done this with grub legacy but not grub2 as I can't get my head round the script language; does the E key work the same with grub2.

You suggest looking for missing graphic driver, would selecting (not sure of exact wording) default graphic mode from the failsafe menu be a possibility.

Geffers

---

### Post by wilee-nilee on 2011-04-12
> **Geffers said:**
> It was a full install to the USB with the bootloader installed to the USB and not an internal HD.

Done this way so that if USB not installed computer boots as supplied but when USB installed BIOS boot menu allows options.

Re your suggestion of hitting the E key, I've done this with grub legacy but not grub2 as I can't get my head round the script language; does the E key work the same with grub2.

You suggest looking for missing graphic driver, would selecting (not sure of exact wording) default graphic mode from the failsafe menu be a possibility.

Geffers

With grub 2 hitting e at the grub menu=edit the nomodeset will get you in with a low graphic mode.

Thanks for confirming the type of install, a full install should run fine when set up.

You mention a fail safe menu, do you mean the rcovery? I thnk there is a low graphic mode from there, but if you get a black screen from the get go from a ubuntu menu I doubt if the recovery will get any farther, if you have tried it mention it in detail if you can.

---

### Post by Geffers on 2011-04-12
> **wilee-nilee said:**
> With grub 2 hitting e at the grub menu=edit the nomodeset will get you in with a low graphic mode.

Thanks for confirming the type of install, a full install should run fine when set up.

You mention a fail safe menu, do you mean the rcovery? I thnk there is a low graphic mode from there, but if you get a black screen from the get go from a ubuntu menu I doubt if the recovery will get any farther, if you have tried it mention it in detail if you can.

Thanks for info, will try suggestions.

It may well be 'recovery' rather than failsafe and any further problems I'll try and get her to tell be exactly what is on screen.

Geffers

---

### Post by grvsaxena419 on 2011-04-12
I think as for installing ubuntu on usb drive for warranty reasons is necessary , Caboose885 is right create recovery cds using hp software and create space for ubuntu on your harddrive keeping windows and recovery partition intact and do a fresh install. Installation on hard drive are better and less prone to failure than flash drives . Or if you dont want to touch partitions at all go for a ubuntu install inside windows that may be a better option.

PS: I used HP warranty on my system while installed ubuntu on it .

---

### Post by Geffers on 2011-04-13
> **grvsaxena419@gmail.com said:**
> I think as for installing ubuntu on usb drive for warranty reasons is necessary , Caboose885 is right create recovery cds using hp software and create space for ubuntu on your harddrive keeping windows and recovery partition intact and do a fresh install. Installation on hard drive are better and less prone to failure than flash drives . Or if you dont want to touch partitions at all go for a ubuntu install inside windows that may be a better option.

PS: I used HP warranty on my system while installed ubuntu on it .

The proper installation is an eventual intention but she doesn't live with me and in theory a working system on a USB stick is very simple. I knew she was getting a new computer, she loves Ubuntu so this should have been a quick option.

As for the Wubi option, never tried it so might be an option.

Geffers

---

### Post by grvsaxena419 on 2011-04-13
> **Geffers said:**
> The proper installation is an eventual intention but she doesn't live with me and in theory a working system on a USB stick is very simple. I knew she was getting a new computer, she loves Ubuntu so this should have been a quick option.

Ok. 
I have never myself used a system on USB stick but don't know why its causing problem may be due to some driver problem . It might be facing some graphics driver issues. :confused:
> 
As for the Wubi option, never tried it so might be an option.

Geffers

All the best for that :)

---

### Post by Geffers on 2011-04-13
> **grvsaxena419@gmail.com said:**
> Ok. 
I have never myself used a system on USB stick but don't know why its causing problem may be due to some driver problem . It might be facing some graphics driver issues. :confused:


All the best for that :)

I think it must be a graphic driver as selecting the low graphic (I think that is the wording) option from the Recovery menu works fine and strangely the screen res looks fine.

Geffers

---

### Post by grvsaxena419 on 2011-04-14
> **Geffers said:**
> I think it must be a graphic driver as selecting the low graphic (I think that is the wording) option from the Recovery menu works fine and strangely the screen res looks fine.

Geffers

Yes that happens as ubuntu tries drivers of the system in which it was installed onto the USB stick but then it is used on a different system. I think that may be the problem. 
Try installing ubuntu on USB stick in her laptop and when the setup gives finish option ( if you choose to install Ubuntu 10.04) it gives an advanced options button and in that you select USB stick for installing MBR ;)
I think that would work :)

---

### Post by Geffers on 2011-04-14
> **grvsaxena419@gmail.com said:**
> Yes that happens as ubuntu tries drivers of the system in which it was installed onto the USB stick but then it is used on a different system. I think that may be the problem. 
Try installing ubuntu on USB stick in her laptop and when the setup gives finish option ( if you choose to install Ubuntu 10.04) it gives an advanced options button and in that you select USB stick for installing MBR ;)
I think that would work :)

Thanks for tip.

I know on my system there is a menu choice to install proprietry drivers so that ** may ** be an easy option, if not I'll give your suggestion a try.

Geffers

---

### Post by grvsaxena419 on 2011-04-14
> **Geffers said:**
> Thanks for tip.

I know on my system there is a menu choice to install proprietry drivers so that ** may ** be an easy option, if not I'll give your suggestion a try.

Geffers

Ok. yes that will be nice if it installs the driver and everything gets fine . ;)
Good Luck ..:)

---


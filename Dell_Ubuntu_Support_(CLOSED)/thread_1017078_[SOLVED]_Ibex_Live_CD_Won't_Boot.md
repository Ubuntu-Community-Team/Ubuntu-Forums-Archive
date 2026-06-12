---
title: "[SOLVED] Ibex Live CD Won't Boot"
date: 2008-12-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 888gavin on 2008-12-20
Hey everyone,

I've decided to switch back to Ubuntu, so today I downloaded the Ubuntu Ibex (8.10) Live CD. I burnt it to a CD with PowerISO, and started up the computer with the CD inside the tray. I came to the Ubuntu Live CD menu, and selected "Try Ubuntu Without Affecting Current OS Installation". That wasn't exactly what the option said, but you get what I mean. Anyway, I selected that, and then the Ubuntu logo came up, with the "bouncing" progress bar underneath it. It does this for two minutes, all the while the CD drive making a noise as though the computer is looking for something, but gives up 1 second later. Then, the screen changes to the BusyBox console thing. I am given a never-ending stream of errors such as "ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen" and "end_request: I/O Error, dev sr0, sector 14311559". This just goes on and on, forever, I am assuming, as I don't really want to sit there and wait for two hours to see if something changes. However, if I HAVE to do this I suppose I could leave it running while I watch TV or something.

I have searched Google quite a bit, and found nothing that has helped me so far.

When I used to run Ubuntu, months ago, it worked fine. Then, I upgraded it, and it wouldn't start. I found out later that it was due to the kernel being updated, so in order to get Ubuntu working back then, every time I turned on the computer I'd have to select an old kernel from the GRUB menu. Maybe this has something to do with it?

Also, would the problem have anything to do with the fact that my hard drive is "IDE"? Should it be set to "RAID"?

I have a Dell Inspiron 530, and it has an nVidia Graphics Card.

Please, I would really love to get back into Ubuntu, and ANY help towards me fixing this problem would be greatly appreciated.

Thanks a lot,

888gavin

---

### Post by 888gavin on 2008-12-21
Please, anyone, I really need some help. Have I posted this in the right section? If not, can someone move it for me?

Thanks a lot,

888gavin

---

### Post by howefield on 2008-12-21
Try a different version, like 8.04 which is an LTS release.

Which version did work for you ?

---

### Post by gbrainin on 2008-12-21
> **888gavin said:**
> Also, would the problem have anything to do with the fact that my hard drive is "IDE"? Should it be set to "RAID"?

I have a Dell Inspiron 530, and it has an nVidia Graphics Card.

Yes, that's probably the problem.  On several computers, the 530 included, newer versions of Linux (from 8.04 onward) don't like to work in IDE mode, and tend to drop you into the "busybox."  Try switching to RAID mode and immediately booting from the CD.

If that works, your old OS will probably not like being in RAID mode, so you will need to switch back if you're going to dual-boot.  In that case, there's a command-line switch you can add in the GRUB menu that makes things work in IDE mode.  I forget what it is just now, but you can search for it on this forum.  If you're switching entirely to Ubuntu, then RAID mode will do you fine.

---

### Post by armandh on 2008-12-21
more likely a bad burn 
in those first selections is there a check cd option?

---

### Post by 888gavin on 2008-12-21
The release that worked on my computer months ago was Gutsy Gibbon (7.10), howefield.

So, gbrainin, are you saying I should set up by BIOS so that my hard drive is RAID mode, and set up the boot list so that "CD" is first, BEFORE hard drive?

armandh, there IS an option to check the cd, but I think it does basically the same thing, the Ubuntu logo appears, and the progress bar bounces back and forth.

---

### Post by 888gavin on 2008-12-21
I set the SATA mode to "RAID", and made the first boot device the CD drive. This caused no change, Ubuntu still does not boot.

Selecting the "Check Disk for Defects" option does the same thing as "Try Ubuntu Without Affecting Current OS Installation" option, the logo appears and then after a minute the BusyBox prompt.

I'm really not sure what to do from this point on!

---

### Post by armandh on 2008-12-21
first take the disk to another computer to see if the live cd will boot.

the bios should be cd boot first
usually the cd must be on the first IDE line [assuming not serial ata]

same problem = bad disk

---

### Post by 888gavin on 2008-12-21
I've burnt another CD, and tried to boot into Ubuntu. Still no luck. I also tried the old CD on the other computer downstairs, and it seemed to work fine, but it took quite a while to load.

One thing that happened though, when I burnt the second Ubuntu CD, I set PowerISO to burn at 4x, and to verify the data after it was written. I got an error saying "Action is Illegal" or something, and was given a choice to Abort, Retry, or Cancel. I just chose Abort, and the disk was finished.

I don't understand what's going on here, is it a problem with my computer's hardware/firmware, or is it a problem with the ISO file or PowerISO?

Once again, all of your help is greatly appreciated.

Thanks a lot,

888gavin

---

### Post by armandh on 2008-12-21
the first disk booted to the live os on another computer
we may assume it is ok but how long? more than 2 minutes something is bad. or memory is small.

back at the target machine bad cd drives can cause trouble
not enough ram is a killer [256 meg minimum]

---

### Post by gbrainin on 2008-12-22
This is not behaviour I've seen before, so I guess we're in detective mode now.

It may sound silly, but I'd try physically disconnecting the hard drive and see if the CD will boot properly.  This won't solve your problem, just trying to isolate it.

---

### Post by gbrainin on 2008-12-22
Another thought on a similar vein: Try disconnecting all unnecessary USB devices (leave just keyboard and mouse).

Looking more closely at the error messages you got, I see they reference sr0, which should be the first CD/DVD drive; that makes me think that the error is there, but it's still worth a few minutes to eliminate some other possibilities.

---

### Post by 888gavin on 2008-12-22
[IMG]http://gavinscorner.com/files/images/UbuntuErrorJPG.jpg[/IMG]
This is a snapshot of the BusyBox prompt.

I tried unplugging everything USB except for the keyboard and mouse, still no change in behavior.

Should I maybe use other software for burning the ISO? I really think that this can't be a problem with my CD drive, since I barely use it, I don't understand how all of the sudden it could be broken.

---

### Post by 888gavin on 2008-12-22
I am now writing this message from the Kubuntu 7.10 Live CD. How is this possible? Kubuntu 7.10 booted up flawlessly, everything went absolutely fine, yet the newer releases simply won't work.

I noticed that when Kubuntu started up, it said "Loading Linux Kernel", while my Ubuntu 8.10 Live CD didn't do that. Is this normal?

This MUST be some sort of problem with the newer Linux kernel. What should I do?

Thanks a lot,

888gavin

PS: Here I am, once more from the Ubuntu 7.10 Live CD. Funny thing is, this CD actually had a pretty bad scratch on it, it had a small hole where I'm sure some data had to be missing, yet it booted up fine.

---

### Post by 888gavin on 2008-12-22
Anyone?

[IMG]http://gavinscorner.com/files/images/BIOSPic.jpg[/IMG]

Here's a snapshot of a message that pops up right before the boot menu, when the hard drive is set to RAID mode. It doesn't pop up in IDE mode, though.

---

### Post by gbrainin on 2008-12-22
Failing to boot and ending up in busybox mode is the expected behaviour for the IDE vs. RAID problem, which started with version 8.04, so it is not surprising that 7.10 works fine.  What's different about your situation is the error messages you get when you are in busybox mode.

You said you unplugged the USB devices; have you tried unplugging the hard drive?

Also, the pop-up message you noted is normal.  It's from the BIOS, telling you that RAID mode is active.

---

### Post by 888gavin on 2008-12-23
[IMG]http://gavinscorner.com/files/images/UbuntuErrorSansHD.jpg[/IMG]

It seems that even when I disconnect the hard drive, I get the exact same error! Is this helpful at all, or does it further deepen the mystery?

Just to be sure I fully disconnected the hard drive (even though there were absolutely no wires going into it at all), I restarted the computer to see if it would boot into Windows, and it didn't, it skipped right to the CD drive.

What could the problem be?

---

### Post by 888gavin on 2008-12-23
I am now writing this message from the Ubuntu 8.10 Live CD. I used UNetbootin to write the CD to a USB flash drive, and I guess it bypassed the kernel's problems with the CD drive. So I guess I'm going to be able to install Ubuntu on my computer now, but I'm not so sure about doing that. Is the computer going to boot Ubuntu when it's installed on the hard disk? Is my CD drive going to work once Ubuntu's installed?

---

### Post by gbrainin on 2008-12-23
Well, I'm still guessing, but I have to think that the problem is with the CD drive.  I'm not sure what on earth that could be, but you seem to have eliminated the other possibilities I can think of.

If your system runs from the flash drive, it will almost certainly run from the hard drive (allowing for the IDE/RAID issue previously discussed).  Good luck!

---

### Post by 888gavin on 2008-12-24
I've successfully installed Ubuntu Intrepid (8.10) onto my computer. Everything works fine, it boots up perfectly.

Once again, I'll run through the process that I went through:

I used UNetbootin to put the contents of the Live CD onto a 1 GB flash drive, and booted the computer with it. It worked fine. To test to see if my CD drive was working, I popped in an audio CD and it ran fine. I backed up my personal files onto an external hard drive, switched the SATA mode to RAID in the BIOS, then formatted the hard drive and installed Ubuntu.

I would like to extend a big thanks over to gbrainin, howefield, armandh, and Zorix from #ubuntu on irc.igs.ca (EFnet). Without you, I would not be able to enjoy the wonder of Ubuntu. Thank you all so much!

888gavin

---

### Post by armandh on 2008-12-24
in retrospect

either the cd drive is bad or it is on the secondary ide line or some other unknown interface problem

glad the usb boot/install solved the problem.

---


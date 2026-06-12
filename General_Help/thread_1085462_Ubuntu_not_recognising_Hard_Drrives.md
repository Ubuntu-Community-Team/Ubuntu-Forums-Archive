---
title: "Ubuntu not recognising Hard Drrives"
date: 2009-03-03
forum: General Help
---

### Post by Admiral Yi on 2009-03-03
Hello,
Im my computer I have two hard drives, one 80GB with windows xp installed on it, one 1TB with nothing installed on it. Both hard drvies are SATA. When I try to install Ubuntu (Hardy)it skips the usual guided/manual install screen and goes straight to the partitioner without even recognising the drives. I have a live CD of Gparted and that recognises both drives. When I formated the 1TB drive to NTFS with Gparted windows was recognising it too. I have since tried to format the drive wit a linux swap, root and home partition, but Ubuntu still won't recognise it. When I had a USB plugged in, the Ubuntu installer was finding that as a drive. 

Anyone able to help? Somebody told me it's a bug with the Kernel in Hardy but I was able to install with Wubi on my last computer and that worked fine.

---

### Post by civillian on 2009-03-03
To make sure its not the disc image you have used, you could try downloading the same image from a different location. 
If it's an error with hardy you might want to try installing Intrepid (the most recent release), or alternatively if you want hardy for the long term support, you could try installing from the alternate install CD which might work? 

Its possible that it worked in wubi because it runs inside a virtual machine with windows as the host, so the vm will pick up the same hardware as the host (although I don't know much about how wubi operates).

Hope this helps!

---

### Post by Admiral Yi on 2009-03-03
I actually have two Hardy cds, one I amde myself and one I didn't neither works.

---

### Post by Slim Odds on 2009-03-03
> **Admiral Yi said:**
> I actually have two Hardy cds, one I amde myself and one I didn't neither works.

But, did you actually **test** the CD's?

The have an integrity check in the menu when you start the disk.

---

### Post by civillian on 2009-03-03
Have you tried installing 8.10? 
It might pick up your drives...

---

### Post by Admiral Yi on 2009-03-04
> But, did you actually test the CD's?

The have an integrity check in the menu when you start the disk.

Tested both disks and they're fine

I will try Intrepid, but I would prefer to use hardy because of the longer support. The comps not working at the moment, but as soon as I get it fixed i'll try 8.10 and also Fedora 10.

---

### Post by Admiral Yi on 2009-03-04
Anyone have a solution to this problem?

---

### Post by civillian on 2009-03-04
Not as of yet. Do you have a status update? (did you try alternate etc?)
(if you need want a good stopgap distro, I'd suggest knoppix, you can run it from a cd :))

---

### Post by stchman on 2009-03-04
What kind of computers are they?  What is the chipset?  They might have newer SATA comtrollers that are not yet supported by Ubuntu.

---

### Post by Therion on 2009-03-04
This sounds like the EXACT same problem I had a while ago, and it about drove me nuts.

Let me make sure I understand the sit though...

Two, internal, SATA drives: an 80GB drive with a Windows install and a 1TB drive NTFS partition only.  Correct so far?

And then you go to install Ubuntu but it only recognizes one installed drive.  Which drive is it recognizing, the 80GB/Windows drive or the 1TB blank drive?

Also, what is it you want to do?  Dual boot Windows/Ubuntu on the 80 gigger, dual-drive/dual boot or wipe Windows and have Ubuntu as your sole OS or something else altogether?

---

### Post by Admiral Yi on 2009-03-04
> 
And then you go to install Ubuntu but it only recognizes one installed drive. Which drive is it recognizing, the 80GB/Windows drive or the 1TB blank drive?

Also, what is it you want to do? Dual boot Windows/Ubuntu on the 80 gigger, dual-drive/dual boot or wipe Windows and have Ubuntu as your sole OS or something else altogether?

Ubuntu doesn't recognise either of the drives. When I put a USB memory stick in it found that, but niether of the sata drives. I was trying to install onto the 1TB drive.

I tried Fedora 10, but it wouldn't actually start. Just got the loader for about 10 mins. Also tried anouther distro I use called Goblinx. That booted but the installer wouldn't start. By Gparted live cd starts and recognises both drives.

As for hardware, I have:
-Intel Core 2 quad processor 2.4ghz
-MSI G45M-FIDR Intel G45 (Socket 775) PCI-Express DDR2 Motherboard ([http://www.novatech.co.uk/novatech/specpage.html?MSI-G45MFI]("http://www.novatech.co.uk/novatech/specpage.html?MSI-G45MFI"))

I have a Nvida Geforce 7200 LE (I think) graphics card, but I had that in my old computer and Ubuntu worked fine with that.

Hope thats enough info.

---

### Post by Admiral Yi on 2009-03-05
I have tried Zenwalk Linux. It has a version of Gparted, and when I open that  it can see both hard drives. The ZenInstaller starts and finds the hard drvies. Looks like the problem isn't with all Linux distros.

---

### Post by Admiral Yi on 2009-03-05
Bump

Tried opensolaris (which is basically the same as Ubuntu but without the repositories) and the installer for that worked and found both hard drives.

---

### Post by Admiral Yi on 2009-03-06
Bump

---


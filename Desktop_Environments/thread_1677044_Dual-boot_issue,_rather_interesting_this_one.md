---
title: "Dual-boot issue, rather interesting this one"
date: 2011-01-28
forum: Desktop Environments
---

### Post by capnnismo on 2011-01-28
Hello Ubuntu Forums!

I was hoping to avoid having to make an account here (not that I don't like you guys) and just get along with using search to solve all my problems. That's worked for me for some time now, but now that I've installed Ubuntu on my new desktop alongside Windows 7 (each OS is on a separate drive), I seem to have run into a small problem.

Let me start with what I did:
- Unplugged 1TB drive from the PSU, BIOS was not seeing my formatted (and thus empty) 500GB drive and I couldn't put it into the boot order at all with the 1TB turned on.
- Loaded up the boot CD and was able to install Ubuntu 10.1 on my 500GB drive.
- Did a bit of configuring, shut my PC off and plugged my 1TB (with Windows 7) drive back in. I tried to see if I could now see my Ubuntu drive in BIOS but nothing is there - just the Windows drive is in the list of available drives to boot from (along with DVD-ROM and USB).

This is where I've run into my problem. What I want is to have a nice GRUB boot menu at the start like any other dual-boot system but just have the two operating systems on separate drives altogether. I did it this way because I was having issues with the advanced partition menu on the boot CD so just went ahead and followed the KISS method by unplugging the Windows drive.

I was told by a friend that if I put my Ubuntu drive into the first position in my boot order and the Windows drive in the second, then I could boot into Ubuntu and run a GRUB update command (he told me to google it) and that would create the necessary GRUB that had the entries for Windows 7 and Ubuntu.

Both operating systems are 64-bit, I imagine that might make a difference in whatever help you guys can offer me. I love the hell out of both OS's and want to be able to use them interchangeably. I'm not an entire Linux newb, but I'm also not an advanced user at all, so please keep that in mind, some things I may need spelled out for me. ;)

Thanks for taking your time in reading this, hope you can help.

---

### Post by Canadianandertu on 2011-01-28
Uhhh... did you set the ubuntu partition to be bootable? What filesystem did you format it as? Are you sure you installed grub correctly? Did you just use ubuntu's automatic drive partitioning?

---

### Post by Rubi1200 on 2011-01-28
Hi and welcome to the forums capnnismo :-)

> I was told by a friend that if I put my Ubuntu drive into the first  position in my boot order and the Windows drive in the second, then I  could boot into Ubuntu and run a GRUB update command (he told me to  google it) and that would create the necessary GRUB that had the entries  for Windows 7 and Ubuntu.
Well, did you try this? What happened?

Here is what I recommend:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by capnnismo on 2011-01-28
Got it working.

The problem was that my boot order menu was only giving me the option of 3 potential boot devices and out of those 3, only ONE of them could be a HDD (ASUS motherboard). In another menu on the same page that I constantly overlooked, there was an option to specify the boot priority of the two hard drives. Changed them around and I went back to the main boot order menu (confused, yet?) and was now able to select the Ubuntu drive as an available device to boot from (but now the Windows HDD wasn't showing). Restarted the computer from BIOS and booted straight into Ubuntu. 

Went into the terminal and put in the command
```
sudo update-grub
```
and it found the Windows installation on the other drive. Restarted the computer and the Grub2 menu came up and gave me all of the boot options and Windows 7 was there. No worries now.

---

### Post by Rubi1200 on 2011-01-28
Excellent! Glad you got it sorted out and working.

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by capnnismo on 2011-01-28
Done ;)

---


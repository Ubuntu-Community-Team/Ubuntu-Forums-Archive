---
title: "Ubuntu on USB drive messed up. Plz Help!"
date: 2008-01-13
forum: Dell  Ubuntu Support
---

### Post by brysono on 2008-01-13
I have a Dell Inspiron 1520 running Windows Vista Business. 
I installed Ubuntu 7.10 on a 30 gb USB drive. The only problems I had with it was it didn't recognize my soundcard, which isn't really a problem since i'll eventually figure out how to get the correct driver.

Every time I booted the laptop it gave me a root menu to select which OS i wanted to use and defaulted to Ubuntu after ten seconds. The problem is that if the USB drive was not plugged in, my computer would display Error 21 and i was unable to boot Vista installed on the local drive. After fussing with the bios and realizing I really had no idea what I was doing, I decided to reformat the USB drive and check the forums for how to dual boot properly. But the drive would not show up in my computer. I eventually found it in device manager but the only things i could do with it were to delete the partitions. So I did thinking that might fix the problem of booting without the drive plugged in.

Now I'm second guessing that decision and I don't want to turn my computer off in case i still get the error 21 message and won't be able to boot anything at all since I no longer have ubuntu on the usb drive. 

So I guess my question is did deleting the partitions fix the booting problem or did I just make it worse?

---

### Post by TwoWordz on 2008-01-13
Ubuntu uses the grub bootloader which in your situation sits on the MBR of your laptop's hard drive. 

Why its doesn't work is because the grub menu file was on your usb HD. This is the menu you see when you boot your computer. 

Now if you want to repair your computer, you need to fix your MBR. On xp you could do that by booting the install cd and bringing up the recovery console. In the console you type fixmbr you reboot and you should be fine. 

I dont use vista but it should have something just like it. 

The other thing you could do is reinstall ubuntu on your usb drive and let it fix the problem.

You dont see your drive in windows because windows knows only two filesystems; fat and ntfs and ubuntu by default uses EXT3. 

Good luck, 

TW

---


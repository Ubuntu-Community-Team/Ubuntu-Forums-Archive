---
title: "Live CD Major problem"
date: 2009-02-10
forum: General Help
---

### Post by endor43 on 2009-02-10
Hello everyone,

I have a rather serious problem. The live cd will not boot to the gui.
I can select either Try without changes to your computer, or install ubuntu at the boot screen after booting cd, both of wich should take me to the gui, but instead it shows the loading ubuntu progress bar like normal then pauses for a long time and doesnt take me to a gui it takes me directly into the Ubuntu commandline, all-text mode. Im not stranger to it, but we're not family, so i dont really know how to execute gnome from the commandline as a workaround. Anyways im not asking how to do that. I am wondering what is wrong. Ive downloaded the iso from two different ubuntu mirrors, tried using two different brands of blank cds, and tried using them on two different computers. Its not me, and it seems like its the image itself, which by the way is 8.10 32-bit. I've always liked ubuntu but this is killing me. My ultimate goal is to just boot the live cd to GUI and use the usb creator to install persisent installation to my flash drive thats it. I also event tried installing ubunt through windows (horrible i know) and it installed, but when it booted to the local installation, it just gave me command line like the live cd, and i did not download the alternate text mode cd. ubuntu has always worked for me in the past including 8.04 and i would use that cd, but it doesnt have the usb creator, and i want 8.10 on my USBFFD.

Sorry for the length. Just trying to be thorough. Please help.

Thanks,
Thomas

---

### Post by photon_man62 on 2009-02-10
Why not just try downloading the image again if you suspect it's the image itself?

---

### Post by endor43 on 2009-02-10
If you read the above post, i did try downloading it again, in fact, from a different mirror at ubuntu just to make sure. Thanks anyways.

Someone please help,
Thomas

---

### Post by Yellow Pasque on 2009-02-10
Did you check the md5sum of the .iso before you burned? Also, you want to burn at low speed, preferably with DAO and verify integrity. Also, run the verify media option on the LiveCD to make sure.

If you do all of that and you're still having issues, try using safe graphics mode. If you still get dumped into a terminal, try to 'killall gdm' and then start gdm again (using gdm command).

---

### Post by endor43 on 2009-02-11
Md5sum is fine, and verified 100% successfull, no errors. But when i go to boot the cd it just goes to the commandline. I tried kill all gdm in regular user and root and they both say that it cant be stopped. then i try to run gdm anyways and it natuallry says its already runnning. How do i do the safe graphics mode in the live cd? thank you. Keep in mind, it is most likely not my pc because i tried it on another pc and it did the same thing. My computer has 4GB of ram and a intel quad core proc with dual Nvidia 8800gtx, 8.04 worked for me too.

Thank you again,
Thomas

---

### Post by endor43 on 2009-02-12
anyone?

---

### Post by endor43 on 2009-02-14
I still cant solve this

---

### Post by endor43 on 2009-02-16
I'd really appreciate some help

---

### Post by Yellow Pasque on 2009-02-18
The LiveCD has an option for modifying the kernel boot parameters. Change 'splash' to 'nosplash' and remove the 'quiet'. This will allow us to see the boot output.

---

### Post by endor43 on 2009-02-19
I have done this, and now i see boot output. unfortunately i didnt see anything irregular, But then again i might have missed it or not known it when i saw it. How will i be able to let you seee boot output?, is there a log stored somewhere?, i can install it so it will save things to ROM instead of ram and then pull it up that way from windows? Thats about all i can think of doing.

Thank you,
Thomas

---

### Post by Yellow Pasque on 2009-02-19
> How do i do the safe graphics mode in the live cd?
Press F4

If you get to a terminal, and you have a flash drive that you can mount, you could redirect the output to a file.
```
dmesg > /pathtoyourflashdrive/bootlog.txt
cat /var/log/Xorg.0.log > /pathtoyourflashdrive/xlog.txt
```

---


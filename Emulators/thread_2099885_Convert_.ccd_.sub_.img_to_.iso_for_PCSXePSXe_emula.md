---
title: "Convert .ccd .sub .img to .iso for PCSX/ePSXe emulators."
date: 2012-12-30
forum: Emulators
---

### Post by ntzrmtthihu777 on 2012-12-30
Ok, as any PSX emulator knows alot of PSX games come in the clonecd .ccd format. I am looking to convert these files into a .iso.

As the .ccd files work just fine with both ePSXe and PCSX you may ask, "Why?"
My answer: a matter of digital housekeeping. I doubt there will be any huge difference in filesize, but having a single .iso file is more appealing to me than 3 separate files. I currently have these files stored in separate directories under my ~/iso directory, eg
```
ls ~/iso/Breath_of_Fire_3/
breath of fire 3.ccd
breath of fire 3.img
breath of fire 3.sub

```What I have tryed:
ccd2iso breath of fire 3.img breath of fire 3.iso
acetoneiso's conversion tool
mounted the .img with acetone iso and copying the contents to a brasero project and making a .iso with that
All methods yield a .iso file which is unusable to either emulator

I am comfortable using either a terminal or gui program, in fact terminal is preferable so I can make a nautilus script to automate the process.

Thank you ubuntu collective :D

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Do you actually own the game? I'm going to assume you do because you certainly have files that come off of a legal rip...

From ePSXe's official site;

> **Ripping your game CD to ISO**
         

Gosh, these days we have like 500 GB, 800 GB, 1-5 TB hard drives!  You can totally rip all of your PSX games and barely put a dent in your  hard drive. PSX games run better & faster when you're running their  ISO. And now that smartphones and tablets are becoming more common,  you'll have no choice but to rip your games to play them on emulators on  mobile devices. So here's how you rip your game CD:
         

1. Download & install *ImgBurn*. You can download it [from its homepage]("http://www.imgburn.com/"), or download it [right here]("http://www.fantasyanime.com/emuhelp/SetupImgBurn2.5.0.0.exe") (it's 2 MB).
         

2. Upon opening ImgBurn, click Create image file from disc, [as shown here]("http://www.fantasyanime.com/emuhelp/emuhelp_epsxe11.gif").
         

3. Make sure the proper source drive is set under "Source", then click click the "Read" icon - [as shown here]("http://www.fantasyanime.com/emuhelp/emuhelp_epsxe12.gif").


         4. That's it! Ripping your game CD will take maybe 20-30 minutes. And by default, ImgBurn will toss the BIN file (the ISO) into *Documents*.
         AcetoneISO is mostly for mounting, but see if you have this;

[IMG]https://lh3.googleusercontent.com/B3XNgU47_Z3aZ7oZnBL2TUwZNfYsUFlXRtIX5LCVO5bRBCm5Ph55dUO2cQWEvsqlGPjtJX3S1CSdX3fFXunHVrCZXw=s512[/IMG]

That is confirmed to be able to properly rip PS1 games.

OR you could try Brasero to rip the game. You can also use IMGburn/Alcohol120% through Wine, if they work. 

You can also check out this link; [http://forums.ngemu.com/showthread.php?t=100052](http://forums.ngemu.com/showthread.php?t=100052)

I know you said convert, but I don't think it is possible in Linux, and would probably corrupt your image anyway. It would be safer and quicker ripping your image yourself.

---

### Post by deadflowr on 2013-01-22
+1 for Brasero.
I've ripped several ps1 and ps2 games with it, and the only game that didn't has several bad sectors which are the bane of every time I reboot my system.(It's Tony Hawk Pro Skater2, which I like to play on occasion so I leave in the drive.)

Just open brasero, choose disk copy and change the output to image file. It'll create a .bin file, usually cd-something.toc.bin.
On first use you'll be prompted to install cdrdao.

---

### Post by ntzrmtthihu777 on 2013-01-23
Ah, Forgot about this thread, there were no reply for so long. I will give these options a try, thank you for your replies. Yes, I actually own the games, but the physical cd's are in a bad way and quite frequently don't work.

---

### Post by Lightning Dragon on 2013-01-24
Hello,

If there is a problem with the physical discs ripping them will also have problems the physical discs had. I'm afraid you are going to have to purchase the games again to be able to rip them without any problems.

---

### Post by ntzrmtthihu777 on 2013-01-24
Question:
What is the legal status of a downloaded rip that you actually physically own _but_ the physical medium is beyond usability?

---

### Post by Lightning Dragon on 2013-01-25
Hello,

I am pretty sure that if your original source is unplayable/broken, it is like not owning it. You would need another copy of the game.

---

### Post by ntzrmtthihu777 on 2013-01-26
> **Lightning Dragon said:**
> Hello,

I am pretty sure that if your original source is unplayable/broken, it is like not owning it. You would need another copy of the game.
Haha, just my luck. This is why I wish the major consoles would switch back to cartridge based games. With today's tech you could create huge games on cartridge, just look at the newer pokemon games. With cartridges there is a greater durability; its so easy to scrag a disc, but find an old nes cart and you can be pretty sure it still works.

---


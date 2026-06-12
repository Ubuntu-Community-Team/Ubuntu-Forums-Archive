---
title: "How To: Uninstall Ubuntu"
date: 2006-01-06
forum: General Help
---

### Post by scole on 2006-01-06
Well, not many of you would want to do this but about a week ago I was reading a forum post that had someone ask how do you uninstall Ubuntu? I was left wondering because so few people would want to do it. But, I found an easier way than deleting partitions blindly and rewriting a windows mbr which is no fun at all. To do this you need to be in windows :( (its an exe) download this file [http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html) You do not need to buy it. Just scroll to the bottom to download from their link. When downloaded run the exe in there. You then may make a bootable floppy or cd your choice. This puts the program on you choice of media so your ready to go. (the cd option makes a cd .iso so you will need a program to burn it.) Both the floppy and cd contain the same program. Next you will restart your computer with the cd or floppy in the drive. Once you boot into the program do not install it to your HDD. Just click cancel to just run it off the cd or floppy. Then go to partion work. Click the oval on the left side of the window (yes you can use your mouse!) to go to your primary hdd. Select and delete every partition except for your standard windows partition. Now you should have a formatless partion that says free space after it. Then select your windows partion and click resize. It will run an error check which may take a while depending on your partion size. Once that finishes type in the largest size in the prompt unless you have other plans for some of that space :) . Once you do that it will allocate all that space back to your primary partion. Next, if you installed grub the bootloader you will need to reset you mbr or else you can't boot up because grub will crash. To do this select you windows partion go to view mbr on the left. When in there select your windows partion and click std mbr. This will take grub off and set your mbr back to the way it was before. Click apply and the changes will be made. Then eject your media and use the file option at the top left to reboot. Your computer should restart normally into windows :) . You just uninstalled Ubuntu. This saved you so much pain. You would have had to rewrite the mbr by hand to do this the other way and then have had to figure out a way to delete the linux partions. It is not a bad idea to back your stuff up before doing this because stuff happens and you don;t wanna lose everything. Hope this helps you. :)

---

### Post by inigmatus on 2006-01-10
scole,

That is by far the simplest way to remove uninstall delete ubuntu and grub on a dual boot system. I have two hard drives, my primary is XP, and as a silent supporter of the linux revolution (but never a player until tonight) I ventured to install ubuntu on my second hard drive, and as a result I also installed grub as the bootloader to my master boot record. Needless to say, newb is me, and I formatted my linux partitions without enough space for the installer to complete ubuntu on restart. Doh.

So it was only after I found a simple way to uninstall (and only after I was assured that I could uninstall if need be) that I was willing to push ubuntu on my baby (comp). I didn't think I'd need it, but it came in handy. Its 1am, and I need peace of mind to sleep. So with your simple instructions to use BootIT NG, delete the partitions, and then view the MBR of the windows partition, and then hit std mbr, and then restart and breathe again, was I able to go to sleep peacefully to dream about how I would tackle a new ubuntu install in the morning, and setting up dual booting back to Windows to play Planetside.

I have my Windows XP back and an empty second hard drive to play with again. No more ubuntu, and no more grub loader. Your instructions work very well. My computer plays along now as if nothing ever happened - and that is something I know some reading this will breathe a sigh of relief about.

There really are good reasons to uninstall, if not for the simple fact that there is a major attraction to us on-the-fence-Linux-explorers in having the peace of mind that our Windows-security-blanket is still there to retreat to with instructions such as yours.

But there are other good reasons to uninstall, like those of us who really enjoy making calculated mistakes with our first custom installs of ubuntu and a tip toeing around the land of Linux, though we may hang on to Windows for our gaming addictions, the easier it seems for us to give up and go home, the more likely we are to stay and continue exploring to the point that burned bridges become a passion rather than a fear.

In plain english, um, thanks for the info. You rock. I'll be reinstalling ubuntu after I get a well-deserved rest, and thankfully no nightmares.  

They should include your uninstall tip in the wiki.

---

### Post by inigmatus on 2006-01-16
Anyone included this in the wiki yet?

---

### Post by scole on 2006-01-24
Also never try to do this while you put windows into hibernation mode. You will corrupt all of your files.

---

### Post by Mustard on 2006-01-25
Handy little HOW TO. :)  Thanks.

---

### Post by bodean on 2006-05-07
Will partition magic do the same thing?

---

### Post by elamericano on 2006-05-07
Partition Magic won't rewrite the MBR, but I still think that Patition Magic + Windows CD is the easiest uninstall. In fact, if you install your bootloader to the partition header instead of the MBR, Partition Magic would be all you need. However, it isn't a free program.

In the Linux universe, maybe GParted is the solution, but I haven't used it, so I can't recommend it.

---

### Post by elamericano on 2006-05-07
Holy Mackeral, I just saw their screenshots an it looks like a complete Partition Magic rip-off... um, I mean clone. This is probably a good thing for us.

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

They even have a small (~30MB) LiveCD (wow, I could boot that from a cheap USB drive too)

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by cwbn on 2008-05-28
I installed Unbuntu version7.10 for PC on my Volicity Micro Laptop.  once it restarted I could not start up window vista  any more did it delete I did not ask me to set up a boot camp.

Please help 

My email is 
[email]ceo@cwbn.tv[/email]

I live in DC and I have a paper on my PC I have it backed up but need to access window to get it but would like to not delete any window files.

---

### Post by tsb08 on 2008-06-04
Hey, 
     Well i downloaded the bootitng.zip file and I can't run the exe. I also downloaded the "image for windows" file and vista ran that exe well.
     I don't know if I need to put the bootitng.zip file on a cd or put something from the image for windows file on a disc. Could someone please help me out? 
     I'm running out of room on my current partition and plan on re-installing ubuntu when i can make more room or fix my other computer.

---

### Post by apche93 on 2008-06-04
ok, well i successfully restored MBR.  But for somereason i cant increase my partition.  I deleted my ubuntu partition (with swap), and i cant seem to increase any of my ntfs partitions.  Does anyone know why??

---

### Post by stuckwithwindows on 2008-06-06
Wow this seems kinda hard but the easiest thing to uninstall. I hope i do not mess up my computer. Coul I use my Windows CD to partition it?

---

### Post by dsnow27 on 2008-06-07
this is amazing. most helpful thread here, the REMOVAL of the problematic ubuntu 8.04 on my hp pavillion with vista without any more frustrations

---

### Post by gsss124 on 2008-06-10
Thanx! I have gutsy 7.10 on a small ~4 gb VERY old HDD, i once removed it and saw that windows did not boot! Now I have this easier way, thanks. why is GRUB so dominating?

---

### Post by Lowcountry on 2008-06-23
> **scole said:**
> Well, not many of you would want to do this but about a week ago I was reading a forum post that had someone ask how do you uninstall Ubuntu? I was left wondering because so few people would want to do it. But, I found an easier way than deleting partitions blindly and rewriting a windows mbr which is no fun at all. To do this you need to be in windows :( (its an exe) download this file [http://www.terabyteunlimited.com/bootitng.html](http://www.terabyteunlimited.com/bootitng.html) You do not need to buy it. Just scroll to the bottom to download from their link. When downloaded run the exe in there. You then may make a bootable floppy or cd your choice. This puts the program on you choice of media so your ready to go. (the cd option makes a cd .iso so you will need a program to burn it.) Both the floppy and cd contain the same program. Next you will restart your computer with the cd or floppy in the drive. Once you boot into the program do not install it to your HDD. Just click cancel to just run it off the cd or floppy. Then go to partion work. Click the oval on the left side of the window (yes you can use your mouse!) to go to your primary hdd. Select and delete every partition except for your standard windows partition. Now you should have a formatless partion that says free space after it. Then select your windows partion and click resize. It will run an error check which may take a while depending on your partion size. Once that finishes type in the largest size in the prompt unless you have other plans for some of that space :) . Once you do that it will allocate all that space back to your primary partion. Next, if you installed grub the bootloader you will need to reset you mbr or else you can't boot up because grub will crash. To do this select you windows partion go to view mbr on the left. When in there select your windows partion and click std mbr. This will take grub off and set your mbr back to the way it was before. Click apply and the changes will be made. Then eject your media and use the file option at the top left to reboot. Your computer should restart normally into windows :) . You just uninstalled Ubuntu. This saved you so much pain. You would have had to rewrite the mbr by hand to do this the other way and then have had to figure out a way to delete the linux partions. It is not a bad idea to back your stuff up before doing this because stuff happens and you don;t wanna lose everything. Hope this helps you. :)

WOW!! That was easy!  Thanks SO much!

(I'm not giving up on Ubuntu...I'm giving my parents my old dual-boot laptop and they only wanted Windows.  I was just going to leave as is, but this really made it easy.)

---


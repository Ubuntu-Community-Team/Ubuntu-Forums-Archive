---
title: "Installing Windows XP on Ubuntu"
date: 2008-12-30
forum: General Help
---

### Post by itr632 on 2008-12-30
I just got a Dell Mini 9 for christmas and it has Ubuntu preloaded on it.  I am trying to install my windows system via a bootable disc.  After some research I found that Ubuntu does not recognize .exe files so it cannot install this for me.  I called Dell and they will not help me.  Anyone know how I could install XP?  I am stumped, not a PC expert but I have a little knowledge.  Thanks to anyone that can help.

---

### Post by eBoxNet on 2008-12-30
What do you wanna do? create a dual boot system? or install windows in a Virtual Machine inside your ubuntu machine? or maybe completely remove ubuntu and install win ?

---

### Post by itr632 on 2008-12-30
> **eBoxNet said:**
> What do you wanna do? create a dual boot system? or install windows in a Virtual Machine inside your ubuntu machine? or maybe completely remove ubuntu and install win ?

I want to completely remove ubuntu and install Windows XP.  I dont really like Ubuntu and it just isnt practical for what I do.  This was a gift, and my wife did not realize she was ordering a machine with a different OS than windows.

---

### Post by itr632 on 2008-12-30
bump

---

### Post by sonik88 on 2008-12-30
Insert the windows os in the disk drive, configure bios to boot from cd, then boot from cd, enter windows installation menu and when asked format the entire hdd using the NTFS filesystem. Then follow the instructions and you should be ready!

Hope I helped

---

### Post by bumanie on 2008-12-30
Assuming you have a xp installation disk - just boot with it and at the partitioning stage get it to install the ntfs filesystem over the present ubuntu installation - xp will probably see the ext3 filesystem as a 'unknown'. xp will overwrite any grub references. Unfortuante you are not prepared to try ubuntu for a while. You will have to search for xp drivers, because drivers are built in to the linux kernel - you won't have an xp drivers disk - check that xp drivers are available for the motherboard first.

---

### Post by Alvinius on 2008-12-30
What is it you want to do?Maybe we can help make Ubuntu "practical' for what you want to do

---

### Post by eBoxNet on 2008-12-30
> **alvinius said:**
> what is it you want to do?maybe we can help make ubuntu "practical' for what you want to do

+1

---

### Post by kokkus on 2008-12-30
It sounds like you don't know that much about PC, so I would ask someone to do this if I were you.
First of all, Ubuntu is an operating system, and so is windows.
You say you wanna remove ubuntu and just have windows.
Since you already have the ubuntu on CD I would have them both, but ok.
The first thing you need to do is to remove the Linux partition by using the ubuntu CD, then pop in the windows cd and boot it in startup to start the windows installation.

---

### Post by eBoxNet on 2008-12-30
i think his laptop (netbook) doesn't have a cd-rom drive so he may need to create a usb boot disk,in the other he should do the same for windows,or he can install windows over network if he has access to a working windows machine.

of course you can use an external cd/dvd-drive (only if you don't gave an optical drive of course)

---

### Post by kokkus on 2008-12-30
Or he can simply keep Linux and install Wine.
itr632, since you don't know much about PC and how to do this things I would go for that solution. 
Wine is a program you can use to run many of your favourite windows programs on your Linux machine.
As you can see, Ubuntu has very good support forums and you can always come here if you need some help.
But it's your PC and your choice.

Good luck:)

---

### Post by albinootje on 2008-12-30
> **itr632 said:**
> I want to completely remove ubuntu and install Windows XP.  I dont really like Ubuntu and it just isnt practical for what I do.  This was a gift, and my wife did not realize she was ordering a machine with a different OS than windows.

Check : [http://mydellmini.com/forum/](http://mydellmini.com/forum/)

---

### Post by itr632 on 2008-12-30
maybe this will help:

So I got a Mini 9 for Xmas and my wife ordered it with Ubuntu. I have been trying to install Windows XP for the last couple of days and I want to throw this thing into a wall. I have the DVD/CD drive so I did what I have done any other time I install an O/S and set the boot sequence to start from the CD. Install Windows bootable CD and nothing. Restart about 1000 times and it will not read it. Put a few other CD's in the player just to make sure it is working properly, and they all work fine. Try another windows installation disk and restart machine, nothing. Put windows bootable disc in another machine, and auto-run starts (so I know the disc is ok). I decide to go into Ubuntu's version of my computer and click on the disc, then I click on setup.exe and it will not open it. I call Dell and sit on hold for 1.5 hours and 4 transfers. Finally get a technician that informed me that I had to install the Ubuntu installation disc that came with the Mini and then Re-format the HD, then install windows. I get home and try this, but all that disc will let me do is re-install Ubunto. My frustration level was starting to peak so I decided to drink a beer and play rock band 3. I call Dell back sit on hold for another hour and the technician explains to me Ubuntu will not read a .exe file which explains why it couldnt read the windows disc. She also tells me she cannot help me install Windows since my machine came with Ubuntu. She informs me that the Ubuntu disc I have only lets you install it and I would need the disc that would give me the option to re-format the drive and I could go from there, but I would have to order it from the Ubuntu website. I went there and downloaded the latest version of Ubuntu (8.10 I think). I put that on a disc and proceeded to try and re-format the drive and install windows. It did take me to a screen to partition the drive, but I wasnt sure how to configure this to run Windows and I just went through it. It ended up just installing 8.10 and I am back to where I started. Can someone PLEASE help me??!!

---

### Post by ajcham on 2008-12-30
Boot from the 8.10 CD, and get onto the Live Ubuntu desktop.  Go to System » Administration » Partion Editor.  Use this to delete all partitions - you don't need to use Ubuntu to format the drive as Windows will do this (simple enough, just select the partition and click the delete icon in the toolbar).

Shut down, and then try booting from the Windows disc and you should be able to install.  Good luck, and if you ever decide to give Ubuntu another try, remember how helpful us guys in the forums have been! ;)

---

### Post by GuitarRocker2562 on 2008-12-30
Okay, when you start your mini, press O for options, and make sure the CD drive is plugged into the computer, turned on, and has the XP disk in it. Now, select boot from CD/DVD drive, and the XP installer should begin, from there install as normal, and when it asks you the drive to install to, select the unknown partition and format it as NTFS.

---

### Post by itr632 on 2008-12-31
> **ajcham said:**
> Boot from the 8.10 CD, and get onto the Live Ubuntu desktop.  Go to System » Administration » Partion Editor.  Use this to delete all partitions - you don't need to use Ubuntu to format the drive as Windows will do this (simple enough, just select the partition and click the delete icon in the toolbar).

Shut down, and then try booting from the Windows disc and you should be able to install.  Good luck, and if you ever decide to give Ubuntu another try, remember how helpful us guys in the forums have been! ;)


There is no option for Partition Editor when I go into System -> Administration....  Is it under another option?

---

### Post by ajcham on 2008-12-31
> **itr632 said:**
> There is no option for Partition Editor when I go into System -> Administration....  Is it under another option?

Odd… that's right where it should be - I've just booted my live disc and confirmed it.

Never mind, try running the command directly by pressing Alt+F2 and entering the following in the run dialog
```
gksu /usr/sbin/gparted
```

---

### Post by itr632 on 2008-12-31
Still didnt work and i got an error 22 message and something else.  I just decided to order a bigger HD and hopefully be able to load XP on there, thanks again for your help guys.  I might be back soon ;)

---

### Post by sovietdoughnut on 2008-12-31
> **itr632 said:**
> Still didnt work and i got an error 22 message and something else.  I just decided to order a bigger HD and hopefully be able to load XP on there, thanks again for your help guys.  I might be back soon ;)

we hope you do come back from the dark side. like others have said, don't forget how helpful and prompt to reply we have been -- and that was trying to help you ditch ubuntu. just imagine how helpful we are when you're trying to keep it ;)

---


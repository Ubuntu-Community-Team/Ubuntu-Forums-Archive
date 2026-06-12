---
title: "[SOLVED] Gutsy doesn't read / mount PSX CDs"
date: 2008-05-10
forum: Gaming &amp; Leisure
---

### Post by Devi 710 on 2008-05-10
Hello everyone,

I recently did a fresh install of Gutsy (Hardy was a little too buggy for me) and tried to get ePSXe working again. I installed it the same as before as per this thread: 

[How to Install ePSXe]("http://ubuntuforums.org/showthread.php?t=550304&highlight=gutsy+can%27t+read+psx+cd")

It will play disk images fine (bin, img, iso, files). But when I put a PSX CD in, it doesn't show up on my desktop or under the 'Computer' at all.

If I set Removable Drives to "Browse removable media when inserted" a window will pop up at "**/media/cdrom/**" but it still doesn't show up on my desktop or under 'Computer'. Like the CD isn't there at all.

Normal data CDs work fine. I have 2 drives. One CD RW, one DVD/CD RW. Same problem with both.

Any ideas? Did I need to install some package so Gutsy can recognize PSX disks?

Thanks

---

### Post by Devi 710 on 2008-05-10
My error message if it helps:

 * Init internal cdrom ... ok
CD read toc header failed (25)
 * First/Last track: 0 1
 * Track 1: CD get track start failed (25)
 (DATA) - Start 0: (244,89,237)
CD(0,2,16) read ioctl failed (25)
CD(22,20,2) read ioctl failed (25)
CD(22,20,3) read ioctl failed (25)
 * NTSC cdrom detected.
 * Init gpu[0][libgpuPeteMesaGL.so.1.0.76]
NVIDIA Corporation
                  GeForce 6200 A-LE/AGP/SSE/3DNOW!
                                                   * Open gpu[0]
 * Init spu[0][libspuPeopsOSS.so.1.0.9]
 * Open spu[0]
padJoy: cannot open cfg/padJoy.cfg * Init pad[0][libpadJoy-0.8.so]
padJoy: could not open /dev/input/js0
                                      * Open pad[0]
CD(0,2,16) read ioctl failed (25)
CD(0,2,0) read ioctl failed (25)

---

### Post by acoustibop on 2008-05-10
I get the same behaviour as far as Ubuntu's recognising Playstation CDs, Devi 710, but I think this may be due to their non-standard format rather than any shortcomings of the operating system.

However, I find that my emulator of preference, [pSX emulator]("http://http://psxemulator.gazaxian.com/"), has no problems reading Playstation CDs directly and, of course it's a far better emulator than ePSXe - in particular, no plugins to worry about! ;)

---

### Post by Devi 710 on 2008-05-10
Thanks for the response.

I've used the pSX Emulator before as well. Very solid and everything works, but you can't play games in a higher resolution with it :( It was always my backup emu. But I will install it again and see if it can read the PSX CDs.

The thing is, in my previous Gutsy install the PSX disks would mount fine and I could use them in ePSXe. I would make disk images of the CDs, but since they don't show up on my desktop (don't mount) I can't.

---

### Post by acoustibop on 2008-05-11
Actually, in the Linux version of pSX, in fullscreen mode it outputs at the desktop resolution.  Try doing a screenshot of a game in fullscreen...

The thing is, I know that pSX doesn't mount pSX CDs: it reads the drive as a raw device, and I would suspect any Playstation emulator or plugin capable of reading CDs directly would have to do the same thing.

**Edit:** I just tried mounting a Playstation CD ("sudo mount -t iso9660 /dev/<raw device> /media/<cd mount folder>" where /dev/<raw device> is the location of your drive and /media/<cd mount folder> a folder you create to mount your CD in) and it worked fine.  A "CD-ROM Disc" icon appeared on the desktop and I could browse the CD.  However, this is useless for playing the CD in an emulator, as if I try to run it as an image, it doesn't work (I get the black Playstation screen that indicates this is a non-valid disc) and, of course, if I run it as a CD pSX simply runs it directly from the device, bypassing the mounted image.

---

### Post by Devi 710 on 2008-05-11
Thanks for all the help!

I installed pSX and it read the psx CDs no problem. No plugins, everything running from the start. I guess the psx CDs never really mount and are just read from the device like you said. And this must have been what was happening in my previous Gutsy installation. 

The graphics are still not nearly as sharp and crisp as they are in ePSXe though. I did get ePSXe to run from the CD - I changed it to /dev/cdrom not /media/cdrom. I thought I already tried it but perhpas I tried /dev/cdrom0 or /dev/cdrom1. I don't know any way to list all my devices in my system (like fdisk -l or something in Terminal) to find this info.

I tried to do a few screenshots to compare the graphics, but the pSX one looks stretched, so the comparison is off. Anyway:

pSX

[http://i54.photobucket.com/albums/g106/klusacek/Pics%20For%20Posting/crash2_pSX.png](http://i54.photobucket.com/albums/g106/klusacek/Pics%20For%20Posting/crash2_pSX.png)

ePSXe

[http://i54.photobucket.com/albums/g106/klusacek/Pics%20For%20Posting/crash_epsxe.jpg](http://i54.photobucket.com/albums/g106/klusacek/Pics%20For%20Posting/crash_epsxe.jpg)

Thanks again!

---

### Post by acoustibop on 2008-05-11
What aspect ratio is your monitor, Devi 710? It's a good idea to set the appropriate ratio on the Graphics tab.

The thing is, although the video from plugin-based emulators often looks more impressive, pSX is much more accurate - if it doesn't always look so pretty, that's because the game actually looks that way.  For playing games, I'd rather have accurate than pretty any day. ;)

---

### Post by Devi 710 on 2008-05-14
1280 x 1024

I had the Graphics tab at Auto, probably why the screenshot looked wrong (on my computer it was fine)

And you are right, pSX is an accurate emulation. And a solid easy to use emu. I just love being able to play old school ps1 games with enhanced graphics (and being able to save when ever I want) :) I guess I am a sucker for eye candy... but game play always comes first.

Thanks for all the input.

---

### Post by acoustibop on 2008-05-14
Actually, you can make save states in pSX as well, Devi 710 - F6 to F10 to save in slots 1 to 5 respectively, and F1 to F5 to reload those slots.  You can do the same on the Quicksave menu, or make manual save states (and reload them) from File -> Save state and -> Load state.

However don't use save states exclusively.  Errors tend to occur when emulating a game (in fact, the same happens on a Playstation, but is not usually seen as there are no save states to facilitate playing that long without saving) and eventually accumulate to the point where they will cause glitches in the game and eventually crash it.  Making a memory card save strips away those errors, so that when you reload from that save, you have a clean game again.

Save states, however, are a 'snapshot' of the game at that point, and include any errors that may have occurred.  So, when you reload from a save state, you reload any errors that may be present - effectively, it's like playing continuously without saving and reloading (to and from a memory card).

A good rule of thumb is to use save states as much as you like in a playing session, but always save to a memory card to end a session, and always start the next session by reloading from that save.

---


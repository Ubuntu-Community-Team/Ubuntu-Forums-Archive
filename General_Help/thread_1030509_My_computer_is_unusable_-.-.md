---
title: "My computer is unusable -.-"
date: 2009-01-04
forum: General Help
---

### Post by iPodVision on 2009-01-04
This is the wrong section probably, but I'm freaking out. I used partition manager to create a new partition for ubuntu, accidently selected the wrong thing. Now I can't use ubuntu because it was inside of windows, and I can't use windows at all ethier. Hitting f11 or f12 etc at bootup doesnt bring up recovery files. Please help!

---

### Post by iPodVision on 2009-01-04
Bump please help!

---

### Post by stretch427 on 2009-01-04
Can You get into the grub menu? 

Try F8  and or Esc,

---

### Post by iPodVision on 2009-01-04
> **stretch427 said:**
> Can You get into the grub menu? 

Try F8  and or Esc,

Ok ill try, ill take pictures also, so hold up for those.

---

### Post by caljohnsmith on 2009-01-04
Do you have a Live CD you can boot? If so, how about doing that, open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by iPodVision on 2009-01-04
Heres what happens:

When I try to open windows:

[IMG]http://i42.tinypic.com/ixwaiu.jpg[/IMG]


What happens when I try to open ubuntu:

[IMG]http://i42.tinypic.com/140huhi.jpg[/IMG]


Whats happens when I press ESC:

[IMG]http://i40.tinypic.com/2hqtixe.jpg[/IMG]


What happens when I goto windows memory diagnostic:

[IMG]http://i44.tinypic.com/b8ql4g.jpg[/IMG]

HELLLP!

---

### Post by iPodVision on 2009-01-04
No I don't have a live cd =/, I used wubi, thats why I was trying to make a new partition to move ubuntu to it and delete windows. I just made a new partition and exited, tryed to boot up windows and it jacked up. I was told I was suppose to make the partition like ext3 I made it like ext2 idk if that was the prob.

---

### Post by iPodVision on 2009-01-04
Some one... I'm sorry for like quad posting but ill be in deep trouble if I don't get this fixed.

---

### Post by stretch427 on 2009-01-04
have you tried using gparted? Its a good partitioner program

as far as the picture goes.  you said you don't have a live cd, can't you just download one? sorry I'm not so firmiliar with Wubi.

---

### Post by Ahadiel on 2009-01-04
What partition manager did you use exactly? Did you shrink your Windows' partition first before creating a separate one for Ubuntu, or did you just delete your Windows' partition and create an ext2/3 partition?

---

### Post by iPodVision on 2009-01-04
> **Ahadiel said:**
> What partition manager did you use exactly? Did you shrink your Windows' partition first before creating a separate one for Ubuntu, or did you just delete your Windows' partition and create an ext2/3 partition?

I used this partition manager:

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

And I right clicked, hit new

Then shrunk it to the new one. =/

I never deleted windows because ubuntu was still in windows. But idk what happened

---

### Post by iPodVision on 2009-01-04
> **stretch427 said:**
> have you tried using gparted? Its a good partitioner program

as far as the picture goes.  you said you don't have a live cd, can't you just download one? sorry I'm not so firmiliar with Wubi.

I only have disks that are like 700 mb big, I always run short like 50 mb. =/

---

### Post by cptr13 on 2009-01-04
If you want to remove windows just do a full Ubuntu install.  Can you download and burn a livecd?

---

### Post by iPodVision on 2009-01-04
> **cptr13 said:**
> If you want to remove windows just do a full Ubuntu install.  Can you download and burn a livecd?

Look at my post above.

---

### Post by ajcham on 2009-01-04
> **iPodVision said:**
> I only have disks that are like 700 mb big, I always run short like 50 mb. =/

The Ubuntu ISO is under 700MB, your discs should be fine.  If the full image is not being burned, perhaps the software is at fault - try an alternative.

EDIT: If it's still no good (maybe you have 650MB discs rather than 700MB?) try the Xubuntu live disc - [http://www.xubuntu.org/get](http://www.xubuntu.org/get) - which is only 589MB.

---

### Post by iPodVision on 2009-01-04
> **ajcham said:**
> The Ubuntu ISO is under 700MB, your discs should be fine.  If the full image is not being burned, perhaps the software is at fault - try an alternative.

EDIT: If it's still no good (maybe you have 650MB discs rather than 700MB?) try the Xubuntu live disc - [http://www.xubuntu.org/get](http://www.xubuntu.org/get) - which is only 589MB.

No I just checked its 700 mb, let me download ubuntu, if that dont work xubuntu it is.

---

### Post by iPodVision on 2009-01-04
> **ajcham said:**
> The Ubuntu ISO is under 700MB, your discs should be fine.  If the full image is not being burned, perhaps the software is at fault - try an alternative.

EDIT: If it's still no good (maybe you have 650MB discs rather than 700MB?) try the Xubuntu live disc - [http://www.xubuntu.org/get](http://www.xubuntu.org/get) - which is only 589MB.

Yay! It burned to the disk! I have the disk in my laptop, now in the bios, which goes first, 2nd etc, I heard you have to edit something on this to boot from cd

[IMG]http://i40.tinypic.com/2hz1t7q.jpg[/IMG]

---

### Post by stretch427 on 2009-01-04
Well are you gonna loose important files if you do a reinstall? 

I know the admins are saying not to just say reinstall if we don't know what to say. So i'm at a loss sorry.

But as to 700MB you should be able to, all my disks are 700MB and they work just fine. Just look at it again. it looks the the ubuntu 8.10 are 699MB so give it a try and see what happens.

but I would say try Gparted first, you might be able to fix the partition.

---

### Post by stretch427 on 2009-01-04
Well are you gonna loose important files if you do a reinstall? 

I know the admins are saying not to just say reinstall if we don't know what to say. So i'm at a loss sorry.

But as to 700MB you should be able to, all my disks are 700MB and they work just fine. Just look at it again. it looks the the ubuntu 8.10 are 699MB so give it a try and see what happens.

but I would say try Gparted first, you might be able to fix the partition.

---

### Post by iPodVision on 2009-01-04
> **stretch427 said:**
> Well are you gonna loose important files if you do a reinstall? 

I know the admins are saying not to just say reinstall if we don't know what to say. So i'm at a loss sorry.

But as to 700MB you should be able to, all my disks are 700MB and they work just fine. Just look at it again. it looks the the ubuntu 8.10 are 699MB so give it a try and see what happens.

but I would say try Gparted first, you might be able to fix the partition.

I have nothing important, just tell me what order that bios goes in.

---

### Post by adult swim on 2009-01-04
if it is in the usb cd drive, select to boot from that (number 1 in your pic), if it is in the computers cd drive select internal optical drive (number 2 in you pic)

---

### Post by stretch427 on 2009-01-04
I usually have my CD/DVD drives booting first, because I do a lot of things that require BOOT's at CD. than so I'd go:

Internal Optical Drive
USB Flash Drive
Internal Hard Disk

Floppy and Network should probably always boot last. Not too many people I know use them that much. 

and so on. the other's aren't as important. Probably just your first three should do fine.

---

### Post by iPodVision on 2009-01-04
> **adult swim said:**
> if it is in the usb cd drive, select to boot from that (number 1 in your pic), if it is in the computers cd drive select internal optical drive (number 2 in you pic)
Uhh it still won't bootup cd? Its in my cd drive and I put internal opitcal drive as first.

---

### Post by adult swim on 2009-01-04
whenever you burned the cd, did you burn a data disk or burn an image?

---

### Post by albinootje on 2009-01-04
> **iPodVision said:**
> This is the wrong section probably, but I'm freaking out. I used partition manager to create a new partition for ubuntu, accidently selected the wrong thing. Now I can't use ubuntu because it was inside of windows, and I can't use windows at all ethier. Hitting f11 or f12 etc at bootup doesnt bring up recovery files. Please help!

If you can first make a complete image of your hard disk with CloneZilla or some other cloning software.

Then try testdisk from an Ubuntu installation cdrom using the live session :
```

sudo apt-get install testdisk

```
And read this :
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by iPodVision on 2009-01-04
I'm uplaoding a video to youtube of me showing the disc has ubuntu on it etc! And that it still wont load up!

---

### Post by Moop on 2009-01-04
> **adult swim said:**
> whenever you burned the cd, did you burn a data disk or burn an image? +1  

It won't boot if it's not burned as a image. What software did you use to burn it?

---

### Post by iPodVision on 2009-01-04
> **adult swim said:**
> whenever you burned the cd, did you burn a data disk or burn an image?

This is what it looks like. I'm uploading a vid to youtube of the whole thing but heres a screen shot.

[IMG]http://i43.tinypic.com/z24n4.jpg[/IMG]

Says iso image file.

---

### Post by iPodVision on 2009-01-04
> **Moop said:**
> +1  

It won't boot if it's not burned as a image. What software did you use to burn it?

Ooo...... Ok what should I use to burn as data disk.

---

### Post by ajcham on 2009-01-04
Yep, you need to burn as an image, which you've not done. You've just burned the image file to a cd, which is why it won't boot.

Try again with another disc, and look for the burn image option. Which software did you use?

---

### Post by abn91c on 2009-01-04
use this program from CNET to make you live cd its free/no limits: [http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html?tag=rtcol;reldl&cdlPid=10792184](http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html?tag=rtcol;reldl&cdlPid=10792184)

---

### Post by Ahadiel on 2009-01-04
There's also [http://www.imgburn.com/](http://www.imgburn.com/).

---

### Post by iPodVision on 2009-01-04
> **ajcham said:**
> yep, you need to burn as an image, which you've not done. You've just burned the image file to a cd, which is why it won't boot.

Try again with another disc, and look for the burn image option. Which software did you use?

yess!! I got it thanks to the last guys post!!

---


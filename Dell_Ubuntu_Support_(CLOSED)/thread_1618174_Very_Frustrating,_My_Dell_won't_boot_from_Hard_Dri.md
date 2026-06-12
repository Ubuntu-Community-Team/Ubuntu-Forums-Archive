---
title: "Very Frustrating, My Dell won't boot from Hard Drive or from live Cd"
date: 2010-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsdieorksw on 2010-11-10
I have a Dell Inspiron 1525 with 10.04 installed.  I installed the newest version of ubuntu from a live cd many months ago but within the last couple days I am no longer able to boot my computer properly to the login screen. For some reason after downloading some files from bittorent (this is probably what caused this but I have no idea how, why, or how to reverse it) my computer froze and I was forced to force shutdown. But now whenever I try to turn my computer back on it goes to the login screen (but it does not look like it normally should, colors are missing, no buttons work, etc.) and it doesn't let me do anything; the mouse doesn't even move. So I tried booting from the live cd that I used to install, and the following appears on the screen: 
"BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

I have no idea what this may mean. So as of right now I can't boot my computer normally or from the live cd so I'm not sure what to do. Can someone help me? The data on my computer is not important, if someoneo can tell me how to get around this and reinstall then that's fine. I just want to be able to use my computer again. Thanks for any help.

---

### Post by kamohammed on 2010-11-10
about the error you were getting:

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed:  Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on  //filesystem.squashfs"

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I had that error while clean installing. I followed the instructions here on how to burn the ISO... using the file suggested there... I was able to run the boot. (install or live cd)... worked for me at least...

The first part, maybe you booted in safe mode... I remember doing that a point in time, but cant remember how and what :/ ... cant help you there...sry...

Added:
try this maybe, press ESC when your PC boots to enter the Grub menu... its like F8 for Windows. Try the options there and see...

Added:
or try this... 
>  				 				**Re: Lappy no boot :(** 			
 			 			 		   		 		 		Try booting  into 'Recovery Mode' (press & hold 'shift' key while the laptop is  booting).

There, select dpkg first (repair broken packages). If it does not work,  reboot & try again in recovery mode selecting 'failsafeX' mode this  time. It should enable you to log in. Then try rolling back the new  driver & using the default one.


---

### Post by jsdieorksw on 2010-11-10
Yeah, I'm burning a new live cd now, we'll see if that works.  Strange that this cd doesn't work anymore...

---

### Post by kamohammed on 2010-11-10
yeah... i had used mine to install ubuntu somewhere, cant remember and yesterday it gave trouble to install. I read up tons of post all over, but the suggestion from the ubuntu site worked for me. 
You can try the "hold shift or ESC" and see if that works out for you...

Im no pro in ubuntu... yet... , but I had similar problems before and those were the suggestions I got. Hope it can help you too...

---


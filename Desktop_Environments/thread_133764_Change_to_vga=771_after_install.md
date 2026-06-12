---
title: "Change to vga=771 after install???"
date: 2006-02-20
forum: Desktop Environments
---

### Post by ConfidentiaL on 2006-02-20
I have  just installed Ubuntu Linux v 5.10, but are having some problems with the screen.
When I installed I had am external screen connected to my laptop all the time, and I didn't use the vga=771 argument on the install. But now when I boot up my install of Ubuntu Linux, I only get a blank screen on my laptop. To be able to see anything, I have to use the external screen to boot with, and then the external screen is the only screen showing an image. My laptop is an Asus A6Va with an ATI Mobility Radeon x700.

I was thinking maybe I should have used the vga=771 argument on the install, but thats too late now... Any1 have a solution for me?

---

### Post by RAOF on 2006-02-20
And this persists - you don't get the login screen on your laptop?

You can add the vga= line to your boot config - you'll need to edit (using sudo) the /boot/grub/menu.lst file, and find the line that looks like:
```
## Options to pass to kernels
# kopt=quiet splash

```
and add the vga= option.  This will make sure that when/if you get a kernel upgrade, the vga option stays enabled with the new kernel.

You'll also want to add the vga= option to the boot options of the actual kernel, further down the file.

---

### Post by ConfidentiaL on 2006-02-21
Ok, I have to say Im fairly new to linux, so I would appreciate if any1 could tell me how to do this more specific.

Thx in advance

---

### Post by kaamos on 2006-02-21
Hello!

Open a terminal. Applications->Accessories->Terminal. Type there
```
sudo cp  /boot/grub/menu.lst  /boot/grub/menu.lst.bak
```
That created a backup of the file. Now you will edit the original with this command:
```
sudo gedit /boot/grub/menu.lst
```
A text file will open up. There you will find a section that looks like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hd*XX* ro
# kopt=root=/dev/hd*XX* ro
Change the line "# kopt" by adding the vga to the end. No not modify anything else! So now the section looks like this:
> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hd*XX* ro
# kopt=root=/dev/hd*XX* ro **vga=771**
Save and close the file. Then type this in the terminal:
```
sudo update-grub
```

Now the line is applied to the kernels and should work at next reboot.

---

### Post by ConfidentiaL on 2006-02-21
I still dont get an image on the laptop's screen, only on the external one.
When I boot, I get to the screen where linux loads, an all the ok's appear on the right side(shows on both screens), but when that one is done, the laptop screen seems to turn itself off, just as it would look if I used the button to turn the screen off, and image on the external changes to the login...

plzz...

---

### Post by ConfidentiaL on 2006-02-21
Also, how do I change the different resolutions you get to choose in the start? I only chose one...

---

### Post by FIONEX on 2006-02-21
You might want to look at /etc/X11/xorg.conf .  I'm not sure if that helps you at all because I'm a noob when it comes to linux.  But if it has to do with resolution, monitors, and screens, then that's something to look at.  I just use it to increase the  resolution for my mouse and the refresh rate and resolution for my monitor.

---

### Post by karlharratt on 2006-02-21
There is an on-going artical about installing Linux (specifically Ubuntu) on [http://techrepublic.com.com](http://techrepublic.com.com) (search for Wacky Linux Adventure) it has been running for a few weeks now and you'll have to go back a couple to find the answer to this problem. 
It is an interesting artical for any n00b (including myself) or any expert who wishes to pass on there expertise.

If this is Trivia Geek then please accept my apologies for causing a paradox.
PCSupportUK

---

### Post by ConfidentiaL on 2006-02-21
I cant seem to find that discussion:-? 
COuld u post a link for me plase?

---

### Post by stepmuel on 2007-09-16
in grub click 'e' to edit the current entry, select 'kernel /boot/vmlinuz...' and click 'e' again. then add ' vga=771' to the line and confirm with enter. then you can boot with 'b'.

afterwards you can add this option in /boot/grub/menu.lst to make it default.

---


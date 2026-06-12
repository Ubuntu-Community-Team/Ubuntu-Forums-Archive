---
title: "[SOLVED] Looking for guidance on slow boot, and slow evolution"
date: 2007-12-10
forum: Desktop Environments
---

### Post by MikeyXX on 2007-12-10
I have my Ubuntu 7.10 working about as well as I'd like. Nothing really major causing me problems (I even got my MoGo mouse to work!). I do have a couple outstanding issues that cause me the most grief.

1) it takes almost 3 minutes to boot. I added "profile" to the end of the kernel line, but that didn't do any appreciable change. If it's booted via XP, it takes about a minute and a bit. Vista takes about 40 seconds. I did a search on google and followed some links that this board offered, but can't seem to find anything to help. I did shut down some unnecessary services, but still....

2) Evolution suddenly takes a while to start. If I press the icon, it won't even show in the bottom application bar for close to 3.5 minutes. It use to move faster and I can't imagine what I've done recently to cause the delay. I don't think I've installed anything...

If you offer any advice, please be specific as I don't know linux very well. Although I am very strong when it comes with computer technology.

---

### Post by swerner on 2007-12-10
For the boot process try this, it's for Ubuntu 6.10 but is still valid for 7.10:
[http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

You could also try installing bootchart to see where most of the effort is spent booting:
```
sudo apt-get install bootchart
```

You will find a png image in /var/log/bootchart

Sorry, I can't help much with Evolution.

---

### Post by MikeyXX on 2007-12-10
Hmm, I missed that link. I'll have a look and see what happens. I've downloaded your app too so we'll see where it's hesitating then I'll have more directed questions.

Thanks for your effort. Don't worry about evolution, that's secondary. I can deal with that seperately.

---

### Post by MikeyXX on 2007-12-10
Ok, I ran it. I'm going to look and then post any of the big time takers (if I can figure out how to read it). Maybe I'll just post the whole thing here.

---

### Post by idiotonuni on 2007-12-10
I had a slow boot problem where it took about 5 mins to boot up also.  I did some searching and i found out it was my bluetooth usb port.  So try to remove a bluetooth conection if you have one and see if it helps.

---

### Post by shae on 2007-12-11
How did you add profile to the end of your boot parameters?  If you added it to the GRUB menu.lst, that could be part of your problems.

---

### Post by MikeyXX on 2007-12-11
I just hit ESC, then hit E and then highlighted the top kernel and hit E then added it at the end of the kernel line. When I went back in after a reboot, it wasn't there si ti ran just the once. It's suppose to help map th efiles so it boots faster. Didn't really work though.



I ran that bootchart and there are three items that take over 90  seconds. Then once two of them stop, there is a bunch of files that run quickly and it boots.

RC lasts for a while, but other things run at the same time, but while
SO1readahead andreadahead-list run, nothing occurs until they end.


Does this mean anything to anyone? If they were shorter, so would my boot time.And it doesn't even look like it's running for most of that time (as the line is clear with only a few dark sections).

---

### Post by redrovo on 2008-01-31
Hi, I am having a similiar problem. I installed Ubuntu 7.10 on my 1.8ghz Turion64 1gig as a dual boot with XP. It takes 1:30 minutes to start to a stable desktop compared to 45 seconds for my XP. This is all minus the grub loader. 

The time difference doesn't matter so much to me, except I feel it must be booting something incorrectly to take so much longer. I've always known linux distros to be much lighter than windows. 

I ran a bootchart, but really am not seeing what is the hangup there. It seems to only cover the first 30 seconds. I'm not sure how to adjust this capture. I've attached the image. 

Also, I've removed ro splash and quiet from menu.lst (grub) .

If anyone has found where it might be stumbling, I would really like to resolve it on my machine. 

Otherwise, Ubuntu is awesome! Couldn't be happier with it. 

Thanks :)

---

### Post by MikeyXX on 2008-01-31
This is what I did. Don't know where i got  the instructions, but I can't find them again. It's booting extremely quickly now.

1) Edit menu.lst
```
 sudo gedit /boot/grub/menu.lst
```

2) At the very end of the kernel line after "splash" , add "vga=791" 
```
 title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e25fb39e-cded-4529-9537-1861e4637173 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quie t
```

3) Save that file, close it, and open up usplash's config file:
```
sudo gedit /etc/usplash.conf
```

Should look like this (if your resolution is 1440 x 900 of course)
```
# Usplash configuration file
xres=1440
yres=900
```

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

```
uname -r
```
This lists your current kernel version.
```

sudo update-initramfs -u -k <insert results from uname -r here>
```

This rebuilds the image that Grub uses to start the system.


It worked for me. Turns out the usplash routine picks up the wrong resolution and pauses. Dunno why, but again, this worked for me. Evolution has speeded up a bit too (although I can't see it being related). I think my Evolution problem is the massive amount of email I'm dealing with over an OWA connection.

---

### Post by redrovo on 2008-01-31
I appreciate the help, but unfortunately vga=791 only made my screen black for the entire boot process. Still took the same amount of time to boot up.

---

### Post by MikeyXX on 2008-01-31
But did you edit the usplash config file with your default resolution?

---


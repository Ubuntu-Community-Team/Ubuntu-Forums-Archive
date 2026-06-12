---
title: "Can't Get To Command Line Interface"
date: 2006-09-20
forum: Desktop Environments
---

### Post by billyfoxtrot on 2006-09-20
Hi,

I just installed Ubuntu on my Dell M1210 laptop, and I'm used to pressing Ctrl Alt F1 to get to the command line in Debian.  When I try this in Ubuntu I only get a black screen.  Does anyone know how to fix this?  I installed the NVIDIA driver, could this have something to do with it?

---

### Post by Paul41 on 2006-09-21
You can create a keyboard shortcut by going to System menu -> Preferences -> Keyboard Shortcuts

---

### Post by billyfoxtrot on 2006-09-21
It's not the keyboard shortcut that's the problem, it feels like Ctrl Alt F1 should work.  It's just that I'm getting a black screen instead of the command line.

---

### Post by Paul41 on 2006-09-21
Sorry, I thought you were trying to open a terminal window.  I also have the NVIDIA driver and Ctrl Alt F1 does take me to the command line so I don't think that is your problem.

---

### Post by billyfoxtrot on 2006-09-21
Nobody knows how to fix this, or if it's a bug of some kind?  I really like working in the virtual console, and I have no idea why it's giving me a black screen instead of the command line.

---

### Post by skymt on 2006-09-21
/etc/inittab should have a bit like this:```
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```Does it?

---

### Post by billyfoxtrot on 2006-09-21
> **skymt said:**
> /etc/inittab should have a bit like this:```
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```Does it?

Yes, it looks exactly like that.  Any ideas?

---

### Post by mssever on 2006-09-21
Here's a kludge:
```
sudo /etc/init.d/gdm stop
```

But it's odd that Ctrl+Alt+F1 doesn't give you a console. It works for me just fine. I did end up SSH'ing into my box once to restart GDM when I encountered some weird problem switching back and forth.

---

### Post by rhwang on 2006-09-21
I've just got my M1210 today and I have exactly the same problem.

Hmm the plot thickens.

---

### Post by rhwang on 2006-09-21
I just got my M1210 today and I have exactly the same problem!

So you are definitely not alone...

---

### Post by billyfoxtrot on 2006-09-21
> **rhwang said:**
> I've just got my M1210 today and I have exactly the same problem.

Hmm the plot thickens.

Interesting... How did you go about setting yours up?  Did you install the NVIDIA driver?  For some reason I have a feeling that might be the culprit.

---

### Post by Paul41 on 2006-09-21
> Did you install the NVIDIA driver? For some reason I have a feeling that might be the culprit.
If you think it is the the NVIDIA driver you could disable it and then try to see if that is what is causing your problem.

---

### Post by billyfoxtrot on 2006-09-21
> **Paul41 said:**
> If you think it is the the NVIDIA driver you could disable it and then try to see if that is what is causing your problem.

Thanks for the advice Paul, do you know the easiest way to temporarily disable it?  Sorry, I'm a bit of a n00b. ;)

---

### Post by Paul41 on 2006-09-21
> Thanks for the advice Paul, do you know the easiest way to temporarily disable it?
I think you can just change the "nvidia" driver in the ext/X11/xorg.conf file to "nv", but I have never actually tried this.  I know you can do it by running:
```
sudo dpkg-reconfigure xserver-xorg
```
This will reconfigure your xserver settings and you can choose the nv driver there.

---

### Post by billyfoxtrot on 2006-09-22
I fixed the problem.  [This site]("http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html") mentions the problem, and states the solution.  Apparently, it is a problem with the nVIDIA driver.  All you have to do to fix it is edit your /boot/grub/menu.lst file and add "vga=791" (without quotes) on the line that says kernel.  So the end of the file should look something like this:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Restart, and that should do it!  I think the resolution of the virtual consoles is 1024x768 instead of my regular resolution of 1280x800, so it looks a little stretched.  But that's just a minor thing to note.

---

### Post by rhwang on 2006-09-22
Woo! I got around it by temporary using the nv driver instead but this is much better.

Will give it a try.

Now I must go ahead and try to get all the 64 bit codec working - got a Core2Duo M1210!

ps if your M1210 hangs saying "saving vesa state" (which you might becase it happens to me) here is how you fix it (a bit off topic I know)

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-April/017581.html](https://lists.ubuntu.com/archives/ubuntu-devel/2006-April/017581.html)

One should probably start a M1210 howto since I am still struggling to get it to work with an external monitor using fn-f8!

R.

> **billyfoxtrot said:**
> I fixed the problem.  [This site]("http://parrenin.frederic.free.fr/DellLatitudeD800/linux-DellLatitudeD800.html") mentions the problem, and states the solution.  Apparently, it is a problem with the nVIDIA driver.  All you have to do to fix it is edit your /boot/grub/menu.lst file and add "vga=791" (without quotes) on the line that says kernel.  So the end of the file should look something like this:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Restart, and that should do it!  I think the resolution of the virtual consoles is 1024x768 instead of my regular resolution of 1280x800, so it looks a little stretched.  But that's just a minor thing to note.

---


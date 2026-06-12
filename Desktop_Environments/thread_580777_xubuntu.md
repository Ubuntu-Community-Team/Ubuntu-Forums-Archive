---
title: "xubuntu"
date: 2007-10-19
forum: Desktop Environments
---

### Post by piratesmack on 2007-10-19
I installed xubuntu 7.10 on an old PC today. I have encountered a few problems.

1. the default resolution was too high for my monitor (I fixed this by editing xorg)
2. every time I try to open the terminal, it takes me back to the log in screen
3. When I try to shutdown, it seems to unmount the hard drive and kill all processes, but it stays at the xubuntu logo until I press the powerbutton on my computer.

The main problem I'm trying to fix is the 2nd one. Any help would be appreciated

---

### Post by TeaSwigger on 2007-10-19
Sorry I can't offer an "I know!" but there is a clear theme to my admittedly inexperienced eyes:

1) You had to hand-config xorg.

2) opening a terminal crashes X.

3) shutdown hangs.

All 3 could well be graphics related, suggesting that either the old graphics card is not well supported, there is a defect, or the configuration and/or "driver" is not cutting the mustard.

If you will find & post the specific graphics card used and any "driver" or graphics package you installed (such as 915resolution etc) if any, that might help find a solution. Also any other info about the PC could potentially help.

---

### Post by piratesmack on 2007-10-19
It's an intel 810L
I don't know the driver off the top of my head, butxubuntu installed it automatically
When I run the command:
"sudo apt-get install xserver-xorg-video-intel"
It says the driver is already up to date

---

### Post by piratesmack on 2007-10-19
The PC is a hp pavillion 6735kr
it has a 15gb hard drive
It came with 64mb SD RAM (I replaced it with a 128mb stick)
Celeron 677MHz

---

### Post by TeaSwigger on 2007-10-19
Wow it's incredibly busy here! 

Hm. Graphics woes aside, I'm afraid xubuntu may be a bit too hefty for those specs. Performance will still be problematic with 128mb shared memory. That's not to imply the computer isn't useful; there are many Linux flavors which will run very nicely on that computer. Some good suggestions for lower spec units to start with may be found at these sites by some particularly adept ubuntu forum members:
[http://kmandla.wordpress.com/](http://kmandla.wordpress.com/)
(lots of good tips and ideas for older / lower spec computers)
and 
[http://www.psychocats.net/](http://www.psychocats.net/) 
(at above look for the minimal install articles)

For problem 3) the hanging at shutdown, I can suggest a quick fix for now that should at least allow you to shut down normally. One of my PCs will hang at shutdown unless I disable the graphical boot, that is the purdy screen which says "xubuntu" while the computer loads, before the sign in screen comes up. It's called "usplash" and also comes on when you shut down, which is where it'll hang mine until I hit the power button. Good news is we can disable "usplash." Here's the work around:

Edit the file /boot/grub/menu.lst in mousepad. First make a backup. You need admin rights so the code is, and you can put this in the run applet for the xubuntu task bar instead of a terminal if you have to:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

to make the backup, then

```
gksu mousepad /boot/grub/menu.lst
```

Or if you can't get to it, hope isn't lost; boot into "recovery mode" and when it stops at the command prompt, enter:

```
nano /boot/grub/menu.lst
```

...and edit it right there "the old fashioned way." Bear in mind you can use this method to reverse the change if there is a problem. Okay, in this file you'll find the line for the xubuntu kernel it boots. Mine for example:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6f9e3158-1af5-4b8e-92c1-09ec5f1b6fc7 ro pci=routeirq nosplash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
```

The longest "kernel" line is the one we want. Yours should end with "ro quiet splash." Erase the "quiet" and "splash." Change it to "nosplash." Save. That's all. It'll still shut down wrong this time, but now when you next boot up, you should see loads of scrolling text as it goes about its business. You can ignore until it loads up the log in screen. When you next shut down, it'll show some similar scrolling text but should shut down by itself and reasonably fast too. If this works there is absolutely no harm in using it, leaving it this way indefinitely. I haven't bothered to "fix" it since the PC is old and this non-graphical boot up and shutdown is faster by nature. 

Unfortunately I can't offer anything further beyond suggesting that graphic card and related does appear to be the problem area for all of these issues. Hopefully someone else can help you zone in on a solution.

---

### Post by reset3x on 2007-10-19
I've had the problem with the i810 graphics killing the Terminal. The only work around that I could find was setting the color depth to 16. No problems after that.

Hope this helps...

---

### Post by piratesmack on 2007-10-19
> **reset3x said:**
> I've had the problem with the i810 graphics killing the Terminal. The only work around that I could find was setting the color depth to 16. No problems after that.

Hope this helps...

Thanks, I was thinking of trying something like that

---

### Post by piratesmack on 2007-10-19
I did the no splash thing, it didn't work. 

But Now I can see an error it's having

"unable to itertate IDE devices: No such file or directory
[ 135.6324551 System Halted"

Then I have to press the powerbutton

Oh and the 16 bit color depth worked perfect

---

### Post by piratesmack on 2007-10-19
But it seems to unmount the hard drive and  everything. Is it safe to shut it down like this?

---

### Post by reset3x on 2007-10-19
> **piratesmack said:**
> But it seems to unmount the hard drive and  everything. Is it safe to shut it down like this?

Just realized what is going on. It's your BIOS. ACPI isn't working. It's safe to turn off your PC.

EDIT: See this thread for a fix: [https://answers.launchpad.net/ubuntu/+question/6522](https://answers.launchpad.net/ubuntu/+question/6522)

---

### Post by piratesmack on 2007-10-22
Alright, cool I got all my problems fixed now. I found out that it's letting me enable compositing in 16bit color depth (it wouldn't in 24bit) do you think an intel 810L could run compiz?

---

### Post by mnfiddledragon on 2007-10-24
FWIW, I had the same issue (as #2) on my Sony Vaio PCG-F540, PII, 128M RAM, etc...

I just upgraded from Dapper Drake, through the ranks, to Gutsy Gibbon, and switched from Ubuntu to Xubuntu at the same time (5.5G hard drive, and a DVD drive that doesn't work. I needed to save space). Anyway, after cleaning up everything, the terminal issue seemed to be the last remaining bit. I thought it was a remnant from either the upgrade or the switch from Ubuntu to Xubuntu via the repositories, but after reading this thread, I decided to try the fix.

Changing color depth in /etc/X11/xorg.conf from 24 to 16 worked beautifully.

---

### Post by reset3x on 2007-10-26
> **piratesmack said:**
> Alright, cool I got all my problems fixed now. I found out that it's letting me enable compositing in 16bit color depth (it wouldn't in 24bit) do you think an intel 810L could run compiz?

That may be stretching things a bit... The i810 uses some of your system RAM for graphics.... PC133 is slow .

---

### Post by andhar on 2007-10-27
I installed xubuntu 7.10 on an i810 based system yesterday and had the terminal crashing and me finding myself at the login screen.

the work around was to install gnome-terminal. xterm also worked.  I posted about it so you can check my recent post.

---


---
title: "new user experiencing kernel panic-help!"
date: 2009-02-13
forum: General Help
---

### Post by jaslin on 2009-02-13
I just about jumped out of my skin when installing Ubuntu 8.1 actually worked today.

It booted really nicely from the hard drive, then I started downloading the upgrades.  It locked up while the updates were loading.

I waited a long time then reverted to the power button.  I got an error screen with these lines:

Boot from (hd0,0) ext3  0f97b244-fele-46da-ab48-299b33d1339f
Starting up...
[   0.800146] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

There is a blinking cursor, but it won't let me type anything.  There is no existing kernel, it's an entirely clean install.

Can't tell you how frustrated I am. I have the live CD, can things be fixed from there?  If so, how?  Any guidance would be great.  I DO NOT want to go back to Windows.  By the way, I installed on a clean drive and let the installer partition for me.

Thanks, Jaslin

---

### Post by drs305 on 2009-02-13
Welcome to the ubuntu forums. Sorry you are having a bit of difficulty with 8.10.

Here is a blog post of a similar problem. He was doing an upgrade so it may not apply if you are doing a fresh install:

[_http://www.maxhorvath.com/2008/11/problems-when-upgrading-to-ubuntu-810-kernel-panic-unable-to-mount-root-fs.html_]("http://www.maxhorvath.com/2008/11/problems-when-upgrading-to-ubuntu-810-kernel-panic-unable-to-mount-root-fs.html")

If that doesn't apply to you, try searching for:
*Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)* 

I found a few threads on the topic. If you use the Advanced Search feature of the ubuntu forums you can narrow the results to those of the past month.

---

### Post by jaslin on 2009-02-13
Thanks Drs

I'm having trouble understanding the fix he recommends.  I've been randomly trying things using the live CD, but I'm at a total loss.  When I searched google with the error message I was getting, it looked liked there were a million variations of this message and that the problem is pretty common.  My problem is I can't just start putting in line commands.  I'm at the mercy of the installer.

Thanks again.

---

### Post by drs305 on 2009-02-13
**Added**: The upgrade probably included a new kernel. If you have a previous kernel available, try booting into that one. Access it via the grub menu. If you don't see a menu, hit ESC during boot until the grub menu appears. Select a different kernel than the one you are having the trouble with (a different one on the menu, probably one with a lower number, such as 2.6.27-9). If you are just installing ubuntu for the first time, you won't have an alternate kernel and can disregard this paragraph.

...


Okay, if you would like to learn a bit about how to fix things when you are using the LiveCD I can give you the basics. The solution I linked to may not work for you but the process of accessing the files will be the same no matter what you do in the future. You can save these instructions for future use if you need to access the system files from the LiveCD. In the meantime, perhaps someone will post a direct solution to your problem.

**A HowTo on Accessing Your System Files via the LiveCD:**

Boot the LiveCD. From the LiveCD desktop, open a terminal: Applications, Accessories, Terminal.

Any files you access directly at this point would be LiveCD files. To access the system files you would be using during a normal boot, you have to mount the partition they are on. 

The first thing we have to do is determine where your system files are - what partition they are on. We can do that with this command. It will list the partitions. Unless you have already created extra partitions, you should have one formatted EXT3 and one listed as swap:
```
sudo fdisk -l
```

You will see entries like */dev/sda1* and */dev/sda2*. If you have an entry that looks like the following, it is probably your linux partition. If you aren't sure, post the results. See the end on how to post results from the terminal:
> /dev/sda1   *     1   6387    51303546   83  Linux

The next step is to list the UUIDs - these are unique identifiers for each partition and also see what is in your *boot* folder:
```
sudo blkid -c /dev/null
ls -la boot
```

Next we will mount your real system partition. First we make a mount point, then we mount it and change to its directory. Change *sda1* to whatever you determined to be the system partition:
```

sudo mkdir /mnt/*sda1*
sudo mount /dev/*sda1* /mnt/*sda1*
cd /mnt/sda1

```

Now you can look at your real system files:
```

cat etc/fstab
cat boot/grub/menu.lst

```

This would get you to the point where you could again look at the link I provided. However, if you didn't upgrade from an earlier version this link probably isn't the solution. 

This would get you to the point where you could again look at the link I provided. However, if you didn't upgrade from an earlier version this link probably isn't the solution. Take a look and see if the link makes any sense. If not, don't get discouraged. Post the results of the "blkid, ls, cat etc/fstab, cat boot/grub/menu.lst" commands here and we can look at them. 

To post the results, you can open a browser with the LiveCD and copy/paste. Copying from the terminal is different from windows. To copy something from within a terminal, highlight it and use CTRL-SHFT-V to put it in memory. Even easier, highlight the section with your mouse and middle click to paste!  To paste into a terminal, use CTL-SHFT-C. To copy/paste into other applications (not in terminal) the familiar Windows commands (and the middle click mouse) still work.

** Added **
To post results, open a reply and click on the # symbol at the top of the post. This will insert (without the spaces) 
[ CODE ][ /CODE ]
You copy between the two.
**  **
If you post those results we might be able to see if there is a problem in grub's menu.lst.

---


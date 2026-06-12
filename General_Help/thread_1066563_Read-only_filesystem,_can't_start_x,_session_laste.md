---
title: "Read-only filesystem, can't start x, session lasted 10 seconds, etc."
date: 2009-02-11
forum: General Help
---

### Post by MaindotC on 2009-02-11
Lot of problems here.  I can't think of anything that caused these problems - didn't add or remove any apps, didn't fetch any updates, didn't change xorg.conf, filesystem doesn't appear full, anything like that.  I have been switching out wireless USB devices to try and find one that goes faster than 24 mbps and after a while [_the WUSB600N fails_](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=17641), and the fully supported Realtek 8187 in my [_WiBee XS-2204s_](http://www.buy.com/retail/product.asp?sku=207675987&listingid=21275012&dcaid=17902) was [_having bugs and didn't work anyway_](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/261098) so I have to reboot, but aside from that nothing else.

I was trying to get my machine (everything listed in signature) to boot from a live USB.  I went into the BIOS and disabled the hard drives, selected every possible option that would boot USB first.  Well, booting from USB is too much to ask from my mobo, so I moved that project to my laptop.  I went back into the BIOS and re-enabled the hard drives.  It took a while to get this configured because I wasn't smart enough to save the profile to the BIOS and the ones I had already saved didn't load properly.  Finally, I see both hard drives are detected.

I boot into Hardy and it begins to check the filesystem.  After roughly [_70% of filechecking, just like this post_](http://ubuntuforums.org/showthread.php?t=960398) it drops into a terminal with an output saying [_unexpected inconsistency; run fsck manually fsck died with exit status 4_](http://ubuntuforums.org/showthread.php?t=333641).  I enter the root password, and per [_other posts regarding this issue_](http://www.google.com/search?q=read-only+filesystem+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) I enter the password for the root shell (which is plaintext and not concealed btw) and type:
```

e2fsck -c /dev/sda1  #it does its thing on /home
e2fsck -c /dev/sda4  #doing its thing on / partition

```
It seems that this did something, so I type
```

 shutdown -r now

```
It starts to show the services stopping, and then a blue screen appears stating that X could not be started and to restart x when I can.  There's a shell poking through the blue area so I log in and use the shutdown command again, and this time the machine actually reboots!  I was running into a Grub Error 17 and 22 but I read on how to point grub in the right direction so I know it is using /dev/sda4 as the boot partition.

When I actually do get to the login window, the screen blinks 6 times and then I am prompted with a message stating [_the display server has been shut down 6 times_](http://www.google.com/search?q=display+server+has+been+shut+down+6+times+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) and there's a problem.  I use the f2 terminal to examine xorg.conf and I even copied that file to backup, then moved the backup file to xorg.conf, and tried w/ some of the other xorg.conf.backup* files but that didn't seem to be the issue.

I can rarely boot from the LiveCD to run e2fsck or that time I had to reinstall grub.  Sometimes it makes it, sometimes it doesn't.  I have 2 cd's of Ibex (because I was installing Ibex on the USB drive for testing purposes) and both of them make it 1 out of 5 times.  I can't get to the Live CD desktop but I can get to the f2 terminal so I run what commands I need from there - usually unmounting the /dev/sda* partitions and e2fsck'ing them.  Roughly twice during this process of constant reboots, I have gotten to the login (I have it set to log in automatically) but I get the [_"your session only lasted less than 10 seconds"_](http://ubuntuforums.org/showthread.php?t=904081) message and I am unable to login via GNOME Failsafe.  I did have the f2 terminal though so I downloaded the ATI driver just in case that was the issue but haven't had a chance to install it.

E2fsck usually returns notifications like:
```

/dev/sda4 updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? y
(more inodes fixed)
(more numbers)
/dev/sda4: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda4: ***** REBOOT LINUX *****
/dev/sda4: 236523/1826816 files (1.0% non-contiguous), 2080692/7291501 blocks

```
So I type "reboot" and I get the blue screen:
```

Could not start the X
server (your graphical environment)
due to some internal error.
Please contact your system administrator
or check your syslog to diagnose.
In the meantime this display will be
disabled.  Please restart GDM when
the problem is corrected.

<Ok>  (I can't select this "Ok")

```
Then the tty1 login appears on top of the blue screen so I log in as non-root administrative user.  It says:
```

No directory, logging in with HOME=/
-bash: no job control in this shell
-bash: cannot create temp file for here document: Read-only file system

```
and I issue the reboot command again.

Lots of problems.  Open the floodgates of suggestions and please not the ones I've already googled and listed in the links above.

---

### Post by MaindotC on 2009-02-11
Update - just tried booting this morning and I AM ACTUALLY IN MY DESKTOP ENVIRONMENT but there's a message that popped up saying "Internal error! failed to initialize HAL!"  I tried to run updates but I couldn't get my wireless device to work.  I thought I'd try and clear out /tmp but when I use rm -rf /tmp/* it says its a read-only filesystem again!

---

### Post by MaindotC on 2009-02-14
Bump - would it make any difference if I changed the entry in fstab to "rw" instead of "ro"?

---

### Post by 2hot6ft2 on 2009-02-14
> **strAlan said:**
> Bump - would it make any difference if I changed the entry in fstab to "rw" instead of "ro"?
ro is Read Only and rw is Read Write which I'm sure you already know but it looks like you have a lot of problems going on all at once. What the heck it's worth a shot at this point, right.

---

### Post by MaindotC on 2009-02-19
I went into the BIOS and selected "Load Failsafe Defaults" which has crippled my machine in the past but for some reason it worked this time.  Both drives are detected and I can boot properly.  Unfortunately, I decided to delete the paritition table and mkfs.ext3 for the 2nd sata drive and I lost all the data!  A lot of .iso's are now gone :(

---


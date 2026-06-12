---
title: "UUID and Failsafe Graphics Mode"
date: 2011-01-04
forum: Desktop Environments
---

### Post by dontgetshocked on 2011-01-04
For some reason when i rebooted i can no longer get to my desktop.it says upon boot something like cant find uuid and wait to mount,then it just waits and waits an nothing happens.I can use the failsafe mode and all is well so i think it is a graphics problem and or the mount thing. What do you suggest?

---

### Post by Krytarik on 2011-01-04
Look in /var/log/messages for the complete error message to get any hint. You may post it here as well.

---

### Post by dontgetshocked on 2011-01-04
which file am i looking for?

---

### Post by Krytarik on 2011-01-04
> **dontgetshocked said:**
> which file am i looking for?
Exactly this, it is the filename:
> **Krytarik said:**
> Look in /var/log/[COLOR=Red]messages[/COLOR] for the complete  error message to get any hint. You may post it here as well.

---

### Post by dontgetshocked on 2011-01-04
attached is my message zipped file.

---

### Post by Krytarik on 2011-01-04
> **dontgetshocked said:**
> attached is my message zipped file.
When was the last failed boot, is it covered by the log?

---

### Post by dontgetshocked on 2011-01-04
here is the only one left.

---

### Post by Krytarik on 2011-01-04
I don't find the error message, it's way to much text to scroll through if one doesn't know where to search. Please do the following:

- boot in normal mode, which expectedly fails
- boot in failsafe mode
- post the messages-file again

EDIT: By the way, it's definetely a mount problem, so please attach the file "/etc/fstab" as well.

---

### Post by dontgetshocked on 2011-01-04
ok

---

### Post by dontgetshocked on 2011-01-04
cant access old desktop,the desktop does not show up.
here is the failsafe message file.

---

### Post by Krytarik on 2011-01-04
Obviously the contains incorrect options, did you change it manually?

Correct any occurence of
```
set root='(hd0,msdos1)'
set root='(hd0,msdos6)'
```
to
```
set root='(hd0,1)'
set root='(hd0,6)'
```
respectively.

Or just do
```
sudo update-grub
```

PS: Apparently the error message isn't logged into the messages-file. Maybe in "/var/log/dmesg". Anyway.

---

### Post by dontgetshocked on 2011-01-04
how do i do this,when i am in safe mode? cause thats the only time i can access the desktop unless maybe i can choose repair and boot to the command line,then i would need more code or use the above?

---

### Post by Krytarik on 2011-01-04
> **dontgetshocked said:**
> how do i do this,when i am in safe mode? cause thats the only time i can access the desktop unless maybe i can choose repair and boot to the command line,then i would need more code or use the above?
Are you getting a desktop or not? Why should the commands, at least the last one, not work in failsafe mode? It can also be run in a console (instead of a terminal as usual).

---

### Post by dontgetshocked on 2011-01-05
i did run the code via the terminal with no problems.still cant get into normal desktop.running in low graphics mode.

---

### Post by Krytarik on 2011-01-05
Thanks for attaching a (real) screen-shot. What about pressing "s" at this point to skip mounting?

Please post the content of the file "/etc/fstab".
Did you remove a hard disk or external device, which is set up in fstab?

EDIT: And by the way, please check /boot/grub/grub.cfg to verfify that the boot options are correct now.

---

### Post by dontgetshocked on 2011-01-05
Ok i have tried editing but think that the uuid when it loads is not what is in the fstab file.boot.cfg or something and fstab are not getting along,i think.

---

### Post by Krytarik on 2011-01-05
It's definetely the "swap"-partition, which isn't mounted correctly.

Check with
```
sudo fdisk -l
```what device name it has (/dev/sda*). You can identify it with "Linux swap / Solaris" in the most right column of the output.

Then just put the device name instead of the UUID-declaration in fstab.

---

### Post by dontgetshocked on 2011-01-05
here is my info

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10041    80646144   83  Linux
/dev/sda2           10041       19458    75641857    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5           18306       19458     9252864   82  Linux swap / Solaris
/dev/sda6           10041       18306    66388992   83  Linux

---

### Post by Krytarik on 2011-01-05
Ok, just yet did some research of UUID.

When changing the swap partition, you apparently have to also update UUID for initramfs:
[https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation](https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation)

So re-check the UUID with
```
sudo blkid
```
and replace the old entry with it.

You should also use it as identifier in fstab, in case of partition changes you don't have to update the existing entries then.

---

### Post by dontgetshocked on 2011-01-05
david@Mint ~ $ sudo blkid
/dev/sda1: LABEL="Mint" UUID="8df76cb2-e543-4b4d-89d9-b599827c199e" TYPE="ext4" 
/dev/sda5: UUID="0bc099be-db03-470a-a343-77b3800ba9fc" TYPE="swap" 
/dev/sda6: LABEL="Pinguy" UUID="e99f1256-a8df-4dac-be0f-10bf4f8e1a3f" TYPE="ext4"

---

### Post by Krytarik on 2011-01-05
Then replace the UUID in /etc/fstab and /etc/initramfs-tools/conf.d/resume with the correct one:
0bc099be-db03-470a-a343-77b3800ba9fc .

By the way, is /dev/sda6 (Pinguy) intentionally not set up in fstab?

---

### Post by dontgetshocked on 2011-01-05
these changes have been made now and i did want to eliminate pinguy from the grub and even delete the partition and while mint is up install grub or grub2 again also it will be the new grub.will this work? I can now get to my desktop but it boots into safe mode and takes literaly hours to perform a function.it flies in safe mode itself.

---

### Post by Krytarik on 2011-01-05
> **Krytarik said:**
> Then replace the UUID in /etc/fstab and /etc/initramfs-tools/conf.d/resume with the correct one:
0bc099be-db03-470a-a343-77b3800ba9fc .
After you made this, don't forget to do also
```
sudo update-initramfs -u
```
Like it's mentioned in the UUID-guide I posted the URL of.

So, if you are still booting through the GRUB Pinguy has installed, then the "update-grub" we've done doesn't affect the boot options. To install GRUB(2) out of Mint:
```
sudo grub-install /dev/sda
```
and again, to be sure
```
sudo update-grub
```
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

After that the proper boot options should be used to get you to a normal desktop.

Then it's also safe to delete the Pinguy partition, of course after you saved needed personal files.

---

### Post by dontgetshocked on 2011-01-05
I still have major problems with main load but safe mode works.dont understand why,it also says it cant mount the drive.

---

### Post by Krytarik on 2011-01-05
> **dontgetshocked said:**
> I still have major problems with main load but safe mode works.dont understand why,it also says it cant mount the drive.
Then please re-check the modifications we've made.

---

### Post by dontgetshocked on 2011-01-05
I thank you for all your help,I have stop for now,my brain is fried.

---

### Post by Krytarik on 2011-01-05
You're welcome! Please post back if you solved it or need more help.

---

### Post by dontgetshocked on 2011-01-07
Going to leave this open for a little bit longer as it is still not working.I can load my desktop after choosing safe mode and then going thru the menus afterwards it will load and except for the desktop glitter,i.e. compiz it works and is even faster.I am continuing to try to solve this problem on my own as well.I have recently learned to use the update manager and thru settings allow it to use level 4 and this allowed me to install my correct video driver.I have reviewed the former suggestions and dont see anything that I have missed,not saying that there is something there that I did not see.Linux is in desperate need of some standalone troubleshooting software at least for dummies.I do not know of any if it exists.Maybe I am wrong but it seems to me to be a graphical problem along with the not being able to mount the drive,but if you choose s to skip it loads? Hmmm , not sure why!

---

### Post by dontgetshocked on 2011-01-07
Going to leave this open for a little bit longer as it is still not working.I can load my desktop after choosing safe mode and then going thru the menus afterwards it will load and except for the desktop glitter,i.e. compiz it works and is even faster.I am continuing to try to solve this problem on my own as well.I have recently learned to use the update manager and thru settings allow it to use level 4 and this allowed me to install my correct video driver.I have reviewed the former suggestions and dont see anything that I have missed,not saying that there is something there that I did not see.Linux is in desperate need of some standalone troubleshooting software at least for dummies.I do not know of any if it exists.Maybe I am wrong but it seems to me to be a graphical problem along with the not being able to mount the drive,but if you choose s to skip it loads? Hmmm , not sure why!

---

### Post by dontgetshocked on 2011-01-07
Going to leave this open for a little bit longer as it is still not working.I can load my desktop after choosing safe mode and then going thru the menus afterwards it will load and except for the desktop glitter,i.e. compiz it works and is even faster.I am continuing to try to solve this problem on my own as well.I have recently learned to use the update manager and thru settings allow it to use level 4 and this allowed me to install my correct video driver.I have reviewed the former suggestions and dont see anything that I have missed,not saying that there is something there that I did not see.Linux is in desperate need of some standalone troubleshooting software at least for dummies.I do not know of any if it exists.Maybe I am wrong but it seems to me to be a graphical problem along with the not being able to mount the drive,but if you choose s to skip it loads? Hmmm , not sure why!

---

### Post by dontgetshocked on 2011-01-07
Still trying to solve.Going to leave this open for a little bit longer as it is still not working.I can load my desktop after choosing safe mode and then going thru the menus afterwards it will load and except for the desktop glitter,i.e. compiz it works and is even faster.I am continuing to try to solve this problem on my own as well.I have recently learned to use the update manager and thru settings allow it to use level 4 and this allowed me to install my correct video driver.I have reviewed the former suggestions and dont see anything that I have missed,not saying that there is something there that I did not see.Linux is in desperate need of some standalone troubleshooting software at least for dummies.I do not know of any if it exists.Maybe I am wrong but it seems to me to be a graphical problem along with the not being able to mount the drive,but if you choose s to skip it loads? Hmmm , not sure why!

---

### Post by Krytarik on 2011-01-07
If you're still getting the same error, it's definetely a problem to mount the swap partition! I had the same a while ago, after moving to a new hard drive. Did you install/update GRUB like I described?

---

### Post by dontgetshocked on 2011-01-07
would it be ok to delete the swap and create a new one using gparted?

---

### Post by Krytarik on 2011-01-07
> **dontgetshocked said:**
> would it be ok to delete the swap and create a new one using gparted?
That wouldn't fix it, it indeed would make it worse, because the partition would get a completely new UUID.

---

### Post by dontgetshocked on 2011-01-07
is the root partition uuid supposed to be the same uuid as the swap?

---

### Post by Krytarik on 2011-01-07
> **dontgetshocked said:**
> is the root partition uuid supposed to be the same uuid as the swap?
No, that isn't possible anyway, it would go counter the purpose of UUIDs.

---

### Post by garyhibdon on 2011-01-07
looking over everything so far, the second archive error message you posted mentions a bios override of the physical ram and then states low physical ram.  have you verified the capabilies of the system? when i was running windows xp i noticed a lack of physical ram due to settings in the bios. accidentally hit a wrong button?

---

### Post by dontgetshocked on 2011-01-07
I reset everything in the bios but it looked ok to be,not much you can change in it.New problem is now my wireless has stopped working.having to use my desktop instead.very much a pain.i hooked up my netbook direct and it connects.??? It's almost to the point that i will give up/backup and re-install except for this is the krap i had to do in my windows days and so far i refuse to accept defeat!nothing in the router settings has changed and it works directly.desktop works fine.So many weird stuff showing up on my netbook! I have 1gb of ram and thats it.suggestions anyone?

---

### Post by Krytarik on 2011-01-07
I'm also generaly stubbornly reluctant to accept defeat. ;-)

So, let's have a deeper look then into the boot-up config:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Post it's results, in CODE-tags (#) please.

EDIT: Regarding the main issue.

---

### Post by dontgetshocked on 2011-01-07
here it is.

---

### Post by Krytarik on 2011-01-07
Apparently we have not talked about what version you are running until now!?

---

### Post by Krytarik on 2011-01-08
1.)  you've changed the UUID of your system partion to the one of your swap partition in /etc/fstab, revert it to:
8df76cb2-e543-4b4d-89d9-b599827c199e

2.) there are some faulty and even double "set root" variables in your grub.cfg, in a terminal (again):
```
sudo update-initramfs -u
sudo grub-install /dev/sda
sudo update-grub
```

Then post the results of the boot info script again.

---

### Post by dontgetshocked on 2011-01-08
david@Mint ~ $ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic-pae
cryptsetup: WARNING: could not determine root device from /etc/fstab
Warning: No support for locale: en_US.utf8

---

### Post by Krytarik on 2011-01-08
> **Krytarik said:**
> 1.)  you've changed the UUID of your system partion to the one of your swap partition in /etc/fstab, revert it to:
8df76cb2-e543-4b4d-89d9-b599827c199e
Did you this before?!

---

### Post by dontgetshocked on 2011-01-08
# / was on /dev/sda1 during installation
UUID=8df76cb2-e543-4b4d-89d9-b599827c199e              ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8df76cb2-e543-4b4d-89d9-b599827c199e  none            swap    sw              0       0

---

### Post by Krytarik on 2011-01-08
> **dontgetshocked said:**
> # / was on /dev/sda1 during installation
UUID=8df76cb2-e543-4b4d-89d9-b599827c199e              ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8df76cb2-e543-4b4d-89d9-b599827c199e  none            swap    sw              0       0
Nope, this way:
```
# / was on /dev/sda1 during installation
UUID=8df76cb2-e543-4b4d-89d9-b599827c199e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0bc099be-db03-470a-a343-77b3800ba9fc none            swap    sw              0       0

```EDIT: changed the code, observe the "/", you've removed it.

---

### Post by dontgetshocked on 2011-01-08
i changed it back but with the same error.

---

### Post by Krytarik on 2011-01-08
> **dontgetshocked said:**
> i changed it back but with the same error.
Take note of my edit of my previous post, I haven't seen this in the first place.

Obviously the thread doesn't get updated immediately, at least your posts.

---

### Post by dontgetshocked on 2011-01-08
Warning no support for locale; en US.utf8

otherwise NO errors

---

### Post by Krytarik on 2011-01-08
> **dontgetshocked said:**
> Warning no support for locale; en US.utf8

otherwise NO errors
Ok, then proceed with GRUB.

EDIT: The locale thing seems to be a common issue currently, shouldn't matter anyway.

---

### Post by dontgetshocked on 2011-01-08
Once again I thank you for staying with me on this.All is well in safe mode.In normal boot it takes forever to load and when you get to the desktop it is still showing the Linux Mint Screen and way,way,way after that when the desktop loads,I am talking maybe 20 minutes or so,everything you try to do takes forever and the CPU from the boot on stays at 100% load and you have to wait and wait.
Any clues of what or where to start or do? I think it is a graphics problem but unsure of what else.
Oh, and now my wireless does NOT work period,I have to plug it in direct. What the heck is going on?

---

### Post by Krytarik on 2011-01-08
Have you done the GRUB thing then? After that please post the results of the boot info script again.

The issue with your wifi may be related to the main issue, or maybe not.

If you are way to overstrained by all of this, and you aren't getting your system to work properly today, it could be easier to just save all your personal files, wipe the disk completely, create new proper partitions and re-install. Maybe "Ubuntu Netbook Remix" this time.

---

### Post by dontgetshocked on 2011-01-08
At this point I believe I will backup everything and do a fresh install.Still hate to do this without knowing what caused it.I well mark this as complete.Thanks for all of your time.A good man knows his limitations and when it is time to admit defeat.Still,I will live ti fight another day.

---

### Post by dontgetshocked on 2011-01-10
One final thought I leave on this.I took it down to bare metal and did a do over and this fixed the problem.However after much soul searching and all of the troubleshooting skills I could muster I believe the problem started with using Desktop Drapes along with allowing level 4 in updates combined with installing another ubuntu os alongside Mint.I am personally done with multiple os's unless as a virtual machine.I have installed probably upwards of 30 distros and they are just not worth it for the normal user in my opinion.
May someone,anyone learn from my experience!

Best Wishes,

---

### Post by stijnh1 on 2011-04-07
I had a similar initial problem (hanging on boot just before login screen, only able to boot in graphical mode via failsafe mode).

Reading the comments here made me check my /etc/fstab, which contained the line:


```
# Commented out by Dropbox
# UUID=170307de-09bd-406a-80ca-4d3702a4f3f8 /               ext4   errors=remount-ro 0       1
```

and had the following line instead:


```
UUID=170307de-09bd-406a-80ca-4d3702a4f3f8 / ext4 errors=remount-ro,user_xattr 0 1
```

The only difference being the user_xattr tag.  I removed that one again, reboot normally, and things worked again.

I remember the ubuntu software center complaining about Dropbox when installing, but I ignored it at the time. Bad idea.

---


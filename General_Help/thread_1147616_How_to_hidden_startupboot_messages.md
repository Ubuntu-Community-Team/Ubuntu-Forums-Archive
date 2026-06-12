---
title: "How to hidden startup/boot messages?"
date: 2009-05-03
forum: General Help
---

### Post by ANew on 2009-05-03
subj:

I get a lot of startup messages on the screen during ubuntu
startup phase. This happens after i resized the ubuntu partition
with gparted. Is there anyway not to show these messages on the
screen?

---

### Post by ajgreeny on 2009-05-03
If you are not seeing the splash screen, where the word ubuntu appears and a growing bar spreads across the screen, you should look in your /boot/grub/menu.lst file to see if the words **splash quiet** appear at the end of the kernel lines.  If not add them and see if it helps.  However, what seems strange if they are not there, is why not.  By default they should be and the system should boot with the splash and no text showing.
Here's an example of what it should look like.
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        10ec6342-7b3f-425c-8655-c637bb65ae72
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=10ec6342-7b3f-425c-8655-c637bb65ae72 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

---

### Post by ANew on 2009-05-03
> **ajgreeny said:**
> If you are not seeing the splash screen, where the word ubuntu appears and a growing bar spreads across the screen, you should look in your /boot/grub/menu.lst file to see if the words **splash quiet** appear at the end of the kernel lines.  If not add them and see if it helps.  However, what seems strange if they are not there, is why not.  By default they should be and the system should boot with the splash and no text showing.
Here's an example of what it should look like.
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        10ec6342-7b3f-425c-8655-c637bb65ae72
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=10ec6342-7b3f-425c-8655-c637bb65ae72 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

I do see splash screen with ubuntu and messages appears after
that. Graphical page with Ubuntu disappears and the screen
fills with a lot of text line.

Also I do have "quiet" in grub menu - it does not help.
The startup was normal - without messages - before i
resized the parttion.

---

### Post by ajgreeny on 2009-05-04
OK, so what are these messages; if we know what they say, we may be able to help sort out the problem.

---

### Post by kpkeerthi on 2009-05-04
> **ANew said:**
> I do see splash screen with ubuntu and messages appears after
that. Graphical page with Ubuntu disappears and the screen
fills with a lot of text line.

Also I do have "quiet" in grub menu - it does not help.
The startup was normal - without messages - before i
resized the parttion.

Can you post the contents of /boot/grub/menu.lst ?

---

### Post by Deamos on 2009-05-04
I have the same issue.  It shows the usplash page briefly and then displays the text readout of services as they are enabled.

Happened to me after I resized my swap partition & main partition.

---

### Post by geirha on 2009-05-04
Just a shot in the dark, but try setting the usplash theme again.
```

# This will list all currently installed usplash themes:
update-usplash-theme
# Set one of the listed themes:
sudo update-usplash-theme *usplash-theme-ubuntu*

```

---

### Post by Deamos on 2009-05-04
> **geirha said:**
> Just a shot in the dark, but try setting the usplash theme again.
```

# This will list all currently installed usplash themes:
update-usplash-theme
# Set one of the listed themes:
sudo update-usplash-theme *usplash-theme-ubuntu*

```

This does not fix the issue.  Just tried it out.  The usplash works up until services begin loading and then it drops back to a terminal based screen until it finishes and then it goes back to the desktop.

---

### Post by PatrickVogeli on 2009-05-04
could post the output of blkid, cat /etc/initramfs-tools/conf.d/resume and cat /etc/fstab please?

---

### Post by Deamos on 2009-05-04
> **PatrickVogeli said:**
> could post the output of blkid, cat /etc/initramfs-tools/conf.d/resume and cat /etc/fstab please?

blkid
```
/dev/sda1: UUID="CE029FFC029FE7AB" TYPE="ntfs" 
/dev/sda5: UUID="0b79dee8-0a66-4e03-b6c5-74f6a9e2bcc2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="94dde8a6-437e-4923-b2cc-890aa4482c3c" 
/dev/sdb1: UUID="B860D6FD60D6C0F4" LABEL="Games" TYPE="ntfs" 
/dev/sdc5: UUID="CC64883664882574" LABEL="Archive" TYPE="ntfs" 
```

/etc/initramfs-tools/conf.d/resume
```
RESUME=UUID=94dde8a6-437e-4923-b2cc-890aa4482c3c

```

/etc/fstab
```
proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=0b79dee8-0a66-4e03-b6c5-74f6a9e2bcc2 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=94dde8a6-437e-4923-b2cc-890aa4482c3c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc5 /media/Archive ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

### Post by PatrickVogeli on 2009-05-04
no idea then... all seems right there. Sorry

---

### Post by Elfy on 2009-05-04
> **PatrickVogeli said:**
> no idea then... all seems right there. Sorry

I have the same issue with a jaunty install and doing what you were thinking hasn't made any difference here even though the swap UUID was incorrect, still trying to get to the bottom of it :(


@Deamos - it might be worth checking that 

```
ls -al /dev/disk/by-uuid/
```

reports the same UUID for your swap - it didn't in my case

---

### Post by Deamos on 2009-05-04
> **forestpixie said:**
> I have the same issue with a jaunty install and doing what you were thinking hasn't made any difference here even though the swap UUID was incorrect, still trying to get to the bottom of it :(


@Deamos - it might be worth checking that 

```
ls -al /dev/disk/by-uuid/
```

reports the same UUID for your swap - it didn't in my case

From what I've eyeballed, all the UUIDs match up.  It almost seems that when the uSplash reaches the point where it gives the progress bar, it craps out and drops to text based.  As my Ubuntu-Fu is weak, I do not know exactly what handles the conversion of the boot process to usplash progress bar.

---

### Post by ANew on 2009-05-04
> **ajgreeny said:**
> OK, so what are these messages; if we know what they say, we may be able to help sort out the problem.

They look like this:

Loading boot files                                      [done]
Loading <something else>                                [done]
.......
whole page of them....

---

### Post by ANew on 2009-05-04
> **kpkeerthi said:**
> Can you post the contents of /boot/grub/menu.lst ?

it is the same as ** ajgreeny ** posted, only UUIDs are
different. 

However, this is not the problem of UUIDs, i have checked them
in properties and they match to one in menu.lst file.

As i said earlier, it happed after resizing the partition,
gparted does not change the UUID after resizing or does it?

---

### Post by Deamos on 2009-05-04
> **ANew said:**
> it is the same as ** ajgreeny ** posted, only UUIDs are
different. 

However, this is not the problem of UUIDs, i have checked them
in properties and they match to one in menu.lst file.

As i said earlier, it happed after resizing the partition,
gparted does not change the UUID after resizing or does it?

UUIDs change on resizing.

---

### Post by geirha on 2009-05-05
> **ANew said:**
> gparted does not change the UUID after resizing or does it?

No, it doesn't on "regular" filesystems like ext3 and ntfs, but swap filesystems does not get resized. If a swap partition is resized, it just creates a new swap filesystem to match the size, so the swapfs will have a new UUID. If the swap partition was untouched, it should have the same UUID as before.

---

### Post by Deamos on 2009-05-05
I have fixed my problem.  I am guessing it set some flag when I performed the resizing of my swap which caused usplash to crash back to the text boot.  I've been trying to find the post where the solution was posted, but I can't find it anymore.  

To correct:
Go to Add/Remove Programs
Install "Startup-Manager"
Run it, located in the System/Administration menu
Ensure that it is set to show boot splash & that show text during boot is not checked.
Then go to the appearance tab and make sure usplash-theme-ubuntu is selected.
Reboot and enjoy! :)

---

### Post by ANew on 2009-05-05
> **Deamos said:**
> UUIDs change on resizing.

No really, i checked them in properties before and
after resizing and they are the same.

No sure about the swap partition - will habe a look

---

### Post by PatrickVogeli on 2009-05-05
> **forestpixie said:**
> I have the same issue with a jaunty install and doing what you were thinking hasn't made any difference here even though the swap UUID was incorrect, still trying to get to the bottom of it :(


@Deamos - it might be worth checking that 

```
ls -al /dev/disk/by-uuid/
```

reports the same UUID for your swap - it didn't in my case
sorry!!! After changing the UUID to read the correct values, you have to do sudo update-mkinitramfs -u -k all

Could you try? thanks!

---

### Post by PatrickVogeli on 2009-05-05
> **PatrickVogeli said:**
> sorry!!! After changing the UUID to read the correct values, you have to do sudo update-mkinitramfs -u -k all

Could you try? thanks!
Just for to clarify, stupid me. The exact command was 'sudo blkid -c /dev/null' (without quotes).

I followed these steps and solved it:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5377919#post5377919](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5377919#post5377919)

---

### Post by Elfy on 2009-05-05
> **PatrickVogeli said:**
> sorry!!! After changing the UUID to read the correct values, you have to do sudo update-mkinitramfs -u -k all

Could you try? thanks!

Hi - I meant that I had done the update command and it didn't work - I tried again with your's and that gave an error, looking at the thread link you gave the command was ```
sudo update-initramfs -u'
```

Still no change though - but no matter I'm usually waiting for the kettle to boil while it boots :D

---

### Post by Deamos on 2009-05-06
> **forestpixie said:**
> Hi - I meant that I had done the update command and it didn't work - I tried again with your's and that gave an error, looking at the thread link you gave the command was ```
sudo update-initramfs -u'
```

Still no change though - but no matter I'm usually waiting for the kettle to boil while it boots :D

Did you try the solution I posted earlier in this thread?  Using the program Startup-manager, it corrected my issue with it dropping to text boot.

---

### Post by modmadmike on 2009-05-06
This usually happens if something goes wrong during the boot phase. Try to read the messages as they appear. If you see nothing then google how to enable boot logging in ubuntu, because i forgot. then print your /var/log/boot to this forum.

---

### Post by Elfy on 2009-05-06
> cat /var/log/boot
(Nothing has been logged yet.)

I have watched it :)

> Using the program Startup-manager, it corrected my issue with it dropping to text boot.nope no deal - but I wasn't expecting it to tbh - it doesn't do anything that manually editing the file doesn't do.

Personally I wonder if it's some odd thing going on with jaunty as update initramfs always worked previously :)

It really is no big deal for me - I only posted in the first place to mention that the fix PatrickVogeli was pointing at hadn't actually worked for me.

In a month or so the jaunty partition will be karmic anyway as I am a glutton for punishment :D

---

### Post by ANew on 2009-05-06
> **PatrickVogeli said:**
> sorry!!! After changing the UUID to read the correct values, you have to do sudo update-mkinitramfs -u -k all

Could you try? thanks!

I tried this and it does not solve the problem, all uuids
are correct. this is not related to uuids as i see.

i also have blinking screen on kubuntu shutdown and the
text messages on the screen appears on shutdown as
well but just a few
"unable to resolve ei (???)"

---


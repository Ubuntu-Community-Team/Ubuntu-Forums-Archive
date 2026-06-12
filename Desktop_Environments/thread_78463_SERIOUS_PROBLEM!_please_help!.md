---
title: "SERIOUS PROBLEM! please help!"
date: 2005-10-18
forum: Desktop Environments
---

### Post by fotisman on 2005-10-18
I can not get in ubuntu.

When i boot i see some fails:

Initializing ifupdown       [fail]
"file" readonly file system

Configuring network interfaces   [fail]
<the same>

Starting system log daemon...   (stucks here for 10 minutes)

Then a new screen comes up and says:

"I could not start the X server (your grafical enviroment) due to some interval error, contact your system admin or check your display to diagnose. In the meantime this display will be disabled, please restart gdm when the problem is corrected."

And then it asks for login.

Please Help me with this. I need my pc!
The last thing iu did before that: i addes utf8 in the options of my hard drive in fstab and reboot.


PLEASE HELP ME!

---

### Post by Stormy Eyes on 2005-10-18
Here's what you have to do:

1. Boot into recovery mode. While booting, press the escape key to get into the GRUB boot menu, and select the entry marked "recovery".

2. In recovery mode, run **nano -w /etc/fstab** and fix your /etc/fstab. Remove that utf8 option, and save using the prompts nano provides.

3. Reboot using "shutdown -r now".

4. While booting, press the escape key to get into the GRUB boot menu, and select the first entry.

Perform these steps, and you should be OK.

---

### Post by fotisman on 2005-10-18
I boot in recovery mode and while booting i hit the ESC key but nothing happens! However i write nano -w /etc/fstab i correct it but i cant save the changes! It says : read only file system!

Any ideas?

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=fotisman]I boot in recovery mode and while booting i hit the ESC key but nothing happens! However i write nano -w /etc/fstab i correct it but i cant save the changes! It says : read only file system!

Any ideas?[/QUOTE]

I do, but my idea requires the use of a bootable LiveCD, like the Ubuntu LiveCD or a Knoppix CD. Do you have one?

---

### Post by fotisman on 2005-10-18
Yes i have! Please help me quick its very important...
and thank you very much!!

---

### Post by Stormy Eyes on 2005-10-18
[QUOTE=fotisman]Yes i have! Please help me quick its very important...
and thank you very much!![/QUOTE]

OK. Boot with the LiveCD, open a terminal, and do the following:
```
mkdir /media/hd
```
```
mount -t ext3 /dev/hda1 /media/hd
```
Once you've done the above, attempt the following. If you're using the Ubuntu Live CD, I can't guarantee this will work, because I'm used to using Knoppix.
```
sudo nano -w /media/hd/etc/fstab
```

---

### Post by Murgle on 2005-10-18
I believe he will tell you to boot in with the liveCD and then change your fstab there.  you will neet to mount the drive most likely and then make sure that you edit the fstab on your harddrive and not the one for the liveCD in ram disk.  if you mount the harddrive with 'sudo mount /dev/hda /mountpoint' then type 'sudo gedit /mountpoint/etc/fstab' and change it there.

Edit: bah Stormy beat me to it...

---


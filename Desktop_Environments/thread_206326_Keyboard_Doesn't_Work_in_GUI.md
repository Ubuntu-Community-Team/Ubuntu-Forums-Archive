---
title: "Keyboard Doesn't Work in GUI"
date: 2006-06-29
forum: Desktop Environments
---

### Post by StylusPilot on 2006-06-29
[COLOR=Blue][COLOR=Navy]Hey guys,

I am a relatively new Linux user, and have the AMD64 version of Ubuntu installed on my PC. (Shuttle SN25P nForce 4)

Whenever I load up Gnome my keyboard doesn't work at all, it's a standard USB Keyboard with media keys (though I have also tried it with a PS/2 Adaptor to no avail).

However, if I load into the Ubuntu recovery mode my keyboard works fine.

Also, whenever I load the normal mode, If I keep pressing the Num Lock key on and off (to see when the keyboard is working and not) it is working right up untill the point where the login screen comes up, then it doesn't respond anymore.

How can I change the Keyboard driver that the GUI uses?

I have tried going into /etc/X11/xorg.conf and changing the driver there, but what should I change it too?

Currently the driver is set to "kbd" with "xorg" as the other setting.

I also tried the following command and tried re-detecting my keyboard through that.

dpkg-reconfigure xserver-xorg

Weird thing is it has been working fine up untill today, (I did however install some new updates last night, but can't  remember what they were)

Any help is much appreciated.

(I will be greatful to get out of this windows installation)

Cheers.[/COLOR]             
[/COLOR]

---

### Post by StylusPilot on 2006-06-30
[COLOR=Blue][COLOR=Navy]Anyone know of anything else I can try?

It's rather annoying being able to get to the login screen and have a working mouse, but not being able to type in a username and password [/COLOR] :(
[/COLOR]

---

### Post by StylusPilot on 2006-06-30
Well I can also log into Gnome from the recovery mode,

If I boot the recovery mode the keyboard works fine as mentioned, then I just type gdm and Gnome comes up and I can login and it works (albeit I have to start dbus too by typing /etc/init.d/dbus start) then Ubuntu acts as it should.

So why when I start the normal mode does my Keyboard not work? whats running or not running in the normal mode that isn't or is under the recovery mode?

So annoying to have to boot into recovery mode and run all that crap just to get into Ubuntu,

---

### Post by grooverider on 2006-06-30
boot into the live cd, check if ur keyboard works there as it should, copy the conf files onto ur harddrive after u mounted them in the live cd with 'sudo mount /dev/hda1 /mnt' (of course asjust the device accordingly to ur root device) then u can replace the files on the drive, which u mounted onto '/mnt' with the live cd conf files, shoudl work, good luck

---

### Post by StylusPilot on 2006-06-30
Problem is that I can't boot into the Live CD, it always freezes at "Starting Manual Drivers" I had to use the "Alternate" disk to install.

I tried the live cd on Flight 6 and the Final one and it did the same thing. (Both x86 and AMD64 do the same)

What about if I booted into another Distro's Live CD? would it use the same files for keyboard?

Isn't it weird thought that it works fine in recovery mode? even under Gnome, doesn't that use the same config files?

---


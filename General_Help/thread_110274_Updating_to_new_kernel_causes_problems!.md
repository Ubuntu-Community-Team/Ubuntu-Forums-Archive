---
title: "Updating to new kernel causes problems!"
date: 2005-12-30
forum: General Help
---

### Post by bigblop on 2005-12-30
I installed Ubuntu 5.10 (kernel 2.6.12-9-386). Then I installed "kubuntu-dekstop" so I can use some KDE apps in gnome. I also installed alsa pacakges because my sound card did not work with MP3 files.

I then afterwards got the message from the updating manager that new linux-headers where available (new kernel version) and I installed those.

I then got a new entry to the grub start menu

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

but when I choose that the following happens:
I get a Kubuntu spalsh screen when it boots (but when I get to the login screen it still the same old Ubuntu screen)...why?

No sound at all works not even the welcoming sound in gnome.

and I guess there is more thats screwed.

Has anyone else experienced problem when updating their kernel?

I only use the old kernel now because everything works fine there, is there any reason to use the new kernel when it causes all these problem?

---

### Post by ThePerg on 2005-12-30
[QUOTE=bigblop]I installed Ubuntu 5.10 (kernel 2.6.12-9-386). Then I installed "kubuntu-dekstop" so I can use some KDE apps in gnome. I also installed alsa pacakges because my sound card did not work with MP3 files.

I then afterwards got the message from the updating manager that new linux-headers where available (new kernel version) and I installed those.

I then got a new entry to the grub start menu

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

but when I choose that the following happens:
I get a Kubuntu spalsh screen when it boots (but when I get to the login screen it still the same old Ubuntu screen)...why?

No sound at all works not even the welcoming sound in gnome.

and I guess there is more thats screwed.

Has anyone else experienced problem when updating their kernel?

I only use the old kernel now because everything works fine there, is there any reason to use the new kernel when it causes all these problem?[/QUOTE]


as the saying goes... newer is not always better..  I would stick with what works for your system.. if you have the ability to either use VPC or VMware to create virtual systems and play with those first before modifying your production one, that would give the ability to see what fails and possibly how to fix it.. so if you do see it break on your good/production system you know what to do. ... anyhow.. just a thought...

---

### Post by bigblop on 2005-12-30
oh it seems that the windows 95 days are not over yet, when things screw up do a format/reinstall

---

### Post by ThePerg on 2005-12-30
[QUOTE=bigblop]oh it seems that the windows 95 days are not over yet, when things screw up do a format/reinstall[/QUOTE]

LOL I agree.. I think it will be a while till we see a true 'AS IT WAS' software/hardware setup.  Hell i still reformat and reinstall with XP 
But I use Virtual PC to create and play with linux I have one standalone Linux system that I dont upgrade except patches and what not. but its kernel is never messed with.

---

### Post by bigblop on 2005-12-30
Could be cool if these "potential destructive updates" had some kind of warning message instead of just adding them to the regular automatically update manger in gnome that updates your icons etc.

---

### Post by ThePerg on 2005-12-30
[QUOTE=bigblop]Could be cool if these "potential destructive updates" had some kind of warning message instead of just adding them to the regular automatically update manger in gnome that updates your icons etc.[/QUOTE]


True,, now there is a suggestion you could put in...

---


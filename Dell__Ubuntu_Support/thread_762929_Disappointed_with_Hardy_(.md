---
title: "Disappointed with Hardy :("
date: 2008-04-22
forum: Dell  Ubuntu Support
---

### Post by Kernel Sanders on 2008-04-22
I'm using the Hardy RC on a Dell XPS M1330 with 250GB HD, 2GIG Ram, 128mb Nvidia Graphics Card, and onboard intel wireless.

I was hoping to just install Hardy and have everything work out of the box. Instead I am unable to connect to ANY wireless network, even though they are detected fine. Secondly, I am unable to enable advanced desktop effects, I just get an error saying it can't be enabled.

I've tried opensuse, and both of these problems are fixed, only I don't have sound.

I have to say, since Ubuntu is being offered on Dell PC's, i'm surprised to see that my bog standard configuration does not work "out of the box" :(

Anyone else have problems with hardy that are not present in other Distros? :(

---

### Post by fatality_uk on 2008-04-22
It's only just gone to release candidate so I presume the build you were using was a beta and as such, you have to expect a few items are not going to work.

I have been using a beta for a while but went and got the RC today and it's rock solid.

All I could suggest is get the RC and try again.

Hope you get it sorted

---

### Post by aaaantoine on 2008-04-22
Sanders, maybe you should try Dellbuntu 8.04 when Dell finishes it up.  That should include drivers for at least some of your hardware.

An [example](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) of what I'm talking about.

---

### Post by Kernel Sanders on 2008-04-22
> **fatality_uk said:**
> It's only just gone to release candidate so I presume the build you were using was a beta and as such, you have to expect a few items are not going to work.

I have been using a beta for a while but went and got the RC today and it's rock solid.

All I could suggest is get the RC and try again.

Hope you get it sorted

Nope, as I stated, i'm actually using the RC, not the beta.


> **aaaantoine said:**
> Sanders, maybe you should try Dellbuntu 8.04 when Dell finishes it up.  That should include drivers for at least some of your hardware.

An [example](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) of what I'm talking about.

Cool, i'll give that a shot :)

---

### Post by bilal.17 on 2008-04-22
i had the exact same problems on my laptop when i upgraded

1. the internet wifi settings were reset on my laptop and the regular gnome app had trouble connecting to my wireless connection so i used a different app (wifi-radar) whcih worked perfectly
2. for compiz ... i dont remember exactly how it stoped working for me, but i think it was the fact that it stopped using the propietary graphics card driver so i had to reenable that

---

### Post by gletob on 2008-04-22
Try Installing WICD and see if that fixes Wi-Fi and Go to system>administration>Hardware Drivers and see if there is an unchecked Nvidia driver

---

### Post by K.Mandla on 2008-04-22
Moved to Dell Ubuntu support, where help should be forthcoming. :)

---

### Post by pbcartwright on 2008-04-23
I had to install an update to my intel wireless when I installed linux on my XPS laptop, but that was 2 years ago. Wireless wouldn't work then, and the update worked. Be sure to check and update all your firmware & bios.. and drivers..

---

### Post by eldersoares on 2008-04-26
I also have many problems with hardy! before, my gutsy was working perfectly and the upgrade from feisty was great...
this time, many things are not working: i cant login normally, only in gnome safe mode. sound doesn't work, wifi either. when i enter, it tells me there was an error with nautilus and bonobo activation...

i've tried dpkg-reconfigure -a, but it's still the same.
does anybody know how to solve this??? is there a way to make the upgrade process again? or should i downgrade to gusty? or maybe install hardy from cd....

thanks..

---

### Post by rhombus on 2008-04-26
I had the same bonobo/nautilus problem after upgrading from Gutsy to Hardy.

The only way I could get in was to start a session using the menu at the bottom-left of the login window and selecting Gnome failsafe mode.

I tried uninstalling all the Mono 1.2x packages from Synaptic (since Bonobo is part of Mono I guess) and tried reinstalling Nautilus, but neither helped.

After searching a while I realized that I had installed Mono 1.9 previously, and since I only formatted my OS partition and not the one reserved for my /home folder, somehow Mono 1.9 was still installed. There is an uninstaller in the Mono 1.9 folder. I ran that, rebooted, and I was able to start a normal session, no errors. I reinstalled Mono 1.2x from synaptic as well and everything has been running smoothly since then. I don't know if this is the case for everyone getting this error, but it helped me, so check if you have a wayward Mono 1.9 installation somewhere.

---

### Post by eldersoares on 2008-04-26
thank you very much rhombus, the problem was with mono, i had a old installation, version 1.2...
now i can login to gnome normally!!!!!!

BUT...
i still have some problems:
- when i trying to make things work, i followed a dell wiki ([http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)) that explained about sound issues. it was worst! before, the players didn't play but i could hear the gnome's sounds. now, any sound works and the volume control in notification bar has an "X". in system -> preferences -> sounds, there's no device to choose....
- another problem is with wifi that seems to work, but the led in my dell laptop (inspiron 6400) never turns on!
- when changing screen brightness through the keyboard, it jumps a very large step... i can't choose an intermediate brightness... only completely dark, medium or maximum bright

meanwhile, thats it!
thanks

---

### Post by rhombus on 2008-04-27
> **eldersoares said:**
> thank you very much rhombus, the problem was with mono, i had a old installation, version 1.2...
now i can login to gnome normally!!!!!!


Glad to help!

About the other stuff...well unfortunately I don't know. All the other stuff on my Dell Latitude C840 is pretty well supported by now (because it's old as time itself). It could be your built-in sound card uses an esoteric chipset that isn't fully supported, I'm not sure. Best of luck to you, though.

---

### Post by djdarrin91 on 2008-04-27
Install Hardy from a cd,my upgrade didn't turn out so well either so i did a fresh install from a cd and everything was fine.Good Luck:)

---

### Post by Denny Johnson on 2008-04-29
> **aaaantoine said:**
> Sanders, maybe you should try Dellbuntu 8.04 when Dell finishes it up.  That should include drivers for at least some of your hardware.

An [example](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) of what I'm talking about.

Anyone have an estimated release date for the Dellbuntu 8.04?

---


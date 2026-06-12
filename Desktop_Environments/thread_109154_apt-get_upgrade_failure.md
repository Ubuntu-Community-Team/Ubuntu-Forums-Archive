---
title: "apt-get upgrade failure"
date: 2005-12-27
forum: Desktop Environments
---

### Post by mrhaffer on 2005-12-27
Hello All - I have been trying for the past week to get Ubuntu going and I have a partial installation with some functions including internet but synaptic and add programs are not among the living.  I did a sucessful apt-get update from the recovery module using root but both the upgrade and dist-upgrade stall out at the third file X-common replacement "can't overwrite to /usr/lib/X11/fonts".  My xorg.conf file has path /usr/share/X11/fonts.  I have downloaded replacement files twice with same result.  The computer is an old HP PII 300MHZ.  Any simple way for a newbie to get past this problem?

---

### Post by az on 2005-12-27
How did you originally install?

---

### Post by mrhaffer on 2005-12-28
My original install was with an install cd and an ISA network card which was interrupted during installation of packages by some eth0 messages about mismatched read page pointers.  My second install was with the install cd and a wireless card.  Got a package installation hang again at about the same point.  Neither installation was complete.  Third install was with a preview disc iso back to ISA network card.  Got the internet access this time so decided to try to see if it could be bootstrapped into full functionality.  By the way I have also tried to get individual install of packages with apt-get and dpkg and I get a BUG thats reported on dpkg about it not being able to configure packages with circular dependencies.  I haven't figured out how to get the workaround provided to work yet.

---

### Post by ikki_72 on 2005-12-28
boot prompt b4 installing? i got that problem of not working synaptic and apt-get with expert. linux boot prompt will work fine. try.;)

---

### Post by az on 2005-12-28
[QUOTE=mrhaffer]My original install was with an install cd and an ISA network card which was interrupted during installation of packages by some eth0 messages about mismatched read page pointers.  My second install was with the install cd and a wireless card.  Got a package installation hang again at about the same point.  Neither installation was complete.  Third install was with a preview disc iso back to ISA network card.  Got the internet access this time so decided to try to see if it could be bootstrapped into full functionality.  By the way I have also tried to get individual install of packages with apt-get and dpkg and I get a BUG thats reported on dpkg about it not being able to configure packages with circular dependencies.  I haven't figured out how to get the workaround provided to work yet.[/QUOTE]


It is not a bug.  You cannot install packages with conflicting dependancies.  Apt is meant to sort that out for you.  If your network access is shaky, do not install from the network.

Since you have a pretty borked system, try reinstalling withtout network access.  Disconnect your network and install from the cd.  You will have a fully functioning system with just what is on the cd.  Try to fix your networking issues then.  After that, dist-upgrade to the newest packages from the network.

There is no reason you need to be on the net to install.

---

### Post by mrhaffer on 2005-12-29
Thank you for suggestions.  I tried a new boot with install disk using default.  Was not able to detect network cards.  Not able to assign root password.  Hung at 44% installing packages.  But did have synaptic at startup and terminal.  Had about 750 packages installed and 750 not installed with 3 corrupted and 15 broken.  used synaptic to manually install about 350 what appeared to be relevant packages.  Without internet go lots of errors about source lists and some packages.  Sudo works in terminal but I have 4 major problems.
1.  Need internet - have both a wireless card and ethernet.  Can see wlan0 and wifi0 in network manager.  Have tried to configure and activate to access point and seems to work but doesn't result in internet connection.  when I did the expert install I was able to select my ethernet isa card from a list.  Is there a way to do something similar?  wireless card is in hal but not isa
2.  Resolution is stuck at default 640X480.  Tried editing config file to 1024x768 and looked in xorg.conf which seemed to recognize Voodoo 3 video card.  Any quick fix for this?
3. broken apps - solutions to this probably need 1
4.  I think that some of the packages that show as installed may not be.  
I should be able to write an install manual when this is done.  Unless I have to wait for "creepy cobra".

---

### Post by mrhaffer on 2005-12-29
Forget to mention one other issue.  What is the root password on the default install?  By now you have probably figured out that this is my first pass at linux.

mrhaffer:confused:

---

### Post by mrhaffer on 2005-12-30
Here's an update - start with the easiest first

root access after default install - two ways - reboot in recovery mode -comes up in root no password required - or - use root passwd in terminal and set new password for root.

not able to change resolution - manually adding monitor hsync and vrefresh values to xorg.conf worked for me when reconfigure had all the right numbers but they didn't get to where they needed to be.  Found a great guide on this in how to forum.:smile: 

Still stumbling around in google and these forums to resolve internet problems with ISA card and wireless card implementation.

---

### Post by mrhaffer on 2005-12-31
Found my ethernet card.  Found the io and irq in windows.  Then did reboot in recovery and put in modprobe ne io=0x240 irq=5.  It told me there was no card at that address.  Then I put in modprobe ne and it found the card.  I went to sytem>admin>networking configured eth0 for DHCP and activated it.  Voila!!! Internet access being used to type this.  I can't believe it took me two weeks to puzzle this out.  When I have another week I'll try to resolve the wireless issue.

Now to see if I can update my system with synaptic.  Cautiously optimistic.  Stay tuned.:rolleyes:

---

### Post by mrhaffer on 2006-01-02
Turns out the ethernet solution needs to be done for every boot.

Got my broken packages fixed.  Synaptic said I had to install three packages.  One was corrupted and two had short read buffer error messages.  By deleting them from archive file, the program was forced to download new ones which installed correcting the 15 broken ones.  Open Office didn't work but I used Automatix loader to reinstall it and some other packages.  Worked well and openoffice now works.

Still trying to figure out wireless internet.  Would conclude Ubuntu not for casual user.  Might be good for new machine.:cool:

---


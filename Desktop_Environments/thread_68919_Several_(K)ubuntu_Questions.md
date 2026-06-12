---
title: "Several (K)ubuntu Questions"
date: 2005-09-24
forum: Desktop Environments
---

### Post by nrwilk on 2005-09-24
Hi, I've been interested in linux for a few years now, but have been yet unable to really get into it.  I'm now resolved to sit down and learn it, because I really like it a lot.

I first installed ubuntu on my PPC machine yesterday, and I instantly fell in love.  It's so much better than every other distro I've experienced (various Red Hat installs, my friend's SuSE box, a slackware install, and Yellow Dog Linux on my PPC machine).  But, I much prefer KDE, so I wiped and installed Kubuntu PPC Breezy v. 5.10.

I have a few issues that I would like to throw out there, and I'm sure there're a few people who can give me some answers.  I did my best to search on these subjects before posting, but I couldn't find any answers so far.  I apollogise if they have been answered already.

1.  When logging in, I get a pop-up window telling me about a SIGSEGV error caused by the soundserver.  Afterwards, the sounds still work, but this never happened the few times I booted up in ubuntu(gnome), so it freaks me out.  The only thing that is strange about it is that the startup sound sounds very distorted, but then all the following sounds are fine.

2.  I cannot get my Apple bluetooth keyboard to work.  I know there is a lot of documentation on this topic, and discussions as well.  But, they all seem to say something like:
> the Bluetooth drivers are installed by default, just reboot and it will detect your bluetooth peripherals
Well, it doesn't.  It sees my Bluetooth USB dongle, and if I click on the Bluetooth item in the system tray, it shows the keyboard in a Konqueror window named "Apple Wireless Keyboard," but it will not work.  Can anyone please give me any other explanation on means to get it working than the fact that it should just work right off-the-bat?

3.  When trying to add my printer to kprint via kcontrol, all the options for printer devices are grayed out.  I have made sure that my printer is on and connected.  I just need to select the "local SCSI, serial, or USB" radio button and then continue with the wizard.  But, that and all the other buttons are grayed out.  I tried doing it under administrator mode, but no dice.

4.  Probably not fixable, but I might as well give it a shot.  It is hard to live without my second monitor.  How can I configure it?  In Yellow Dog the Displays panel had an option for dual head configuration, but it didn't work for me.  I know this is sketchy for just about everyone.  Am I wrong?

5.  When logging in I get a dialog box saying:
> You may replace bluez's pin helper program with kbluepin; it is located in /usr/lib/kbluetooth now.
how can I replace whatever it is that I need to replace.  And, for that matter, what is it that needs to be replaced?

6.  Small annoyance, but I'm sure there's a way to fix it.  Whenever a new window is opened, it is always opened UNDER all the existing windows.  Even if it is a kdesu dialog, or something else of the sort.  How can I make new windows appear above the existing windows?

7.  When my USB key is hot-plugged, it shows up on my screen, but when I double-click the icon, I get an error saying that there is no /dev/sdb1 entry in either /etc/fstab or /etc/mtab.  I tried manually making an entry in mtab, but then I would get an error saying that it appeared to already be mounted.  When I tried this with my ubuntu install it mounted automagically with no problems.  Is there an option I can toggle for automount?  Something I need to configure?

8.  My time zone is correct, and whether I have it set to automatically set my time, or I manually set it, the time is always wrong.  It always thinks it is 5 hours and 15 minutes later than it should be.  Wierd!

Strangely, all of these issues (except the bluetooth and dual-head monitors) didn't occur when I had ubuntu installed, before Kubuntu.

Thanks so much for any help provided!  These forums are great!  People respond here faster than anywhere else I've participated.

Believe me, I've found a linux home with Kubuntu.  I love it.

---

### Post by mlomker on 2005-09-24
>   The only thing that is strange about it is that the startup sound sounds very distorted, but then all the following sounds are fine.

That part is normal.

Regarding your other problems...Breezy is a beta and the PPC and AMD64 versions are considerably more unstable than the i386 due to the number of people working on them.  I'd strongly recommend downgrading to Hoary until Breezy is formally released.

---

### Post by nrwilk on 2005-09-24
[QUOTE=mlomker]That part is normal.

Regarding your other problems...Breezy is a beta and the PPC and AMD64 versions are considerably more unstable than the i386 due to the number of people working on them.  I'd strongly recommend downgrading to Hoary until Breezy is formally released.[/QUOTE]


Would I notice a big difference?  I'm already kinda attached. hehe

Would this require a clean install, or could I downgrade via kynaptic?

---

### Post by ltmon on 2005-09-24
You may find some answers to your bluetooth issues at [http://kde-bluetooth.sourceforge.net/](http://kde-bluetooth.sourceforge.net/)

The main configuration file for bluetooth is in /etc/bluetooth/hcid.conf.  The documentation at the above address has an example configuration that I used without modification.

This has fixed (for me) the pin helper issue, and allows me to use bluetooth HCI profiles (in my case a phone controlling my media player, but it should be no different for a bluetooth keyboard).

Hope it helps.

L.

---

### Post by fordfan753 on 2005-09-24
[QUOTE=Fealos]7.  When my USB key is hot-plugged, it shows up on my screen, but when I double-click the icon, I get an error saying that there is no /dev/sdb1 entry in either /etc/fstab or /etc/mtab.  I tried manually making an entry in mtab, but then I would get an error saying that it appeared to already be mounted.  When I tried this with my ubuntu install it mounted automagically with no problems.  Is there an option I can toggle for automount?  Something I need to configure?
[/QUOTE]
I have limited kubuntu experience, so I don't know about automounting in KDE, but...OK, it told you that there was no entry in /etc/fstab or /etc/mtab . This should be easy to fix, by making an entry in /etc/fstab . The two files are related as I will explain...fstab shows a list of drives/partitions and where to mount them to (usually pre-existing folders in /mnt or /media) mtab, however, shows **which drives/partitions are currently mounted** which is why editting mtab would make the kernel think that it was already mounted. Mtab is not good to edit, stick with changing fstab.

[QUOTE=Fealos]
8.  My time zone is correct, and whether I have it set to automatically set my time, or I manually set it, the time is always wrong.  It always thinks it is 5 hours and 15 minutes later than it should be.  Wierd!
[/QUOTE]
Is your hardware clock set to GMT maybe? Or maybe local time, but it kubuntu thinks it's in GMT, either way that shouldn't be too hard. Have you got NTP support installed? NTP is brilliant if you have an always on net connection. If you need clarification just ask, good luck, and I admire your persistance!

---

### Post by nrwilk on 2005-09-24
[QUOTE=fordfan753]I have limited kubuntu experience, so I don't know about automounting in KDE, but...OK, it told you that there was no entry in /etc/fstab or /etc/mtab . This should be easy to fix, by making an entry in /etc/fstab . The two files are related as I will explain...fstab shows a list of drives/partitions and where to mount them to (usually pre-existing folders in /mnt or /media) mtab, however, shows **which drives/partitions are currently mounted** which is why editting mtab would make the kernel think that it was already mounted. Mtab is not good to edit, stick with changing fstab.[/quote]

hehehe, the reason I only tried editing mtab was because it looked more like I could edit it.  When looking at fstab I couldn't understand what I should include.  The man page was no help, it was pretty technical.  Or, I could be too tired right now.


[QUOTE=fordfan753]Is your hardware clock set to GMT maybe? Or maybe local time, but it kubuntu thinks it's in GMT, either way that shouldn't be too hard. Have you got NTP support installed? NTP is brilliant if you have an always on net connection. If you need clarification just ask, good luck, and I admire your persistance![/QUOTE]

Actually I do have it set to automatically set itself via NTP.  And the timezone is correct.  That's why it's so wierd.

Thank you for the help, and everyone else too!

I'll try that site for the bluetooth config file right now.

---

### Post by claydoh on 2005-09-24
The timezone issue is a known bug, which either is fixed after either after updating from the standard apt repositories, or upgrading to kde 3.4.2, I cannot remember which fixed it for me. [Here is another way to fix it as well]("http://kudos.berlios.de/kf/kisimlar/fixes.html#utcsticks")

---

### Post by nrwilk on 2005-09-25
[QUOTE=claydoh]The timezone issue is a known bug, which either is fixed after either after updating from the standard apt repositories, or upgrading to kde 3.4.2, I cannot remember which fixed it for me. [Here is another way to fix it as well]("http://kudos.berlios.de/kf/kisimlar/fixes.html#utcsticks")[/QUOTE]


Well, I am running 3.4.2, so I must need to update from the standard repositories.  Does this just mean installing all the updates from the standard repositories?  Because I've done that as well.  I'll try the other method, through that linky.

EDIT:  It worked! Thanks very much!

---

### Post by eddy-v on 2005-10-23
2. Apple wireless keyboard

try (im not sure if this is needed):
```
hidd -c some-address
```
(the addres is something like 00:0a:75:6a:bb:76)

to use your keyboard try:
```
/usr/bin/bluez-pin --dbus
```
The keyboard should work now.
Also check your hcid.conf in /etc/bluetooth

Good luck

---


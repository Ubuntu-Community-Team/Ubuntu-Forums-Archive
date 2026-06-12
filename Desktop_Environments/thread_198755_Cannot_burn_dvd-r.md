---
title: "Cannot burn dvd-r"
date: 2006-06-17
forum: Desktop Environments
---

### Post by LinuxConvertJune2006 on 2006-06-17
Hello all, this has been killing me all day. There was a bunch of auto updates this morning on my main Ubntu PC. In addition to that, I cracked open a new batch of DVD-R  RiDATA blank dvd's (16x). I burnt dozens on DVD+R's using my NEC burnewr and Dapper 6.06 in the past 2 weeks.

In researching this I found this closed thread:
[http://www.ubuntuforums.org/showthread.php?t=179846](http://www.ubuntuforums.org/showthread.php?t=179846)

I tried what was in this thread including re-install of latest Ubuntu dvd_rw tools AND install the dvd+rw-tools_6.1-2_i386.deb package manually. No luck using Gnome's "Write to Disc" for a good iso, or just plain jane files. Plenty of free space on disc.

After selecting Write to Disc I get a generic "Error writing to Disc" as the title and the body says "There was an error writing to the disc; unhandled error, aborting"

I tried using DVDDecryptor (under WINE) to burn an iso, no luck, I/O error. 

I tried multiple blanks, then used a friend's PC (and they work there) to rule out the new blanks.

I don't know if tihs is a DVD-R Dapper bug, or something as a result of the updates this morning (was a bunch).

I'm leaning towards Dapper DVD-R bug, anyone have any ideas or suggestions? I just bought 100 of these blanks!

---

### Post by LinuxConvertJune2006 on 2006-06-18
Anyone have any thoughts? Or ideas of where I could turn to for knowledge on this topic? In Googleing I've found other with this issue, are DVD-R's something the linux kernel can't handle (i.e. should I just eat my money loss on these blanks and buy DVD+R's?) or is burning DVD's in general broken after the latest updates?

---

### Post by jimbob on 2006-06-18
Sorry I cannot be of any real help as I don't burn very many DVD's at all but I can tell you those that I have done are DVD-R so I would say that at least you can rule out the kernel as being at fault.

Which other burning programs have you tried?  Have you tried K3b?

Also,  I assume your manual for the NEC says it will burn both +R's and -R's right?

I am a great believer in the command line to eliminate an extra layer of software while troubleshooting.  Read the man pages on dvdbackup, vobcopy and growisofs.  I burned a movie from my hard drive using the command:

  growisofs -speed=1 -dvd-compat -Z /dev/hdc -dvd-video /(full path to your file in here)

That might give you some clues while waiting for some more responses.

Sorry I can't be of more help.
________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB IDE 80 GB SATA
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by LinuxConvertJune2006 on 2006-06-18
Thank you for the reply! I will try your suggestions (command line).

To answer your question, yes this drive has burned -R's in the past. EDIT: Also to confirm, its burning plain jane files and ISO's of DVD's, nothing burns in any software I tried with DVD-R blanks.

What I have done in the meantime, I installed Kubuntu 6.06 on another seperate computer wit a brand new LiteOn LightScribe DVD burner. I didn't run updates since the wirelesss assistant doesn't automatically connect on boot, but I was able to get it connected after reboots and downloaded some files and used k3b to burn a DVD on that seperate computer. So that rukes our the blanks on Kubuntu (KDE).

So that leave Gnome on Ubuntu or the updates for Gnome/Ubuntu from Friday and lack of compatibility with -R's , or -R's and this NED burner (to reiterate +R's worked before the updates, don't have any on me now).

Anyway, I'd love to just copy the file from my Ubuntu PC to the working Kubuntu PC to burn them, but Samba doesn't seem to work either (full open share created on Kubuntu install, but getting access denied??). Anyway, I guess I'll have to go research that now as well....oh and I tried to get Nvidiai glx legacy drivers working, what a nightmare!

[vent on]
Talk about frustrating! I might have to back level to a different OS that's more stable, Ubuntu was great and it took a week to get all my linux and windows under WINE software running and configured, now this...it's just too frustrating. Seroiusly, its like using Windows all over again, nothing works!

[/vent off]

---

### Post by LinuxConvertJune2006 on 2006-06-18
To update, burning from command line doesn't work either, I get a generic "I/O error".

Anyone out there reading this, don't download the latest updates, or any updates at all on a fresh install if you want to burn anything. Or at the very least, use only +R's. 

Maybe somene out there with a fresh install and no updates (Gnome) can try some -R's and reply? 

In the meantime I'm trying to enable Samba or FTP or VNC and configure apache to allow files in /vaw/www to be downloaded all to no avail. I gave up on my "test" of only using GUI apps to configure, it seems hopeless now.

EDIT: it seems linux/Ubuntu doesn't support Belkin switch boxes either, X settings are all lost booting up connected to swich box and mouse jumps all over the screen like crazy. For those of you reading this, make sure you like unplugging a mouse/keyboard/monitor every single time you want to use your other systems before switcihng over.

---

### Post by IbeeX on 2006-06-18
Hi I also had problems with burning DVD disc, but at the end it looks like my DVD-RW disc is bad, I ca't bur it also on M$.
And I burned with no problem DVD even from Nautilus :)

---

### Post by LinuxConvertJune2006 on 2006-06-18
[QUOTE=IbeeX]Hi I also had problems with burning DVD disc, but at the end it looks like my DVD-RW disc is bad, I ca't bur it also on M$.
And I burned with no problem DVD even from Nautilus :)[/QUOTE]
Hi Thanks for your reply! Unfortunatley, burning in Ubuntu did work under Nautilus but after the "updates" it stopped, or it never worked with -R's. Are you using -R's or +R's with Nautilus ?

---

### Post by LinuxConvertJune2006 on 2006-06-18
[QUOTE=IbeeX]Hi I also had problems with burning DVD disc, but at the end it looks like my DVD-RW disc is bad, I ca't bur it also on M$.
And I burned with no problem DVD even from Nautilus :)[/QUOTE]
JUST and FYI also, burning regular CD-R's works just not the DVD-R's I have.

---

### Post by LinuxConvertJune2006 on 2006-06-19
In case anyone is wondering I went elsewhere ans found this:
[https://launchpad.net/distros/ubuntu/+source/dvd+rw-tools/+bugs](https://launchpad.net/distros/ubuntu/+source/dvd+rw-tools/+bugs)

It appears to be an Ubuntu bug.

---

### Post by sowdog on 2006-07-03
For a convert in june you're doing well. thanks for the research. i thought something was b0rked :)

---

### Post by keith whitehouse on 2006-07-03
hi,

I don't want to rain on anyones parade BUT, 

My Dapper Drake which is fully updated with every update available, burns dvd's. I have just inserted a blank dvd-r (tesco brand) and the cd/dvd creator -file manager pops up, I drag my file into it and select burn to disc. To verify the data on the disc I burnt 103 database files some of which have 500,000 records in them, I then imported the data back into a database to verify. Everything is ok.

I normally use bonfire for burning but I decided to go with the basic installed burning software.

The burner is a usb LG dual layer

best regards keith

---

### Post by keith whitehouse on 2006-07-03
a bit more rain maybe

I have just burnt the same data to a PCline dvd-rw using Bonfire and that works as well, and I have also burnt a cd-rw (tesco) and that works. I do not have any + discs to try.

best regards keith

---

### Post by maxfacta on 2006-10-04
Hey, did you get anywhere with this? no posts for a while now...
I just updated to Dapper last week (long time with no net connection), and suddenly couldn't burn DVD's anymore. I'm using DVD+R. I'm seeing a fair few reports of this issue on the forums, but can't find anyone who has reached a resolution...

---


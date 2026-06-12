---
title: "Ubuntu or Fedora?"
date: 2008-05-20
forum: Fedora/RedHat and derivatives
---

### Post by pancakelizard on 2008-05-20
Even though I've had horrible luck with the Live CD not working with Ubuntu, I've haven't had the chance to run 8.04 yet. However because of past experience with Ubuntu, I am willing to give it another shot. 

Actually, I would like to distance myself from Windows as much as I can. I've been programming alot for a job I've been having and rarely is Windows used, plus I would like to experience of knowing as much of Linux as I can. Alot of people at work say they have made it their main OS and rarely boot into Windows XP usually only to do their taxes, because TurboTax will not run.

It seems that for desktops, Fedora and Ubuntu are the two popular distros but I'm having trouble picking with one I would like to use. I can't test out ubuntu live cd because of my nvidia card. I also have not had a chance to burn the Fedora live DVD and try it so I can not speak the same for it as of yet.

Also as far as programs goes, I would found [this web site]("http://www.linuxalt.com/") that shows linux alternatives of certain programs however since multiples for some were mentioned, I was wondering people's preferences on which one to use:

Adobe Acrobat Reader
Adobe Photoshop
Cute PDF
APC PowerChute
CDex
iTunes
Office (I know of OpenOffice but heard that Lotus's New Version is suppose to be awesome).
mIRC
WinAmp
WS_FTP
Smart Mp3 Renamer
TorrentZip
Discjuggler
Last.fm Plugin
Newsleecher

I've already found the following - if there are better, please advise.
Nero Burning Rom - Nero for Linux
Pidgin - Pidgin
Snag it - Print Screen
Firefox - Firefox
Utorrent - Azuerus
clrmamepro - Works in WINE
DVDFAB - Works in WINE

My HP Printer should work with CUPS and I have a wired connection for my router/firewall so that won't be an issue. I've also never had an issue with my wireless keyboard and mouse with older versions of Ubuntu (even though they are MS products).

For my system drive, I will be using RAID 1 and for my storage drive, I will be using RAID 5. Has anyone had any problems with these and setup or the OS not detecting them?

Any help is appreciated. :)

---

### Post by meindian523 on 2008-05-20
> **pancakelizard said:**
> 
Also as far as programs goes, I would found [this web site]("http://www.linuxalt.com/") that shows linux alternatives of certain programs however since multiples for some were mentioned, I was wondering people's preferences on which one to use:

Adobe Acrobat Reader
Adobe Photoshop
Cute PDF
APC PowerChute
CDex
iTunes
Office (I know of OpenOffice but heard that Lotus's New Version is suppose to be awesome).
mIRC
WinAmp
WS_FTP
Smart Mp3 Renamer
TorrentZip
Discjuggler
Last.fm Plugin
Newsleecher

Do you mean you WANT alternatives for the above and a preference from the multiple options for the below?I guess so.
> **pancakelizard said:**
> 
I've already found the following - if there are better, please advise.
Nero Burning Rom - Nero for Linux
Pidgin - Pidgin
Snag it - Print Screen
Firefox - Firefox
Utorrent - Azuerus
clrmamepro - Works in WINE
DVDFAB - Works in WINE



Nero Burning Rom - Nero for Linux-->Brasero for GNOME/K3B for KDE
Pidgin - Pidgin-->My preference too
Snag it - Print Screen
Firefox - Firefox-->Same
Utorrent - Azuerus-->Deluge is getting rave reviews in the community too.
clrmamepro - Works in WINE
DVDFAB - Works in WINE

Dunno nothing about RAID.:)Also,except for the PSP part,I guess K3B should take care of anything you want to do with optical media.

---

### Post by iaculallad on 2008-05-21
As for the choice of either using Ubuntu or Fedora, choose the distro of where you feel comfortable most.

Or you could try a derivative of Ubuntu like Linux Mint.

---

### Post by sdennie on 2008-05-21
> **pancakelizard said:**
> 
Actually, I would like to distance myself from Windows as much as I can. I've been programming alot for a job I've been having and rarely is Windows used, plus I would like to experience of knowing as much of Linux as I can. Alot of people at work say they have made it their main OS and rarely boot into Windows XP usually only to do their taxes, because TurboTax will not run.


Unless you need games that won't run under Wine, there isn't any real reason to keep an XP partition around.  You can use virtualization software (VirtualBox, VMware, virt-manager, etc...) to run Windows within linux.  It's actually quite easy to use.

As for which distro to choose, I agree that you should try both.  I know that Ubuntu has a Live CD and I believe that Fedora does as well.  Grab them both and have a look at them and see which you prefer.

---

### Post by Inxsible on 2008-05-21
The default torrent client in Hardy is Transmission and it works really great for basic torrents. Unless you want some specialized functionalities on the torrents, I see no reason why you should be using anything other than that.  There is also another torrent program called rtorrent. Its a great lil app. Its command line based and really powerful especially since you can control it via ssh over a network.

---

### Post by lazyart on 2008-05-21
I installed Fedora on a machine last week for the first time.  I really liked the installer program.  Not sure how it compares to Ubuntu because I haven't done a fresh install since Feisty I believe.  It ships with the Gnome desktop so it's instantly familiar.

Try em both.  SELinux (a part of Fedora by default) can get in the way sometimes so you might want to turn it off while you kick the tires.  It's a security enchancement for Linux that I imagine will make it into Ubuntu one day.

---

### Post by Bakon Jarser on 2008-05-21
My preferences

Adobe Acrobat Reader - KPDF

Adobe Photoshop  -     Photoshop CS2 works in wine

Cute PDF             - Open Office

Office               - Open Office

WinAmp   - Amarok (may be an Itunes replacement if you don't buy songs)

TorrentZip  - Looks like there's a package build for Fedora, maybe that might help with your decision

Last.fm Plugin     - Amarok

Utorrent - Deluge

---

### Post by msrinath80 on 2008-05-21
Like most others in this thread, my recommendation is to try out both distributions and choose the one which best supports *all* your hardware. As for the programs, you should find the popular ones available on both distros. In Fedora, I guess all you will need to do is add the livna repository to yum and you're good to go!

PS: I switched from Hardy to Fedora 9 and I must say I love it!

---

### Post by Skeet on 2008-05-21
You could try installing Fedora on a spare partition (or partition a smallish one off as a sandbox environment) and then try Ubuntu 8.04 in VirtualBox (its free), that way you don't technically have to install both at separate times.

In fact I might install the latest Fedora in VirtualBox now, haven't tried it yet. Have to get used to the different console commands though. Yum etc.

:lolflag:

---

### Post by pancakelizard on 2008-05-21
Is there a way to install one Linux distro over another and not lose settings?

Such as if I install Fedora but start making preferences, folders, etc and decide I don't like it and wish to try Ubuntu?

---

### Post by sdennie on 2008-05-21
> **pancakelizard said:**
> Is there a way to install one Linux distro over another and not lose settings?

Such as if I install Fedora but start making preferences, folders, etc and decide I don't like it and wish to try Ubuntu?

That part is actually quite easy.  Just make a /home partition and mount it as /home on both distros.  Where you are going to run into problems is with grub.  Kernel updates from either side are likely to blast /boot/grub/menu.lst.  The easiest way to solve this problem is to just chainload to a partition based boot loader (grub to grub in this case).  I'm not a grub expert though, so I may be completely wrong.

---

### Post by crashcoredump on 2008-05-21
I have Ubuntu on my home box and Fedora 8 on my notebook. I like both fairly equally although I think some things just work in Ubuntu whereas in Fedora they take some massaging.

I use Ubuntu at home because a couple of friends told me that they thought, as a desktop client Ubuntu was superior.

I plan to upgrade my notebook to Fedora 9 this week. The screenshots look great. If your comfortable with both you may just flip a coin...:)

---

### Post by sw1995 on 2008-05-21
I'd love to have Fedora 9 on my notebook if for no other reason than a change of pace, however I could not get wireless working whatsoever which is deal breaker #1. I tooled around all day and night with ndiswrapper but I just don't have time beyond that.

---

### Post by Mortosa on 2008-05-21
I loved Fedora when i first tried it but the wireless issue was a major deal breaker for me as well since I do a lot of tech work and sometimes I remote in from my laptop.

Ubuntu may not look as nice as Fedora but everything worked for me without having to spend time tweaking it. I have really come to enjoy my Ubuntu laptop. It has served me well on trips.

---

### Post by Skeet on 2008-05-21
Unfortunately, no. You have to do a complete reformat, wiping the contents of the drive. Do as instructed above and

```
sudo apt-get install virtualbox
```

Install Fedora in that to test it out. If you can get Ubuntu installed that is.

---

### Post by lswest on 2008-05-21
> **pancakelizard said:**
> Is there a way to install one Linux distro over another and not lose settings?

Such as if I install Fedora but start making preferences, folders, etc and decide I don't like it and wish to try Ubuntu?

you can do that, if you make a seperate /home partition, your settings will be safe, and you can just boot back and forth between OSes (providing they use the same username) and have them both save preferences to your /home partition.  however, you will have to install the programs in each OS.  When installing make sure (when manually partitioning) to mount your /home partition as "/home" (without the quotes) and to not format it.

Also, i agree with what was said before, try out Fedora and Ubuntu, then choose which you like best.  I always found Fedora had 2 steps more that i need to take before having a system i would begin customizing, so i don't use it.  The two steps were adding the user to the sudoers file, and changing the file browser, since the default one opens each folder in a new window, and i didn't see the point in having to do 2 extra steps to get to an OS i could begin modifying, so i stick with Ubuntu or Mint or Arch, etc.

---

### Post by Skeet on 2008-05-21
Oh! Well there you go, you learn something new every day. I didn't know that!

:lolflag:

---

### Post by Antman on 2008-05-21
> **lswest said:**
> I always found Fedora had 2 steps more that i need to take before having a system i would begin customizing, so i don't use it.  The two steps were adding the user to the sudoers file, and changing the file browser, since the default one opens each folder in a new window, and i didn't see the point in having to do 2 extra steps to get to an OS i could begin modifying, so i stick with Ubuntu or Mint or Arch, etc.
A default sudoer entry seems to be something unique to Ubuntu (and derivatives). It's the only distro that I have seen that has it setup as default.

---

### Post by lazyart on 2008-05-22
The reason there is a default entry in Ubuntu is because by default the root account is disabled and you need some way to have super powers.

In Fedora (and from what I gather most any non-Ubuntu distro) you can just *su* and become root, so you don't really need sudo as much.

What caught me was using */sbin/ifconfig*. /sbin is not in the default path and when I just typed *ifconfig* it told me command not found.  I'm like WTF!?! No ifconfig! :)

---

### Post by mangurt on 2008-05-22
> **pancakelizard said:**
> 

Also as far as programs goes, I would found [this web site]("http://www.linuxalt.com/") that shows linux alternatives of certain programs however since multiples for some were mentioned, I was wondering people's preferences on which one to use:

Adobe Acrobat Reader
Adobe Photoshop
Cute PDF
APC PowerChute
CDex
iTunes
Office (I know of OpenOffice but heard that Lotus's New Version is suppose to be awesome).
mIRC
WinAmp
WS_FTP
Smart Mp3 Renamer
TorrentZip
Discjuggler
Last.fm Plugin
Newsleecher

I've already found the following - if there are better, please advise.
Nero Burning Rom - Nero for Linux
Pidgin - Pidgin
Snag it - Print Screen
Firefox - Firefox
Utorrent - Azuerus
clrmamepro - Works in WINE
DVDFAB - Works in WINE



There were some great suggestions for alternative programs.  Here's a few more.
Utorrent-deluge or ktorrent (both are great)
itunes-amorak
Winamp-vlc
newsleecher-PAN if you are grabbing headers, SABnzbd ([www.sabnzbd.org](www.sabnzbd.org)) if you are doing .nzb files and want to download and forget it
DVDfab-dvd:rip, acid:rip ffmpeg (depends on what you are are looking to do)

Hope that helps out.

---

### Post by igknighted on 2008-05-23
> **lazyart said:**
> The reason there is a default entry in Ubuntu is because by default the root account is disabled and you need some way to have super powers.

In Fedora (and from what I gather most any non-Ubuntu distro) you can just *su* and become root, so you don't really need sudo as much.

What caught me was using */sbin/ifconfig*. /sbin is not in the default path and when I just typed *ifconfig* it told me command not found.  I'm like WTF!?! No ifconfig! :)

Yes, it is not in the default path for anyone except the root user.    It's a conscious decision by the Fedora devs, essentially because if a command is in /sbin, you really need to be root for it to be useful (keeps people from trying to play with things they shouldn't).

Remember, 'su' only gives you root (or Super User) privileges.  If you want to actually _be_ root (and by extension have /sbin and all other commands in your default path) use 'su -' instead.  You don't need to type /sbin/<commandname> if you do it that way.

---

### Post by RiceMonster on 2008-05-23
> Last.fm Plugin

All of the linux audio players I've used so far have built-in last.fm support, so you won't even need the last.fm app, which has a native linux port available.

---


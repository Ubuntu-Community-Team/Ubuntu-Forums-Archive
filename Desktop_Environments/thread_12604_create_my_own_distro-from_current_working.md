---
title: "create my own distro-from current working"
date: 2005-01-25
forum: Desktop Environments
---

### Post by machiner on 2005-01-25
I think I saw somewhere, could even be in this forum, a how-to - or article about creating my own distro.

WHat I want to do is backup my schwiiiiiiiiiiiiiiiing setup (ubuntu/debian) to a bootable cd that will install the thing like a regular install cd for a regular distro.

Dooable, right?

Say I use partimage to back up my / directory -- instead of, or re-working the, .tar file that results fcrom the backup -- I want it to be burnable to a bootable disc.

I think I know how to do most of it -- naah, who am I kidding...

SOmeone know what the heck I'm talking about here?

---

### Post by dare2dreamer on 2005-01-25
You might want to have a look at mondo rescue.

[http://www.microwerks.net/~hugo/](http://www.microwerks.net/~hugo/)

It can build a bootable recovery cd with your custom kernel and tools, and then use either a fileserver or additional media to restore your system.

Personally, I just backup the critical files and mirror my home directory. I figure if I mess things up bad enough to have to bare metal restore, I probably am going to want to walk through the install and configurations again to see what I did wrong.

---

### Post by machiner on 2005-01-25
Man -- I have had NO luck with mondo in the past. Now I am chicken.

Thanks for your (damn quick) response.

If there is no other way, or one more complicated I'll probably try mondo again...but I'm leary.

Is there a way I can do it with a tar file of my / partition?

---

### Post by machiner on 2005-01-25
Look what I'm doing....

[http://www.madcarters.com/screenshot.png](http://www.madcarters.com/screenshot.png)

I think I can, I think I can...

---

### Post by dare2dreamer on 2005-01-25
You should be able to tar up anything you like as root, though personally I'm always a little leery of mucking with live filesystems.

I've pulled off tricks like you are describing by coming up on live cd's, and then doing the CLI tar -czvf dance over to some mounted share I had handy.

Considering that most of your system is pretty static, have you considered just backing up /etc and anything else you customize? I have one box I handle like that, and use the following trick to generate a record of everything I have installed on the machine:

How to replicate the installed packages of one system on another:

existing system:

```
# dpkg --get-selections > /floppy/selections
```


new system:

```
# dpkg --set-selections < /floppy/selections
# apt-get dselect-upgrade
```


The "selections" file is a plain text file, and can be edited to customize list of packages to install.

Once you have a list of packages you've installed, and a copy of all of your configs, there isn't much left you really need to backup.

I've found that the first thing you learn to do is install Linux, then you learn to break Linux, and then you graduate from the penguin academy by fixing Linux and learning how to make decent backups. :-)

---

### Post by machiner on 2005-01-25
Yeah -- I don't mess with live files either -- typically I boot to a rescue CD run partimage and BAM 13 minutes later I've got a terrific .tar file of my partition. Partimage rocks - and restore is amazing.

I wonder -- is there a way I could burn the .tar backup to a disk with the installation procedure as well - but code it to extract the .tar file and not ask me any questions?

THAT would rock.

I know this has to be dooable...

maybe I would have to copy grub and some other files with a .tar extract routine...


won't your cool floppy trick just back up a list of installed files? Won't I have to reinstall them anyway?

---

### Post by dare2dreamer on 2005-01-25
the floppy-selections bit will require a re-install, but the idea is you have a list of packages you can feed to dpkg so the process is largely automated. Bonus here is you end up getting a clean set of up-to-date packages out of the deal as well.

As for putting the necessary bits on a custom live-cd, I wouldn't see why you'd need more than a bootable kernel, enough tools to connect you to your data (drivers, networking tools, etc) and your tar/gz in order to create and restore the images.

Why not just custom up some low-footprint live-cd like damnsmalllinux and use the remaining space on the disc to hold your tgz file?

Regardless, please post about your ubuntu/mondo experiences.

---

### Post by az on 2005-01-25
I did the same sort of thing ages ago with a tool called bootcd.

Take a look at the packages in synaptic.  I do not know how they handle 2.6 kernel udevs and stuff.  I had to hack the initrd to autodetect the cdrom from which I was booting, but this was with a 2.4 kernel and ide-scsi.

The bootable cd it makes of your system includes scripts to write back your system onto another target drive.

---

### Post by machiner on 2005-01-25
I'm going to read up a bit on mondo/mindi and see how to incorporate my .tar file.

I think I can get this done and I'll absolutely do a write up.

Maybe I'll get to try it this weekend.

I want to explore the web a little as well.

Thanks for the input fellas...keep it comin'.

---

### Post by machiner on 2005-01-26
mindi requires too many deps and some want to remove my apps....I'll pass on this method for the time being.

I don't want to remove some ubuntu tweaked apps for debian and pull gnome and start all over.

It's still a process in the making.

---

### Post by xpt on 2005-01-26
[QUOTE=machiner]Yeah -- I don't mess with live files either -- typically I boot to a rescue CD run partimage and BAM 13 minutes later I've got a terrific .tar file of my partition. ...[/QUOTE]

I, IMHO, suggest that you take some time to read more before you dive into what you are doing. Yours is a good solution, but only good for your very own system. What if you have to install it into a brand new system, with entirely different HW. I bet this approach will give you more headaches than good. So, why spend time doing it if you know it will fail when you really need it? 

More over, what if you need to bring your CD system into a place where no installation possible, you need to rely entirely on live CD to perform your job? 

Think big, before you spend your time. I've wasted lots my own time doing such things and later find it is only good for one thing. 

FYI, I've been keeping an eye on such Live CD/Live working system/Customizse installation 3in1 system for quite a while. So far there is no solution yet (I might not be able to cover all). My best bet is bootcd, which has native package in Debian. However, it fails to recognize my SATA HD on my new AMD64 system. If I bet my luck there previously, I would have wasted some more time.

Just speaking off my own experience. Look before you leap. :-)

---

### Post by machiner on 2005-01-26
naah -- no worries. I'm pretty savy....although I respect your warnings. Sometimes I ask noob questions merely for examples. Hey now - I'm no linux expert, but 1's and 0's don't change their stripes much.

Yeah...this is for my system only - and I build systems for friends that use the same hardware, so if I needed to I could slap this puppy in their drives and all is good in OS land.

Besides, I never had any training other than "diving in". (I'm a freakin' bio major with 20 years sales/management/marketing...I'm a geek) It works quite well for me. If I can't figure it out after reading a bit (less and less)  and getting my hands dirty, then it's completly not for me.  Man, I HOPE I break stuff! When I started with win 3.1 it took me about a day before I started breaking things just so I could learn to fix them....all the way up to winxp, and now linux. I'm sure you know how that goes. Real learning doesn't come from books...ask my old science students.

The only production stuff I have on this box is websites...continually backed up, sealed, buried, super-ultra-mega-DELUXE taken care of.

Besides, I'm an Ubuntu Guru now.

Ba hahah.
Really - thanks.

PS-- but none of this means I won't ask for help. I'm all about community.

---

### Post by machiner on 2005-01-26
Know what I really want - even easier that what I will no doubt do soon --

I want a distro that asks me:

Do you have a .tar back up of a partition you would like to restore?

upon installation.

Akin to:
If you have any 3rd party drivers, now's the time to insert that disc.

I am sure that this is very simple to do. Just look at Debian's new installer - all those platforms.

Naah - this and some other ideas will be a piece of pie in short time.

Currently I employ a rescue disk with partimage. Works fine, but I want the whole enchilada.


"...better than sunshine
better than moonshine
damn sure better than the rain..."

---

### Post by machiner on 2005-02-01
UPDATE:

I have not approached the subject since my last post.

Being that the current backup solution I employ keeps me fabulous .. I will continue mucking with the OS - kernel, et al. as I rather enjoy configuring the install differently and trying to break the distro.

I renistalled my working ubuntu setup - completely differently than 2 weeks ago - I'm enjoying this more than attempting to create my own (hardware wise as well) personal quick-flip-distro.

However - as the idea suits an empiricle moment in the future - I'll probably bring this idea all the way to completion.

No doubt updates will follow.

Happy Computing

---

### Post by naurus on 2007-03-11
can anybody post the link to the thread that described this? i read about it somewhere else...

---


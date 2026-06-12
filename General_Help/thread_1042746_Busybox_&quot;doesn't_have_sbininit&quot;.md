---
title: "Busybox &quot;doesn't have sbin/init&quot;"
date: 2009-01-17
forum: General Help
---

### Post by Starman~ on 2009-01-17
I'll give this one more shot here. 

I've been using the Live Cd 8.04 fro a few weeks. Decided to take the leap and setup a dual boot system on my windows machine.

It worked okay. Hardy has been working for about a week. I got it all tweaked the way I like. I'm gonna add that the tweaking was NOT easy, and anyone who is selling ubuntu as user(beginner) friendly is selling cow pies. 

Anyway, I added some extensions to openoffice, loaded Kompozer, tweaked it some more and...  started it up a couple hours ago and got the busybox (I don't even know what the hell it is or how to use it) and it tells me "target doesn't have /sbin/init". 

I've read many posts trying to solve the issue for other users. I'm ready to just dump the thing and stick with my windows 2000.


I'm not computer illiterate, but I don't know linux. One curious thing. Since I can still boot into windows, I loaded the driver for ext2 formats. Oddly, it won't access my home partition. It asks me if I want to format it. 

So Hardy had been running for a week in dual boot and then it up and takes a dump.
If anyone has any really insightful options I'll give it one more try. Otherwise my only other question is "How do I get rid of the grub and restore my system to just windows?"

Sorry if I sound a little grumpy. I just spent a zillion hours learning how to tweak it the way I like it. 
My windows2k has been a rock, but getting old, which is why I gave Ubuntu a try. 
Thanks

---

### Post by sedawk on 2009-01-17
Seems like an important program, /sbin/init, is missing from your
root partition or your root partition is broken or the system is confused
about which partition is your root partition.

What happens if you boot using the Live-CD? Is the data on
the hard disk still okay, e.g. can you see the root partition
and files like /etc/fstab ?
Its hard to give further hints without knowing what went wrong ...

---

### Post by Starman~ on 2009-01-18
Thanx for the reply, needed to let it go for a bit.

I'm using the live CD as I type, it loaded fine.

Seems that most other posts regarding this issue were directed at issues with the install or CD itself. 

I'll Just add some system info:

Asus a7n8xe, Athlon(tm) XP 2600+
500 MB mem

120GB drive (partitions = 70Gb windows, 35gb extended w/ swap,/ = [hd0,5], & /home = [hd0,5])

I checked the menu.lst against the fstab for consistent entries and they are the same. 

The error in busybox says no "/sbin/init". Everything points to hd0,5. I confirmed that there is no "init" in /sbin. 

what should be there? Is there a file missing?

I think the issue is related to an update that synaptic wanted to do. There was a debian and unbuntu repository open at the same time and this caused errors when updating. I "forced" synaptic to replace the updates with earlier ubuntu packages. who am I kidding this is just a guess.

Can someone tell me what, where, and how to create or check on this "init" file?

PS: it just occurred to me to ask, is this file or folder archived somewhere? I did a search and I got  a lot of init's. I also tried to boot to an older kernel version and recovery version, they all do the same thing.

---

### Post by Starman~ on 2009-01-18
I can't get Ubuntu to boot, I'm done throwing time at it.

Can some explain or give me link to removing the grub and restore my MBR?

I'm wiping my disk and restoring the ext3 partition to ntfs.

My first cup of Ubuntu... I'll drink water

---

### Post by Starman~ on 2009-01-18
Ignore the request about MBR. I have the info I need to restore it to windows only.

That gives some sense of comfort, so I'll try to work this out for a couple more days.

I would greatly appreciate any insights in to recovery of this formally operable system. 

I tried the Live CD and copied the "init" and "initctl" files to /sbin. This got me past the busybox but I am confronted with this -

"**init: rc-default main process (5110) terminated with status 127**"

Any ideas?

---

### Post by mssever on 2009-01-18
It sounds like your system is seriously hosed. It's likely due to some of the customizations you made, where you probably made a mistake somewhere. The update process wouldn't have deleted init, since, as you've discovered, a Linux system can't run without init.

If you're willing to take the time and frustration, it might be possible to find out what's wring and fix your system. However, it'll probably be difficult. It would be a lot easier at this point to reinstall. If you created a separate /home partition, you shouldn't lose too many customizations.

Before reinstalling, you should consider backing up at least /home and /etc (the more the merrier) from the live CD environment.

EDIT: If you want to keep troubleshooting, please post the contents of /etc/event.d/rc-default.

---

### Post by Starman~ on 2009-01-18
Thanx, I did create a /home. I think I'll screw with it a while longer. I'm reasonably certain this occurred due to synaptic errors I saw. The most important lesson I got was that he advice in these forums can be absolutely bad advice. Too many quasi experts. I'm a noob, and can't sort the wheat from the chaff (yet).

rc-default
> # rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script

What's it say?

---

### Post by mssever on 2009-01-18
> **Starman~ said:**
> Thanx, I did create a /home. I think I'll screw with it a while longer. I'm reasonably certain this occurred due to synaptic errors I saw. The most important lesson I got was that he advice in these forums can be absolutely bad advice. Too many quasi experts. I'm a noob, and can't sort the wheat from the chaff (yet).
I think that few people deliberately give bad advise, but in many cases, you have the newbs leading the newbs which can lead to interesting (!) results. It wouldn't hurt to check out the official documentation for something before following advise, just to make sure it's sane. (While I'm not a newbie, you would do well to check out what I tell you, as well. :)) For terminal commands, the standard place to look for documentation is the manual page: ```
man command
``` Read "man man" for documentation on the manual. Note that the manual isn't written with newbies in mind, so it might be a while before you get used to it. For everything else, Google is a good source.
> rc-default


What's it say?
Nothing useful, unfortunately. I was hoping that it had somehow been corrupted, but alas, it's correct, so the problem is elsewhere.

Here are some other useful tools for exploring and recovering:

[LIST]
[*]chroot changes your root directory to somewhere else. You can use this in a live CD session to run commands as though you were booted into your normal install. You set it up this way (assuming /dev/sda1 is your / partition, and that it's formatted as ext3): ```
sudo mount -t ext3 /dev/sda1 /mnt
sudo chroot /mnt
```
[*]locate will quickly locate filenames containing the string given (i.e. "locate foo" will find all files whose name contains foo). locate uses an index for fast results, which you have to generate using "sudo updatedb" before you can use locate or before locate will notice changes to the filesystem. This tool could be useful from within a chroot environment.
[/LIST]
As far as fixing your system goes, if it were my system the first thing I'd try would be re-installing all the "essential" packages: ```
# from the chroot environment:
aptitude reinstall packagename1 packagename2
```I'm looking right now for where to get a list of essential packages.

---

### Post by mssever on 2009-01-18
> **mssever said:**
> I'm looking right now for where to get a list of essential packages.I didn't find a place to get that information, so I threw together a quick and dirty script for the purpose. I had my terminology a bit wrong, though. You should for sure re-install the required packages, and possibly the important packages. Here's the script: ```
#!/usr/bin/env python

import apt.cache
from optparse import OptionParser

parser = OptionParser()
parser.add_option('-i', '--important', dest="important", action="store_false", default=True, help="Don't show packages with the priority \"important\"")
parser.add_option('-r', '--required', dest="required", action="store_false", default=True, help='Don\'t show packages with the priority "required"')
parser.add_option('-t', '--terse', dest="verbose", action="store_false", default=True, help="List only package names separated by a space. Useful as an argument to another program")
(options, args) = parser.parse_args()

available_packages = apt.cache.Cache()
installed_packages = sorted([(i.installedPriority, i.name) for i in available_packages if i.isInstalled and i.installedPriority != 'optional' and i.installedPriority != 'extra' and i.installedPriority != 'standard' and i.installedPriority != ''])

if not options.important:
    installed_packages = [i for i in installed_packages if i[0] != 'important']
if not options.required:
    installed_packages = [i for i in installed_packages if i[0] != 'required']

if options.verbose:
    print "  Priority\tName\n  ========"
    for i in installed_packages:
        print "%10s\t%s" % i
else:
    for i in installed_packages:
        print i[1],
```Run it as "python scriptname". Pass the --help option for documentation. This would be best to run from the chroot environment. However, it doesn't have to be.

So, to reinstall all required packages, you could do something like this from a chroot environment: ```
aptitude reinstall $(python /path/to/the/script -ti)
```

---

### Post by Starman~ on 2009-01-18
mssever, thank you for your assistance. I feel like I may have whined a little too much. In any case I will attempt to carry out the suggestions you have made. It is possible I could screw up. Like I said I'm good with windows, but Linux is still very foreign to me. 

I'll post the results. If it doesn't go, I'll try one reinstall, start over.

---

### Post by Starman~ on 2009-01-19
mssever,

thanx for all your help. I ran through the instructions you gave. It seemed to do what it intended, but on boot I still get the init:rc-default message. Oh well. I learned a little about python in the process. 
Guess I'll give it a chance and reinstall. There was something I did within the parameters *allowed *by ubuntu. Obviously it should not have been done, but more importantly, ubuntu shouldn't have allowed removal or reconfiguration of such critical data without warnings. 
As such, I will be more careful in the future. Lesson learned. 

Thanx again

---

### Post by mssever on 2009-01-19
> **Starman~ said:**
> mssever,

thanx for all your help. I ran through the instructions you gave. It seemed to do what it intended, but on boot I still get the init:rc-default message. Oh well. I learned a little about python in the process. 
Guess I'll give it a chance and reinstall. There was something I did within the parameters *allowed *by ubuntu. Obviously it should not have been done, but more importantly, ubuntu shouldn't have allowed removal or reconfiguration of such critical data without warnings. 
As such, I will be more careful in the future. Lesson learned. 

Thanx again
I don't blame you for reinstalling, but I'm curious as to what caused your problem in the first place. If you were using GUI tools, there must be some bug somewhere, because those tools shouldn't allow you to destroy your system without warning. From the command line, it's a bit more complicated. The command line tools generally assume that you know what you're doing. And since there might be valid reasons for doing something potentially destructive, they'll usually let you do so. And power users generally don't like programs to bother them with warnings. So the question is, did you do something where there should have been a warning, or did you unknowingly misuse some tool? And furthermore, could the tool be modified to discourage misuse without impeding power users?

---


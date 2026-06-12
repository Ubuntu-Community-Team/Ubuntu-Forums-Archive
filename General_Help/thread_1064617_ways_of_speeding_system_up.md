---
title: "ways of speeding system up?"
date: 2009-02-09
forum: General Help
---

### Post by braveheart2 on 2009-02-09
besides overclocking and upgrading ram...how can i make my system run as fast as possible? system optimization tips of any kind would be awesome :)

---

### Post by kerry_s on 2009-02-09
lower the resource use, by that i mean use the lightest app's you can stand.
dump the desktop, use a window manager, that alone may give you enough to see speed in your programs. the best way is to just go custom from the start, install the base and add on from there with just what you use.
last resort would be to move to a faster distro, ubuntu is not as fast as others, it's not there goal.

---

### Post by mb_webguy on 2009-02-09
The fewer bells and whistles you use, the faster the gears will turn.

Your computer has a fixed amount of resources (barring opening up the case and adding more), and the quickest way to speed up your computer is to use fewer things at once, and use things that use fewer resources.  

You could turn off the fancy desktop effects.  You could use a more lightweight desktop environment, like Xcfe.  You could use more lightweight alternatives to your applications, such as Abiword instead of OpenOffice, and Thunar instead of Nautilus.  If you want real speed (at the cost of convenience) use a console login instead of a desktop environment.

As far as tweaks, you could try some of the ideas in [this article]("http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/").

And if you're really desperate to squeeze out every last bit of speed, you could [compile your own kernel]("http://ubuntuforums.org/showthread.php?t=311158").

---

### Post by zika on 2009-02-09
I've just discovered that my Intrepid 64-bit installation doesn't have /etc/inittab file. how come?

---

### Post by Neural oD on 2009-02-09
you also - for ease - if you're not to sure about tinkering with your system, might want to try a lighter distro. Try xubuntu or even fluxbuntu. If your sys is really old you might want to try puppy linux or the like

---

### Post by cariboo on 2009-02-09
@zika

Your statement has nothing to do with this thread, you should start a new one.

To answer your question /etc/event.d has taken the place of inittab in Ubuntu.

Jim

---

### Post by mb_webguy on 2009-02-09
> **zika said:**
> I've just discovered that my Intrepid 64-bit installation doesn't have /etc/inittab file. how come?

Some otherwise common system files that aren't used for anything in a default Ubuntu installation, and would be empty anyway, simply aren't created.  That article I posted the link to is very slightly dated (it's from April 2007), though the information is still good.  Since Edgy, Ubuntu has used something called Upstart as a replacement for the traditional inittab (which that article should mention, since it's based on Feisty).  If you create an inittab file, it will still work, since /etc/event.d/rc-default (which is the new method of dealing with runlevels since 6.10) checks for inittab.

---

### Post by zika on 2009-02-09
> **cariboo907 said:**
> @zika To answer your question /etc/event.d has taken the place of inittab in Ubuntu. Jim
thank You, I've managed to google that afterwards. I googled before I've asked but not thorough enough.

> **cariboo907 said:**
> @zika Your statement has **[COLOR=Red]nothing[/COLOR]** to do with this thread, you should start a new one.
I've asked a question that arose from following a link from this thread:in post #3, link: [http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/](http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/)...

---

### Post by zika on 2009-02-09
> **mb_webguy said:**
> Some otherwise common system files that aren't used for anything in a default Ubuntu installation, and would be empty anyway, simply aren't created.  That article I posted the link to is very slightly dated (it's from April 2007).  Since Edgy, Ubuntu has used something called Upstart as a replacement for the traditional inittab (which that article should mention, since it's based on Feisty).  If you create an inittab file, it will still work, since /etc/event.d/rc-default (which is the new method of dealing with runlevels since 6.10) checks for inittab.
I'm not sure if I'm allowed to thank You for the quick and detailed answer but, nevertheless, I will make that risk ... Thank You ... ;) 
my intention was to comment lines with tty3-tty6 and that I can not do by adding (creating) inittab ... ;) what would be the right way in this case, with upstart?

---

### Post by mb_webguy on 2009-02-09
> **cariboo907 said:**
> @zika

Your statement has nothing to do with this thread, you should start a new one.

To answer your question /etc/event.d has taken the place of inittab in Ubuntu.

Jim

Jim, zika's statement actually *is* relevant to the thread, because it was in response to my post, where I posted a link to an article that suggested freeing memory by disabling virtual consoles in inittab.

---

### Post by mb_webguy on 2009-02-09
> **zika said:**
> I'm not sure if I'm allowed to thank You for the quick and detailed answer but, nevertheless, I will make that risk ... Thank You ... ;) 
my intention was to comment lines with tty3-tty6 and that I can not do by adding (creating) inittab ... ;) what would be the right way in this case, with upstart?

You're welcome. :)

And to do the equivalent of what was suggested in the article using the Upstart method, I *think* you should edit the files /etc/event.d/tty3 through /etc/event.d/tty6 and comment out everything.  However, I'm not entirely sure about this, and haven't tried it myself.

---

### Post by zika on 2009-02-09
> **mb_webguy said:**
> You're welcome. :)

And to do the equivalent of what was suggested in the article using the Upstart method, I *think* you should edit the files /etc/event.d/tty3 through /etc/event.d/tty6 and comment out everything.  However, I'm not entirely sure about this, and haven't tried it myself.
I'll try this on a test machine ... ;) if I get some conclusive outcome I will report here ... :) thank You.

---

### Post by mb_webguy on 2009-02-09
I just tried it on tty6.  After a reboot, Ctrl+Alt+F6 just pulled up a black screen rather than starting a virtual console, which I think is the desired outcome.  My boot seemed to be a fraction slower, though that could simply have been because I was watching it closely in case something went wrong.  Deleting or moving those files might be a better alternative.

On the other hand, after looking at those files more closely, I think perhaps that with Upstart the virtual terminals might not be created until initiated by the user.  To be honest, this isn't an area where I have much experience.  I'm aware of Upstart, but I'm used to the old inittab method.

---

### Post by zika on 2009-02-09
my "solution" was to change "start" in those files to "stop" but I did not tried it yet. never mind, that 15M of memory will not make a difference that much ... ;) but, nice mental workout and a new thing I've learned. mathematicians, especially old ones are, difficult to comprehend ... ;)

---

### Post by adamlau on 2009-02-09
1. Choose the best hardware I can afford at the moment.
2. Always start with a minimal install off the minimal CD.
3. Install  a featherweight window manager such as JWM :) .
4. Compile as many kernel and userland apps as possible.
5. Focus on lightweight apps with as few dependencies as possible.
6. Rely heavily on bash aliases, functions and scripts.

mkfs.xfs -f -l size=64m,lazy-count=1 [COLOR="Indigo"][format to and tune xfs][/COLOR]

tmpfs /tmp tmpfs noatime 0 0 [[COLOR="Indigo"]/tmp on tmpfs and noatime for all mounts][/COLOR]

xfs_db -r /dev/sda(x)
	frag
xfs_fsr -v /dev/sda(x) [COLOR="#4b0082"][defrag fragmented xfs partitions][/COLOR]

/etc/default/console-setup [COLOR="#4b0082"][disable ttys][/COLOR]

/etc/sysctl.conf > vm.swappiness=0 [COLOR="#4b0082"][limit swapping][/COLOR]

sysv-rc-conf [COLOR="#4b0082"][disable unnecessary services and daemons][/COLOR]

.gtkrc-2.0 > gtk-menu-popup-delay = 0 [COLOR="#4b0082"][for GNOME][/COLOR]

/etc/dhcp3/dhclient.conf > prepend domain-name-servers 208.67.222.222,208.67.220.220; [COLOR="#4b0082"][use opendns][/COLOR]

/etc/modprobe.d/aliases > alias net-pf-10 off [COLOR="#4b0082"][disable ipv6][/COLOR]

That should about cover most of what a typical speed demon does to go faster ;) .

---

### Post by zika on 2009-02-09
done almost everything from the list with no numbers and have several more "tricks" I have to find details of in my black installation notebook hidden from everybody ... :lol:

do not understand tmpfs ... ? I've got it. thank You for the good thing to research on ... ;)

I've fond that a great thing is re-directing FireFox to write cache in /dev/shm ... nice reading and finger-gymnastics ... :lol:

a question for  ***adamlau*** : when I mount /tmp "Your" way do I have to remove /tmp from the disk...?  how do they cooperate?
(even though I have no idea how would I do that without making Ubuntu upset since at either the time I have /tmp on /dev/shm  or at the time it's on the disk, Ubuntu needs it, right?)
(I've simply put *tmpfs /tmp tmpfs noatime 0 0*in /etc/fstab, was that what I was supposed to do? according to *df*  and monitoring disk activity it works)

---

### Post by braveheart2 on 2009-02-09
> **mb_webguy said:**
> The fewer bells and whistles you use, the faster the gears will turn.

Your computer has a fixed amount of resources (barring opening up the case and adding more), and the quickest way to speed up your computer is to use fewer things at once, and use things that use fewer resources.  

You could turn off the fancy desktop effects.  You could use a more lightweight desktop environment, like Xcfe.  You could use more lightweight alternatives to your applications, such as Abiword instead of OpenOffice, and Thunar instead of Nautilus.  If you want real speed (at the cost of convenience) use a console login instead of a desktop environment.

As far as tweaks, you could try some of the ideas in [this article]("http://www.chinwong.com/index.php?/site/article/ubuntu_speed_up_tips/").

And if you're really desperate to squeeze out every last bit of speed, you could [compile your own kernel]("http://ubuntuforums.org/showthread.php?t=311158").

:mrgreen: thanks for the link, very useful! oh and i have found that the theme "high contrast invert" runs much faster,i also lowered all video settings and everything is going smooth now! yay.

---

### Post by braveheart2 on 2009-02-09
> **adamlau said:**
> 1. Choose the best hardware I can afford at the moment.
2. Always start with a minimal install off the minimal CD.
3. Install  a featherweight window manager such as JWM :) .
4. Compile as many kernel and userland apps as possible.
5. Focus on lightweight apps with as few dependencies as possible.
6. Rely heavily on bash aliases, functions and scripts.

mkfs.xfs -f -l size=64m,lazy-count=1 [COLOR="Indigo"][format to and tune xfs][/COLOR]

tmpfs /tmp tmpfs noatime 0 0 [[COLOR="Indigo"]/tmp on tmpfs and noatime for all mounts][/COLOR]

xfs_db -r /dev/sda(x)
	frag
xfs_fsr -v /dev/sda(x) [COLOR="#4b0082"][defrag fragmented xfs partitions][/COLOR]

/etc/default/console-setup [COLOR="#4b0082"][disable ttys][/COLOR]

/etc/sysctl.conf > vm.swappiness=0 [COLOR="#4b0082"][limit swapping][/COLOR]

sysv-rc-conf [COLOR="#4b0082"][disable unnecessary services and daemons][/COLOR]

.gtkrc-2.0 > gtk-menu-popup-delay = 0 [COLOR="#4b0082"][for GNOME][/COLOR]

/etc/dhcp3/dhclient.conf > prepend domain-name-servers 208.67.222.222,208.67.220.220; [COLOR="#4b0082"][use opendns][/COLOR]

/etc/modprobe.d/aliases > alias net-pf-10 off [COLOR="#4b0082"][disable ipv6][/COLOR]

That should about cover most of what a typical speed demon does to go faster ;) .

when i change the swappiness, will it stay like that after i boot?

---

### Post by zika on 2009-02-09
yes. you can, alternatively, edit that file and add the line *vm.swappiness=0* at the end.

---

### Post by Slim Odds on 2009-02-09
I know that you asked for other things than more memory, but that **IS** your problem.

A modern desktop GUI with 256M is always going to be a problem.

Get some more RAM, it's cheap.

P.S. I just bought a 1G chip for my machine for about $35

---

### Post by zika on 2009-02-09
I understood the OP's question as: overclocking and more RAM are obvious, are there others. not as if he wanted to escape upgrading RAM ...

I've benefited from this discussion even though I have memory more that I ever use (average usage is less than 40%) and gained considerably in speed simply by putting the unused memory in use. (FF's cache in RAM and /tmp in RAM).

afterthought: just because memory is retively cheap it is good to think as OP did. what we can achieve with it. tmpfs (with /dev/shm) is one of great places for that ...

---

### Post by braveheart2 on 2009-02-09
ok this is from Digitalife.com's Ubuntu tweaks: > Tip No. 1: Use that memory!
In an excellent three-part article, Tom Adelstein observes that for the longest time, Linux was used as a workstation or server rather than as a desktop operating system. Thus, the default settings that come with most distributions are not optimized for desktop PC systems.

One bottleneck, Adelstein says, is the tendency of Linux to use a swap file on the hard disk instead of RAM. Since the hard disk is 100 times slower than internal memory, this can slow things down considerably.

The tendency of Linux to go to the swap file is controlled by a variable called “swappiness” and the higher the number, the greater the tendency to go to the disk. To find out what the swappiness is on your machine, type the following in a terminal window (if you want to make sure you don’t make any typing errors, you can copy the line and paste it into the terminal window with Ctrl-Shift-V) :

sudo cat /proc/sys/vm/swappiness

Type your password and wait for the terminal program to come back with a number. If you have the default Ubuntu setting, it will say “60.” We want to lower that to 10 by typing this in the terminal window:

sudo sysctl -w vm.swappiness=10

To make sure the system always uses a swappiness of 10 on every boot, we’ll need to edit the sysctl.conf file in the etc directory. To do this, type:

sudo gedit /etc/sysctl.conf

This will call up a text editor with the configuration file. Find the line that says “vm.swappiness=60” and change the 60 to 10, taking care to change nothing else in the file. Save the file and you’re done.



i can't seem to do the last step where Im looking for the "vm.swappiness=60" and change it to "vm.swappiness=10" its no where in the config file....:confused:

---

### Post by zika on 2009-02-09
just add that line at the end of that file. You might want to use 10 instead of 0.
browser.cache.disk.parent_directory when set to /dev/shm in FF works great! with that and /tmp linked to that dir made my disk totally silent!

---

### Post by kerry_s on 2009-02-09
> **zika said:**
> just add that line at the end of that file. You might want to use 10 instead of 0.
browser.cache.disk.parent_directory when set to /dev/shm in FF works great! with that and /tmp linked to that dir made my disk totally silent!

i have a low ram laptop, 256mb ram maxed out.

i use:
```

vm.overcommit_ratio = 75
vm.dirty_ratio = 5
vm.swappiness = 1

```

i use to do that firefox tmp thing but in my case ram is to little, it would end up swapping more, in my case i disable disk cache by changing it to false.

---

### Post by braveheart2 on 2009-02-09
thanks Zika:guitar: im slowly doing all these techniques when i find the time, all are helping:KS

---

### Post by Slim Odds on 2009-02-10
Use RAID0 !!

---

### Post by braveheart2 on 2009-02-10
> **Slim Odds said:**
> Use RAID0 !!

:lolflag: i only have one 150GB IDE drive and im not upgrading anytime soon in this economy :)

---

### Post by zika on 2009-02-10
> **braveheart2 said:**
> thanks Zika:guitar: im slowly doing all these techniques when i find the time, all are helping:KS
good speed!

---

### Post by zika on 2009-02-12
I finally got to get rid of tty[3-6]. 
upstart-correct method would be to change ACTIVE_CONSOLES-"/dev/tty[1-6] to ACTIVE_CONSOLES="/dev/tty[1-2] but that did not work. tty[3-6] were stiil there.
next step was to rename /etc/event.d/tty[3-6] to /etc/event.d/tty[3-6].backup. no success.
next step was to move /etc/event.d/tty[3-6] to /etc/event.d/backup/tty[3-6]. no success.
finally what I've suggested in my previous post (#14) worked. simply change "start" into "stop" in /etc/event.d/tty[3-6].
I do not know why I did not believe myself and why I have tried all the other solutions but the one that I was confident that would work. maybe because I was more afraid to mess with the files itself than to move them around. respawn is a devil ... ;)
this doesn't help much in sense of speed but ... we tried ... :)
the biggest speed gain came from taking /tmp to tmpfs and taking FF cache to /bin/shm.
in the meantime I've tried also eliminating gdm from the loop with success but with downside: problems with accessing ntfs partition alive on my disk and acessing USB-Flash ... so I've put gdm back into the loop for now being. 
so much from me for today ... ;)
update: check with *env* if Your gtkrc file is not expected to be called gtkrc-2.0 but gtkrc-1.2-gnome2 as it is on my machine so change that accordingly to get faster menus in gnome. I had file ~/.gtkrc-2.0 on my machine for some time and I did not see any improvement. once I've noticed that the name should be ~/.gtkrc-1.2-gnome2 it worked. in order not to have this file owerwritten on upgrade set its contents to be ```
include "/home/zika/.gtkrc.mine"
``` and contents of file ~/.gtkrc.mine to be ```
gtk-menu-popup-delay = 0
``` nobody complained but it simply did not make a difference. now it does, believe me ... :)

---


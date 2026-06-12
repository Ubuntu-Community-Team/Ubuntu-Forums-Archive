---
title: "Linux kernel updated?"
date: 2006-01-18
forum: General Help
---

### Post by Thunk on 2006-01-18
When I logged into my Ubuntu today, the red update icon informed me of a new update to the Linux kernel. After installing it, it wanted me to restart my computer. Does anybody know what was updated in the kernel and where I can find out about what's going on in these updates?

---

### Post by earobinson on 2006-01-18
[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by Thunk on 2006-01-18
cheers!

---

### Post by Micro Rotors on 2006-01-18
Hmmm, 

I have never been asked to reboot my computer when ever I get my updates.

Bill

---

### Post by earobinson on 2006-01-18
99% of updates do not need a reboot in linux. kernel updates do, and are the only ones I can think of off the top of my head.

---

### Post by angkor on 2006-01-18
[QUOTE=Micro Rotors]Hmmm, 

I have never been asked to reboot my computer when ever I get my updates.

Bill[/QUOTE]

Well, you don't *have* to reboot right away, you can just finish your session running your old kernel. To boot into the new kernel you do need a reboot.

---

### Post by Micro Rotors on 2006-01-18
Hey What just happened,

I figured Id go ahead and reboot for the heck of it. Now when I boot up it says "edubuntu" instead of just "ubuntu" Also the list of check is not lit up as usual.

What happened?

Bill

---

### Post by lolcese on 2006-01-18
In my computer, I now have the kubuntu banner instead of the ububtu one, at boot time. Also, the new kernel didn't create a new entry in grub.

---

### Post by lolcese on 2006-01-18
In my computer, I now have the kubuntu banner instead of the ububtu one, at boot time. Also, the new kernel didn't create a new entry in grub, but replaced the current one.

---

### Post by scpike on 2006-01-19
i get the kubuntu banner too, weird

---

### Post by soonindallas on 2006-01-19
[QUOTE=Thunk]When I logged into my Ubuntu today, the red update icon informed me of a new update to the Linux kernel. After installing it, it wanted me to restart my computer. Does anybody know what was updated in the kernel and where I can find out about what's going on in these updates?[/QUOTE]

Updates are accompanied by an announcement in this forum:
[http://www.ubuntuforums.org/forumdisplay.php?f=20](http://www.ubuntuforums.org/forumdisplay.php?f=20)

Synaptic also gives you info on what is being updated and why and where it comes from.

---

### Post by ssam on 2006-01-19
for info about security updates see [http://www.ubuntuforums.org/forumdisplay.php?f=20](http://www.ubuntuforums.org/forumdisplay.php?f=20) or [http://www.ubuntulinux.nl/files/breezy.xml](http://www.ubuntulinux.nl/files/breezy.xml) (rss feed).

The reason that your splash screen changed is that when you install one of the ubuntu variants (edubuntu, kubuntu ...) the splash screen art work is not imidiatly updated. However next time you update the kernel the new art work is picked up.

i think this is already fixed in the dapper branch due to changes in the boot system.

possibly reinstalling ubuntu-artwork, and then reinstalling the kernel would set you back to the ubuntu splash screen

---

### Post by Zalbor on 2006-01-19
Ssam, your explanation is surely correct. I have installed xubuntu-desktop (still keeping ubuntu-desktop) and now my splash screen has changed to xubuntu. But your solution doesn't help, I'm afraid. I reinstalled ubuntu-artwork and then the kernel, and afterwards I tried the same with the usplash package. During kernel reinstallation, the console says "looking for a splash screen... none found, skipping" and xubuntu remains.

---

### Post by lapsey on 2006-01-19
for some reason, i only got this notification when i was in the user account i set up initially: the other account, despite given 'admin' status (as in, can use synaptic) didnt recieve the update info. 

any takers?

---

### Post by ozorba on 2006-01-19
[QUOTE=lolcese]In my computer, I now have the kubuntu banner instead of the ububtu one, at boot time. Also, the new kernel didn't create a new entry in grub, but replaced the current one.[/QUOTE]


If you have installed kubuntu-desktop after installing ubuntu this will happen. Even if you remove kubuntu-desktop you will still get kubuntu banner.

This happened to me a while ago.

---

### Post by lolcese on 2006-01-19
Thanks, but how can I get the original ubuntu banner?

---

### Post by Azion on 2006-01-19
Surely the banner doesn't make that much of a difference, i'm shure the lads at motu will sort out any problems

---

### Post by Micro Rotors on 2006-01-19
For me it went to edubuntu and now I can hardly see the list as things get checked out. Now I have to look very closely to see if stuff is Ok or Failed to initialize.

I want my old Ubuntu back.

Bill

---

### Post by lolcese on 2006-01-19
Of course, is not a big problem, but ...... I want my ubuntu back ;)

---

### Post by Azion on 2006-01-19
True point.
I had the same prob as you but mine went to kubuntu.
Strange thing is, mine's not even running the new kernel.
And I can't find it anywhere, lol

---

### Post by Micro Rotors on 2006-01-20
Well Then maybe something else is going on then, Could be it something bad? Have we been hacked?

---

### Post by Bob Ullet on 2006-01-20
Try this--

[http://www.ubuntuforums.org/showthread.php?t=76309&highlight=SPLASH+KUBUNTU](http://www.ubuntuforums.org/showthread.php?t=76309&highlight=SPLASH+KUBUNTU)


It worked for me.

---

### Post by Limulus on 2006-01-20
[QUOTE=Thunk]When I logged into my Ubuntu today, the red update icon informed me of a new update to the Linux kernel. After installing it, it wanted me to restart my computer. Does anybody know what was updated in the kernel and where I can find out about what's going on in these updates?[/QUOTE]

If you run Synaptic, there are a couple neat things.  First, go File -> History.  It will show the various packages that have been installed via it or the Ubuntu Update Manager arranged by date/time of install.

e.g. on my system on 01/18/2006 at 09:57, it upgraded several packages, including linux-image-2.6.12-10-686 from version 2.6.12-10.25 to 2.6.12-10.26

Now, if you click on a package, e.g. linux-image-2.6.12-10-686 then select Package -> Changelog, it will download the most recent changes (sometimes I've found they're not immediately available, but usually are within a day or two of the package showing up).  The changelog has all the changes that have been made (for that particular package, going back to May 25, 1997!).  The most recent change for that package is:

```

linux-source-2.6.12 (2.6.12-10.26) breezy-security; urgency=low

  Changed by Ben Collins:

  * [SECURITY]
    - CVE-2005-4605: procfs information disclosure

    - CVE-2005-4618: sysctl: don't overflow the user-supplied buffer with '\0'

    - CVE-2005-4639: dst: Fix possible buffer overflow

    - CVE-2005-3356: double decrement of mqueue_mnt->mnt_count in sys_mq_open

    - CVE-2006-0095: dm-crypt: zero key before freeing it

 -- Ben Collins <bcollins@ubuntu.com>  Thu, 12 Jan 2006 10:54:57 -0500

```

For more details, you can look them up on the "National Vulnerability Database" e.g. for that last one see [http://nvd.nist.gov/nvd.cfm?cvename=CVE-2006-0095](http://nvd.nist.gov/nvd.cfm?cvename=CVE-2006-0095)

---

### Post by breezyfox on 2006-01-20
Hi all 
I am new to this forum. just wanna know how to update to kernel
 when you just have server installed and no grapical display.
I have installed breezy in my old box that works fine and amazing.

any url to the updated repository pertaining to kernel update.

thanks guys you are doing wonderfull work.

bf

---

### Post by Bob Ullet on 2006-01-20
Oops sorry but my above post was not the one that I FOLLOWED.

Try this one--
[http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250)

---

### Post by ubuntu27 on 2006-01-20
You lucky guys, hehe :)

I cannot boot into Ubuntu no matter what kernel I choose...

See: [http://ubuntuforums.org/showthread.php?t=119567](http://ubuntuforums.org/showthread.php?t=119567)

---

### Post by nominal on 2006-01-20
[QUOTE=Thunk]When I logged into my Ubuntu today, the red update icon informed me of a new update to the Linux kernel. After installing it, it wanted me to restart my computer. Does anybody know what was updated in the kernel and where I can find out about what's going on in these updates?[/QUOTE]
i dont even have an update button...i think, where do u find the button...

---

### Post by lolcese on 2006-01-20
It worked, thank you Bob Ullet

---

### Post by Limulus on 2006-01-20
[QUOTE=breezyfox]just wanna know how to update to kernel when you just have server installed and no grapical display. I have installed breezy in my old box that works fine and amazing. any url to the updated repository pertaining to kernel update.[/QUOTE]
Well, first, [check](http://members.shaw.ca/Limulus/ubuntu.html#SynTer) that you have a complete set of Ubuntu repositories:

```

# Official Ubuntu Repositories
deb http://archive.ubuntu.com/ubuntu/ breezy main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-security main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main universe multiverse restricted

```

run **sudo nano /etc/apt/sources.list** at the command line to edit the system file that contains this info.

Then save any changes, exit and run **sudo apt-get update** to get the latest information from the server and then **sudo apt-get upgrade** to install the latest package upgrades.

That should do the trick! :)

---

### Post by Limulus on 2006-01-20
[QUOTE=nominal]i dont even have an update button...i think, where do u find the button...[/QUOTE]
It should show up automatically in the "Notification Area" of your Gnome Panel (if you don't have a NA, right-click in the Gnome Panel, click Add to Panel, scroll down to Utilities, click Notification Area and press Add).

If its not showing up there, go System -> Administration -> Synaptic Package Manager, press the Reload button and then the Mark All Upgrades button.  If it doesn't offer any upgrades, scroll to the *linux-image-2.6.12-10-386* package; under Installed version, does it say 2.6.12-10.26? or some other number?  If a different number, what does it say under "Latest Version"?

Also, check to make sure that you have your [repositories](http://members.shaw.ca/Limulus/ubuntu.html#SynTer) set up correctly.

---

### Post by az on 2006-01-20
[QUOTE=Azion]True point.
I had the same prob as you but mine went to kubuntu.
Strange thing is, mine's not even running the new kernel.
And I can't find it anywhere, lol[/QUOTE]

Your don't have the breezy-updates or security updates repositories active, then.

---

### Post by mishranurag on 2006-01-20
Same here dude!
Anurag

[http://www.ubuntuforums.org/showthread.php?t=120110](http://www.ubuntuforums.org/showthread.php?t=120110)

[quote=ubuntu27]You lucky guys, hehe :)

I cannot boot into Ubuntu no matter what kernel I choose...

See: [http://ubuntuforums.org/showthread.php?t=119567]("http://ubuntuforums.org/showthread.php?t=119567")[/quote]

---

### Post by dueY on 2006-01-21
[QUOTE=ssam]for info about security updates see [http://www.ubuntuforums.org/forumdisplay.php?f=20](http://www.ubuntuforums.org/forumdisplay.php?f=20) [/QUOTE]

How serious are these security updates?  Would an old kernel likely be exploited?

---

### Post by Limulus on 2006-01-21
[QUOTE=dueY]How serious are these security updates?  Would an old kernel likely be exploited?[/QUOTE]
As I recall, the severity of the security vulnerabilites it fixes are 'low', so they're not likely to be exploited... but its still considered a good idea to install it (otherwise they wouldn't have released it, ne?)

---


---
title: "slow shutdown Hardy Heron"
date: 2008-04-24
forum: Desktop Environments
---

### Post by adohall on 2008-04-24
Anyone else noticed that shutdown is very slow in Hardy Heron? I'm getting longish terminal-style message too before the splash logout image kicks in.

---

### Post by taiye on 2008-04-24
The same here. I getting a whole lot of messages about network manager before Hardy shuts down. I get a "checking battery state" message followed by a whole lot of stuff about network manager before it shuts down eventually. It takes the best part of a minute or so before eventually shutting down.

---

### Post by jesusfreak107 on 2008-04-25
I have that problem on Gutsy, errors appear about my network before shutdown and logo, yet my network card is fine.  I am using a PCI 10/100 Ethernet card, connected to a Wireless-N router, w/28-key WEP encrypt, on a 10Mb/s connection, if that helps any.

---

### Post by taiye on 2008-04-25
I uninstalled network manager and installed wicd. At least it's cleaned up my screen on shut down and restart.  Incidentally, wicd seems to give me a much better wireless connection.Still got the "checking battery state" message though and no improvement on the shut down time.

---

### Post by imbjr on 2008-04-25
Just to say: me too.

I used to notice those network errors, I think, when playing with a virtualised ubuntu install, but now they appear in a proper install.

---

### Post by sports fan Matt on 2008-04-25
How slow is it for you guys?

---

### Post by imbjr on 2008-04-25
It's variable, but once I thought the shutdown process had bricked itself.

---

### Post by loup on 2008-04-25
Since installing Heron last night I also observed a very slow shutdown. Mine seems to hang for a long time  on the following process: "running local boot scripts ((/etc/rc.local)".
That file, rc.local, doesn't contain anything!

---

### Post by adohall on 2008-04-26
Shutdown is quicker today. I presume that's because I was finally able to get through to the software servers for add-ons and updates. Perhaps Hardy was trying just one more time to make that connection yesterday, when I shut it down.

---

### Post by Hotwheelz79 on 2008-04-26
Hi adohall,

I have not noticed a slow shut down Hardy Heron it seems pretty reasonable 2 me.

I don't know if i'm missing anything but as I said seems fine 2 me.

I have tried it on 2 of my machines of similar speeds.

Thanks.

:-)

---

### Post by Quicky on 2008-04-26
Same problem with me - I get the > running local boot scripts ((/etc/rc.local) message and occasional warnings about network errors. Shutdown speed is extremely slow.

---

### Post by arbrandes on 2008-04-26
I can confirm Hardy's shutdown sequence is taking way too long.  I just upgraded from Gutsy, where there was no such problem.

I tried uninstalling network-manager because of the weird DBUS messages, but it did not solve the problem.  In hindsight, the network-manager messages appeared only AFTER 30 seconds of the machine seeming to hang.

There is another thread around here where the author seems to fix the problem by using binary drivers straight from Nvidia's site, as opposed to the restricted drivers from Ubuntu's repository.  I'd rather find another workaround, though.

---

### Post by adohall on 2008-04-27
Have we had some sort of silent update? Suddenly the terminal-style logout scripts have disappeared completely and I go straight to the splash image.

---

### Post by ingvildr on 2008-04-27
> **Quicky said:**
> Same problem with me - I get the  message and occasional warnings about network errors. Shutdown speed is extremely slow.

I had this exact problem with 32bit Ubuntu on my desktop and partners laptop, i changed to 64bit and i have no problems what so ever. I hope it gets fixed because i could get a sandwich waiting for the laptop to shutdown. Actually, another thing if i log on and then strait off again i still get text but it is nowhere near as slow.

---

### Post by adohall on 2008-04-28
I turned off print and bluetooth services at startup. I wonder if that had something to do with a sudden speed up in shutdown.

---

### Post by imbjr on 2008-04-29
> **adohall said:**
> I turned off print and bluetooth services at startup. I wonder if that had something to do with a sudden speed up in shutdown.


I turned off Bluetooth last night and the shutdown was faster. I'll have to do it without a lot of logging in and off first though - I was setting up others accounts and I know that such a process can have an effect on the system.

---

### Post by Belerophon on 2008-04-29
Same problem here.
Upgraded to hardy, and restart and shutdown are very slow. It hangs up on the tty log in console...
On gutsy, I also had those strange messages from network manager...

Thanks.

---

### Post by talent03 on 2008-04-29
> **loup said:**
> Since installing Heron last night I also observed a very slow shutdown. Mine seems to hang for a long time  on the following process: "running local boot scripts ((/etc/rc.local)".
That file, rc.local, doesn't contain anything!

+1 for me too. I have had the exact same problem. I also get the network error problems but everything runs just fine when I boot and everything else. I just have a big pause at the local boots scripts line when I shutdown.

<m1330 dell>

---

### Post by djf_jeff on 2008-04-29
Ok, a quick me too for me!

Hardy with latest update (29 april). Network manager seems to hang the shutdown...

---

### Post by imbjr on 2008-05-01
I thought the problem had gone away, but last night it had a nice long delay before shutting down proper.

---

### Post by Tom--d on 2008-05-01
I have been getting it when I upgraded to Hardy. Gusty never did it. 

Still finding out why.. and when I do.. I will post back here :)

---

### Post by Big Ben on 2008-05-02
I've got the same problem, even after doing a clean install.  
Hangs on "running local boot scripts (/etc/rc.local)" for about 30 seconds, then a bunch of error messages about network manager, then a brief flash of the splash screen, followed by normal shutdown.

Had no similar problems on this machine with edgy, feisty, or gutsy.

Has anyone filed a bug report on this?

---

### Post by Aearenda on 2008-05-02
Looks like [https://bugs.launchpad.net/ubuntu/+bug/222233](https://bugs.launchpad.net/ubuntu/+bug/222233)

---

### Post by Big Ben on 2008-05-03
The fix in [this thread]("http://ubuntuforums.org/showthread.php?p=4858236#post4858236") appears to have worked for me, as strange as the fix seems.

---

### Post by darkshado on 2008-05-03
same problem there is screenshot:

1)

[[img]http://uploads.imagup.com/03/1209810385_IMGP2597copie1.JPG[/img]](http://www.imagup.com/imgs/1209810385.html)


2)

[[img]http://uploads.imagup.com/03/1209810848_IMGP2598.JPG[/img]](http://www.imagup.com/imgs/1209810848.html)


3)

[[img]http://uploads.imagup.com/03/1209810874_IMGP2599copie.JPG[/img]](http://www.imagup.com/imgs/1209810874.html)

---

### Post by darkshado on 2008-05-03
Thanks **Greg T.** it work for me! :)

> Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.

---

### Post by EmyrB on 2008-05-04
As strange as it sounds I had the same issue until I decided I wanted to install the chrome usplash from Gnome Look. After I installed it via StartUp Manager the network manager output has gone away. Weird :/

---

### Post by imbjr on 2008-05-04
> **darkshado said:**
> Thanks **Greg T.** it work for me! :)

How many shutdowns have you done that now work?

I find that the problem is intermittent. Hopefully you have found the solution, but don't be surprised if it re-appears.

---

### Post by MikeyMike01 on 2008-05-04
> **imbjr said:**
> How many shutdowns have you done that now work?

I find that the problem is intermittent. Hopefully you have found the solution, but don't be surprised if it re-appears.

Just did 3 shutdowns in a row, and they all worked perfect after that fix, shutdown in under 10 seconds with the uSplash showing up from the start. 

:guitar:

---

### Post by imbjr on 2008-05-05
> **MikeyMike01 said:**
> Just did 3 shutdowns in a row, and they all worked perfect after that fix, shutdown in under 10 seconds with the uSplash showing up from the start. 

:guitar:

It's just that I read someplace (durn if I didn't keep the page ref) that the fix works but only for the current session. 

At the moment, my shutdown is also working - though I have not applied any fix.

---

### Post by TheMemphisExperience on 2008-05-05
On my newer ACER Aspire 5920, shutdown takes between 10-20 seconds. However, on my older Dell Optiplex 260, I get those same shutdown scripts that hang the operation. However, even with that, it only takes about 30-60 seconds to shutdown. At least the Dell shuts down with Hardy; with Gutsy, sometimes the computer would stay on in spite of the shutdown command being given and operations killed.

---

### Post by darkshado on 2008-05-06
yeah, but when you do a "ctrl+alt+backspace" the problem comes back! :(

---

### Post by BvanderWeerd on 2008-05-09
Thanks, this fixed a major annoyance!

> darkshado  	
Re: slow shutdown Hardy Heron
yeah, but when you do a "ctrl+alt+backspace" the problem comes back! 

I tried the "ctrl+alt+backspace" and didn't experience any problems. Perhaps you forgot to edit the 'reboot' command?

---

### Post by run1206 on 2008-06-05
i edited both shutdown and reboot commands and i still hang at shutdown.... :(

---

### Post by mrollie on 2008-06-09
I found that not starting BlueTooth Manager in System-Preferences-Session Preferences has fixed the no shutdwon problem for me.  My older Toshiba (A-35 S209) laptop does not have Bluetooth and by un checking the option the shudown is quicker and does not seem to hang.

Ollie:)

---

### Post by run1206 on 2008-06-09
deactivated Bluetooth manager; no go :(

i notice when i restart or shutdown, gvfs fails to unmount (looked on task manager and saw it's an image to my physical HDD). i wonder if there's anyway to deactivate that "virtual" filesystem (didn't see it if edgy, feisty, or gutsy) :?

thanks in advance

---

### Post by run1206 on 2008-06-09
SOLVED!!!!  not using the Bluetooth service did in fact get my laptop to shutdown properly :D 

thanks mrollie!!! :D

---

### Post by feld on 2008-06-10
> **run1206 said:**
> deactivated Bluetooth manager; no go :(

i notice when i restart or shutdown, gvfs fails to unmount (looked on task manager and saw it's an image to my physical HDD). i wonder if there's anyway to deactivate that "virtual" filesystem (didn't see it if edgy, feisty, or gutsy) :?

thanks in advance

gvfs is from gnome. it's needed to replace the old system gnome used to use... can't remember what it was called right now. Anyway, this gives gnome/nautilus way more features and performance in certain areas.

---

### Post by run1206 on 2008-06-10
yeah what bothered me what that in the task manager i saw another drive with the same specs as the original drive, yet when i shutdown through terminal, it wouldn't unmount, i guess it isn't supposed to :?

---

### Post by blackmachine on 2008-06-12
Try this. It worked for me :) ```
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3")
```

---

### Post by run1206 on 2008-06-12
> **blackmachine said:**
> Try this. It worked for me :) ```
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3")
```

wow, this causes Ubuntu to shutdown unbelievably quick!! :shock: :D thanks blackmachine!

---

### Post by ene_dene on 2008-06-23
I can't shut down or restart a comp in Hardy, it always comes to cursor in top left corner. Nothing works for me. Is there any possibility that there will be released some official patch since lot of people are suffering from this problem? Is anyone working on that bug?

---

### Post by run1206 on 2008-06-23
> **ene_dene said:**
> I can't shut down or restart a comp in Hardy, it always comes to cursor in top left corner. Nothing works for me. Is there any possibility that there will be released some official patch since lot of people are suffering from this problem? Is anyone working on that bug?

i used the fix for the hanging of NetworkManager (one of the members here posted the link will try to find it later on).  snce i use wicd for managing my wireless and wired networks, i turned it off and it solved my shutdown problem.

edit: actually, it's the fix right above your post: #41 i used and it worked. try it and let us know if it works for you.

---

### Post by ene_dene on 2008-06-23
I'm not sure that network manager is a problem.

I've tried the solution provided on [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/183568/comments/3) but I'm not sure if I did it correctly:
This part I understand:
> Modify /etc/dbus-1/event.d/25NetworkManager as follows (just add the --signal 9 option)

d_stop() {
        # Modified MF 11 Feb 2008 To avoid NM hang
        #start-stop-daemon --stop --retry 60 --quiet --pidfile $PIDFILE \
        # --oknodo --user $USER --exec $DAEMON

        start-stop-daemon --stop --signal 9 --retry 60 --quiet --pidfile $PIDFILE \
                 --oknodo --user $USER --exec $DAEMON
}
But I'm not sure about this part:
> Modify /etc/init.d/sendsigs as follows
...
        # Kill all processes.
        log_action_begin_msg "Terminating all remaining processes"

        # Added MF 11 Feb 2008 To avoid shutdown hang
        OMITNM=
        if [ -f /var/run/NetworkManager/NetworkManager.pid ]; then
                OMITNM=$(cat /var/run/NetworkManager/NetworkManager.pid)
                OMITNM="-o $OMITNM"
        fi
        echo "Not killing $OMITNM"

        killall5 -15 $OMITPIDS $OMITNM

        # END MF mods
        log_action_end_msg 0
...
Do I need to replace the whole file with this text (which I tried and it didn't work) or do I have to add this to some specific place in that file (I've added it to the end, and it didn't work)?

Here's how my /etc/init.d/sendsigs looks like unmodified:
```
cat /etc/init.d/sendsigs 
#! /bin/sh
### BEGIN INIT INFO
# Provides:          sendsigs
# Required-Start:    
# Required-Stop: 
# Default-Start:     6
# Default-Stop:       
# Short-Description: Kill all remaining processes.
# Description: 
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin

. /lib/lsb/init-functions

do_stop () {
	OMITPIDS=
	if [ -e /var/run/sendsigs.omit ]; then
		for pid in $(cat /var/run/sendsigs.omit); do
			OMITPIDS="${OMITPIDS:+$OMITPIDS }-o $pid"
		done
	fi

	if [ -d /var/run/sendsigs.omit.d/ ]; then
		for pidfile in /var/run/sendsigs.omit.d/*; do
			[ -f "$pidfile" ] || continue
			for pid in $(cat $pidfile); do
				OMITPIDS="${OMITPIDS:+$OMITPIDS }-o $pid"
			done
		done
	fi

	# Kill all processes.
	log_action_begin_msg "Terminating all remaining processes"
	killall5 -15 $OMITPIDS
	log_action_end_msg 0
	sleep 5
	log_action_begin_msg "Sending all processes the KILL signal"
	killall5 -9 $OMITPIDS
	log_action_end_msg 0
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	if which usplash_down >/dev/null; then
		usplash_down
	fi
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

```
If someone who understands the second part of solution knows how to modify the file, please paste it here and I'll paste it back to my file.

---

### Post by run1206 on 2008-06-23
code should look like this:
```
cat /etc/init.d/sendsigs 
#! /bin/sh
### BEGIN INIT INFO
# Provides:          sendsigs
# Required-Start:    
# Required-Stop: 
# Default-Start:     6
# Default-Stop:       
# Short-Description: Kill all remaining processes.
# Description: 
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin

. /lib/lsb/init-functions

do_stop () {
	OMITPIDS=
	if [ -e /var/run/sendsigs.omit ]; then
		for pid in $(cat /var/run/sendsigs.omit); do
			OMITPIDS="${OMITPIDS:+$OMITPIDS }-o $pid"
		done
	fi

	if [ -d /var/run/sendsigs.omit.d/ ]; then
		for pidfile in /var/run/sendsigs.omit.d/*; do
			[ -f "$pidfile" ] || continue
			for pid in $(cat $pidfile); do
				OMITPIDS="${OMITPIDS:+$OMITPIDS }-o $pid"
			done
		done
	fi

	# Kill all processes.
	log_action_begin_msg "Terminating all remaining processes"
        
        # Added MF 11 Feb 2008 To avoid shutdown hang
        OMITNM=
        if [ -f /var/run/NetworkManager/NetworkManager.pid ]; then
        OMITNM=$(cat /var/run/NetworkManager/NetworkManager.pid)
        OMITNM="-o $OMITNM"
        fi

        echo "Not killing $OMITNM"

	killall5 -15 $OMITPIDS
	log_action_end_msg 0
	sleep 5
	log_action_begin_msg "Sending all processes the KILL signal"
	killall5 -9 $OMITPIDS
	log_action_end_msg 0
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	if which usplash_down >/dev/null; then
		usplash_down
	fi
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

```

---

### Post by ene_dene on 2008-06-23
Unfortunately it doesn't help I still can't restart or shutdown computer without pressing a button.

---

### Post by run1206 on 2008-06-23
there's also a command that lets you go to a program that changes what you want to run at startup and shutdown: works with rc.0 and rc.6 (forgot what the command was ...sys-[something]-conf :?  )

the only other thing i can think of is a tutorial on shutdown procedures:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialInitProcess.html)

sorry i couldn't help you much, didn't bring the linux laptop to work today :(

edit: you could use the package "bum" (boot up manager) and delete the process that might be giving you your shutdown problem.

---

### Post by ene_dene on 2008-06-23
OK, thanks anyway. Hope they'll fix this bug in next version of Ubuntu.

---

### Post by Aearenda on 2008-06-23
ene_dene: the only time I've seen a system completely stop with just the cursor flashing at top left when it should have shut down, it was because the hardware was weird and needed to be powered off differently, e.g. using APM instead of ACPI. I suspect you are seeing a different problem than this thread is about. To prove it, you could do this:
1. Prevent GDM starting after boot: 
```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm
```
On some systems the number in the name of the link (30 here) is different.

2. Reboot so that you come up with the console only.

3. Login to the console and use 'sudo halt' to close down again.

Does the system hang in the same way? If it does, then I think you need to look at kernel parameters and ACPI/APM issues. If not, then I'm wrong about this, and we need to look elsewhere.

To put things back to normal, do this when logged in to the console:
```
sudo mv /etc/rc2.d/K30gdm /etc/rc2.d/S30gdm
```
Then reboot, or do```
sudo /etc/init.d/gdm start
```

By the way, I wouldn't recommend expecting that "they" will fix your problem. In the open source world, it is "we" who should be working to fix your problem, either by finding a workaround, or by logging a bug in Launchpad for developer attention after we have exhausted other avenues.

---

### Post by ene_dene on 2008-06-24
> **Aearenda said:**
> ene_dene: the only time I've seen a system completely stop with just the cursor flashing at top left when it should have shut down, it was because the hardware was weird and needed to be powered off differently, e.g. using APM instead of ACPI.
This observation helped me to solve the problem and I thank you for it. I've written a script that has something to do with ACPI and it seems that it didn't shut down properly. The reason that I thought that it was Ubuntu problem was that I had another laptop that had shutdown problem in Hardy, It just wouldn't shut down, but I remember now that there was something else on a screen than cursor in upper left corner. It was problem with ATI cards or something like that. This laptop with nvidia, didn't had such problem until recently but it also took extremely long time to shut down, and I figured that the problem repeated it self (my past experience and lot of people having a problem with shutdown).

> By the way, I wouldn't recommend expecting that "they" will fix your problem. In the open source world, it is "we" who should be working to fix your problem, either by finding a workaround, or by logging a bug in Launchpad for developer attention after we have exhausted other avenues.
I agree with you, however there are some exceptions. One of the goals of projects like Ubuntu, all modern desktop Linux distributions is to attract all the people and also to show that there is a good alternative for MS products. Now, for example I've explained to my dad, which is 55, starting using computers 5 years ago, all this wonderful stories how Ubuntu is cool and that he can do all the stuff he did on Windows and he will be even more secure, bla, bla. And I know that it is true, but for him, and many like him it all comes down to simple comparison "I could shut down comp in windows, I can't shut it down now". He just wants to be able to start comp, check mail, write something and shut down. If one of these basic things he can't do without reading lot of materials,writing few posts, rewriting some config files then all arguments for Ubuntu fail. Ok, this was purely my mistake, but if he had my other laptop or any of the computers from this thread he could not use it, and he is an average comp user. Another example is my girlfriend which has Asus laptop, on which I've installed Gutsy and she impressed, she could do it all without ever seeing command line. Then we upgraded to Hardy and wireless stopped working and we could not find and solution for the problem, so we went back to 7.10.
The point is, we should all try to help to develop open source, by reporting a bug or fixing it. But some basic things like shutdown or things that worked perfectly in previous version and don't work now should not happen (and we have a well visited thread on this problem). If that problem happens to a beginner or average comp user the most probable scenario is that he/she will go back to Windows. Also, lot of people can't even ask for help, they don't know English and in their country Linux is not well supported.

---

### Post by Aearenda on 2008-06-24
I'm so pleased you have solved your shutdown problem! And I do agree that we (the whole Open Source community) have a problem with regression testing (i.e. something that worked before should not stop working accidentally in a new version, or with a patch to fix something else). The problem is time for testing and access to the wide range of hardware to do the testing on. Volunteer developers are short of both, and Canonical (for example) simply has no chance of matching the testing resources of large commercial vendors. So, this is an area that we (the computer-savvy but non-developer community) can really help with, by making sure that beta versions are tested on our older hardware (by dual-boot, for example), and that bugs are bugged. That way, Aunt Sally's Ubuntu system should 'just work'!

---

### Post by run1206 on 2008-06-24
> **ene_dene said:**
> Unfortunately it doesn't help I still can't restart or shutdown computer without pressing a button.

the command i was talking about earlier is "sysv-rc-conf"
it's a command that shows all the processes that are used during shutdown and restart.  you should be able to get the package through synaptic. sorry i couldn't find it sooner 
here's the tutorial:
[http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf](http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf)
still not sure which process may be causing the problem, but at least not you can see what's running during the boot process :D


Aearenda: very true.  i still use gutsy on my desktop i bought 5 years ago, runs really good. just hoping that they keep eye on the older drivers and programs used when releasing new distros.

---

### Post by ene_dene on 2008-06-24
Aearenda I agree.

run1206 I've solved the problem, but it is a nice feature to know. Thank you.

---

### Post by locky28 on 2008-06-25
Hi all,

I'm still having this problem of error messages hanging on the screen for about 5 seconds before the splash screen comes up during shutdown/reboot.

I've tried editing /etc/dbus-1/event.d/25NetworkManager and /etc/init.d/sendsigs as said but no luck. I've also tried re-applying the settings under the System>Administrator>Login Window with no luck. I tried disabling the Bluetooth service but that didn't make a difference either :(

Does linux keep logs of those errors that came up during shutdown? Does anybody know where I can get them from because I think that would really help if I could show you all the problem...

Thanks :)

---

### Post by locky28 on 2008-06-25
Never mind, I found a solution on the eeeuserforums.

[http://forum.eeeuser.com/viewtopic.php?id=1859](http://forum.eeeuser.com/viewtopic.php?id=1859)

Why this worked IDK but I'm sure glad it did :D

---

### Post by slavka012 on 2008-07-07
> **Big Ben said:**
> The fix in [this thread]("http://ubuntuforums.org/showthread.php?p=4858236#post4858236") appears to have worked for me, as strange as the fix seems.
The fix is strange indeed, but it works...

---

### Post by sayakb on 2008-07-07
Haven't read the whole thread. 
For a fast shutdown, you may also try:
```
sudo init 0
```

---

### Post by loafman on 2008-07-12
One case of slow shutdown is in wireless network mounted drives when using wpa_supplicant for authentication. There is an ordering problem in /etc/rc[06].d in that S15wpa-ifupdown is executed before any of the S??umount* scripts. This shuts down the wireless network and causes Samba to hang due to multiple network timeouts.

A workaround is to rename S31umountnfs.sh to S10umountnfs.sh in /etc/rc[06].d. This forces network mounted drives to be unmounted before shutting down wireless. There are probably other ordering problems, but this fixes the network drive over wireless problem for me and shuts down much faster.

---

### Post by jerrallan on 2008-07-13
I speeded up my start up shutdown by disabling bluetooth. I tried disabling power management, but that disabled the quit button.

After reading this thread I fiddled with System>>Admin>>Login Windows and changed to automatic login.  Doing that increased the boot time and shutdown time.  Shutdown time before the change was 15-20 seconds. After the change, it was 40 seconds.  I changed it back to login on restart.  After a couple of reboots shutdown went pretty quickly.

---

### Post by timzak on 2008-07-24
> **Big Ben said:**
> I've got the same problem, even after doing a clean install.  
Hangs on "running local boot scripts (/etc/rc.local)" for about 30 seconds, then a bunch of error messages about network manager, then a brief flash of the splash screen, followed by normal shutdown.

Had no similar problems on this machine with edgy, feisty, or gutsy.

Has anyone filed a bug report on this?

I am getting exactly what is described above, for weeks, if not months now (as of 7/24/08).  Has a fix been found yet?

Edit:  Using 8.04.1, wired network connection, bluetooth disabled.  I don't seem to recall this after I first installed Hardy in late April, but it seems to have crept in shortly afterword (maybe started in May sometime?)  Are there log files somewhere that could tell me when these errors first started appearing?  That might help us track down what is causing this problem.

---

### Post by timzak on 2008-07-26
> **slavka012 said:**
> The fix is strange indeed, but it works...

Thanks, this worked for me too.  It didn't work right away...I think it took 1 or 2 reboots for it to take effect.  Thank you to the original posters of these solutions, your posts are too old for me to click the thank you icon now.

---

### Post by soho2014 on 2008-09-14
I have very slow shutdowns too, but I've noticed, that the longer I use the machine, the slower the shutdown.  Sometimes it appears as if nothing at all is happening for 5 minutes or so.

Once I got the shutdown splash screen, and it went through the progress bar, and just when it looked like it was going to turn off, it seemed to hang there, and I got fed up and just cut the power myself.:confused:

---

### Post by dissdigg on 2008-09-15
I have the same experience - using the power icon/button in the top corner.  

Sometimes it takes 5 minutes before the splash screen to display, and it only lets me power off or restart.  If I click CANCEL, and press the power button again the splash immediately comes up and will then let me suspend/hibernate as well.

Oh, and while I'm waiting that 5 minutes the whole desktop is unresponsive.

So,  if I'm short on time, I will alt-ctrl-F# login, and do a sudo shutdown or reboot.

This is weaksauce.

---

### Post by Casper Hansen on 2008-09-15
On my PC I'm unable to shutdown and restart. I have to run 

```
sudo shutdown -h now
```

before the PC will shutdown.

I think it's a problem with the GUI or something. 

There's no slow restart/shutdown on my laptop though.

---

### Post by Daeo on 2008-10-31
The problem may be due to "flash cookies" . Try Mozilla Firefox Add-on: BetterPrivacy.  :lolflag:

---


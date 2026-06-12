---
title: "Palm, PDAs, GNOME Pilot &amp; Ubuntu"
date: 2006-06-05
forum: Desktop Environments
---

### Post by CybaCowboy on 2006-06-05
Firstly, as you can see from the screen-shot, Ubuntu *should* run "*gpilotd-control-applet*" when my Palm (Pilot) is "connected"...

This is not the case however, and Ubuntu does not automatically run *any* program when I connect my Palm (Pilot) or press the HotSync button!


Secondly, I'm trying to setup GNOME Pilot, but the included help is quite cryptic and refers to buttons that clearly don't exist (such as the "Get from Pilot" button)!

Here's the situation - I already sync my Palm (Pilot) with Windows XP with the username "*Cowboy*" over USB, however I would like to sync it with both operating systems (if this is possible)...

What settings do I need to input, as shown in the screen-shots below?

---

### Post by CybaCowboy on 2006-06-05
Oops - forgot the attachments!

---

### Post by Gamabunta on 2006-06-05
Personally I would not use GNOME Pilot but [J-Pilot](http://www.jpilot.org/) instead. You can get it from Universe.

---

### Post by CybaCowboy on 2006-06-05
[QUOTE=Gamabunta]Personally I would not use GNOME Pilot but [J-Pilot](http://www.jpilot.org/) instead. You can get it from Universe.[/QUOTE]

Okay, I've got J-Pilot installed, but how do I get my Palm (Pilot) to connect?

I've hot the HotSync button, but nothing happened!

---

### Post by simplyw00x on 2006-06-05
What model Palm are you using? Also, I can reccommend using gpilot. It works with minimal configuration and integrates with evolution. Also, why would you want gpilotd-control-applet running whenever you attach a palm?

---

### Post by CybaCowboy on 2006-06-05
[QUOTE=simplyw00x]What model Palm are you using?[/QUOTE]

Palm Tungsten T.


[QUOTE=simplyw00x]Also, I can reccommend using gpilot. It works with minimal configuration[/QUOTE]

Sounds like a plan...

How do I set it up (see the screen-shots above)?


[QUOTE=simplyw00x]and integrates with evolution.[/QUOTE]

I use Thunderbird.


[QUOTE=simplyw00x]Also, why would you want gpilotd-control-applet running whenever you attach a palm?[/QUOTE]

This is the default setting...

I don't even know what "*gpilotd-control-applet*" is!

---

### Post by zlogic on 2006-06-05
Try right-clicking the top panel and adding the "pilot applet" to it. Worked for me on Breezy (assuming that Palm was successfully set up).

---

### Post by CybaCowboy on 2006-06-05
[QUOTE=zlogic]Try right-clicking the top panel and adding the "pilot applet" to it. Worked for me on Breezy (assuming that Palm was successfully set up).[/QUOTE]

Doesn't work - there's no such option!

---

### Post by Anthem on 2006-06-05
[QUOTE=CybaCowboy]Okay, I've got J-Pilot installed, but how do I get my Palm (Pilot) to connect?

I've hot the HotSync button, but nothing happened![/QUOTE]
Please don't take offense at the stupid question, but is your palm on?

Gpilot's been nothing but crap for a long time, but almost everybody gets JPilot to work.  Something in this thread might help:

[http://ubuntuforums.org/showthread.php?t=128603](http://ubuntuforums.org/showthread.php?t=128603)

---

### Post by robenroute on 2006-06-06
[QUOTE=CybaCowboy]Okay, I've got J-Pilot installed, but how do I get my Palm (Pilot) to connect?

I've hot the HotSync button, but nothing happened![/QUOTE]

Hi there,

In order to get my Tungsten T5 chatting to my laptop, I had to do quite a few things: [click here for my forum posting]("http://ubuntuforums.org/showthread.php?t=78918")

Mind you, that was on Breezy; I haven't tried it on Dapper, yet. Will do that in the next few hours...

Rob

---

### Post by robenroute on 2006-06-06
Oh dear, I just had a quick look at my own solution and unfortunately, I stumbled on the first step: there is no /dev/pilot defined!

No time now, I'll look at it later....

---

### Post by robenroute on 2006-06-06
[QUOTE=robenroute]Oh dear, I just had a quick look at my own solution and unfortunately, I stumbled on the first step: there is no /dev/pilot defined!

No time now, I'll look at it later....[/QUOTE]

Well, couldn't keep myself from having a quick look. What I did:

1. I ignored the missing /dev/pilot
2. I checked the Device Manager (all values still the same = not very surprising considering the fact I'm still using the same Tungsten T5 ;) )
3. I edited /usr/share/gnome-pilot/devices.xml
4. I created the custom rules file
5. I clicked the gnome-pilot applet (which started the connection wizard) --> all went fine
6. started jpilot and did a sync.... now, this is very it gets funny: both my laptop (jpilot) and the T5 report the sync being successful. However, the address book and the calendar (all in jpilot) are completely empty!

Hmmmm :-k

---

### Post by robenroute on 2006-06-06
Just a quick BTW: after the steps mentioned in my previous reply, /dev/pilot was automagically added to the system.

---

### Post by CybaCowboy on 2006-06-06
Stuff this, I give up.

I don't mind doing a bit of work to get Ubuntu to do what I want, but this is just far too much stuffing around...

---

### Post by Gamabunta on 2006-06-07
Give up already?
Try this:
1. Press the hotsync button in j-pilot
2. Press the hotsync button on your palm usb connector

---

### Post by CybaCowboy on 2006-06-07
Nothing.

---

### Post by fdimmling on 2006-06-07
[QUOTE=CybaCowboy]Nothing.[/QUOTE]

The same here. As soon as you press the Sync on the Palm /dev/pilot is created and points to /dev/ttyUSB1 here. Owner is root and group is dialout. User is member of dialout thus there should be no permissions problem. Nevertheless JPilot gets no connection. With gpilotd I got once a connection and the user and ID from the Plam were successfully exchanged but after that no more connection. Not even after restarting the computer. Strange. Seems that the 6 week delay time of Dapper was not mainly spent on desktop issues.

Friedrich

---

### Post by robenroute on 2006-06-07
[QUOTE=fdimmling]The same here. As soon as you press the Sync on the Palm /dev/pilot is created and points to /dev/ttyUSB1 here. Owner is root and group is dialout. User is member of dialout thus there should be no permissions problem. Nevertheless JPilot gets no connection. With gpilotd I got once a connection and the user and ID from the Plam were successfully exchanged but after that no more connection. Not even after restarting the computer. Strange. Seems that the 6 week delay time of Dapper was not mainly spent on desktop issues.

Friedrich[/QUOTE]

Have you actually tried the things I described in my postings? You do need to edit some files, as far as I know. Ie been struggling with this myself (still am, in fact). If the devices.xml file isn't changed to reflect your particular Palm ID, it'll be hard to get things working....

---

### Post by wastrel on 2006-06-08
gpilotd is broken in dapper - it crashes and hangs and sometimes even works.

What I'm doing is running gpilotd manually from the terminal before each sync (no pilot applet.)

I also installed the updated gpilotd test packages found on this bug thread:  

[https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653](https://launchpad.net/distros/ubuntu/+source/gnome-pilot/+bug/25653)

This has improved the number of successful syncs, but it's still crashy.

I run gpilotd, then hit the hotsync button on my Clie.  I can then watch the terminal output of gpilotd to see whether it's either crashed (segfaults), hung up (repetitive error or no output), or working (hotsync output messages).

If it's hung i ctrl-c and try again.  If it's crashed I usually have to change the port that gpilotd is looking at ( ~/.gnome2/gnome-pilot.d/gpilotd  device=/dev/ttyUSBX) because the previous port is still being held by the crashed process (or something...).

It's a pain, but I can sync.  Hoping for a fix on this soon.  jpilot works flawlessly, as long as gpilotd isn't running.

---

### Post by fdimmling on 2006-06-10
[QUOTE=robenroute]Have you actually tried the things I described in my postings? You do need to edit some files, as far as I know. Ie been struggling with this myself (still am, in fact). If the devices.xml file isn't changed to reflect your particular Palm ID, it'll be hard to get things working....[/QUOTE]

It seems that sometimes I can sync my Palm with j-pilot if I do it right after starting the computer. But in the vast majority of cases j-pilot does not connect with the Palm. 

Friedrich

---

### Post by wastrel on 2006-06-10
[QUOTE=fdimmling]It seems that sometimes I can sync my Palm with j-pilot if I do it right after starting the computer. But in the vast majority of cases j-pilot does not connect with the Palm. 

Friedrich[/QUOTE]


Do you have the gnome pilot applet running?

---

### Post by fdimmling on 2006-06-10
[QUOTE=wastrel]Do you have the gnome pilot applet running?[/QUOTE]

No. But gnome-pilot behaves the same strange way. I once succeeded in getting the Palm (Tungsten E) recognized but never got it really synced - the pilot symbol just stayed white. However at the times when I tried to work with j-pilot ther were no gpilot processes running.

Friedrich

---

### Post by rplantz on 2006-06-16
Most of the posters here seem to be using usb devices, so perhaps my remarks are irrelevant.

I have an old Palm m-100 which uses a serial connection. It worked just fine with evolution and j-pilot under breezy, but did not under dapper.

After much poking around, I discovered System->Preferences->Removable Drives and Media Preferences has a tab for PDAs. Sure enough, selecting "Sync Palm devices when connecete" did the trick. Next I will install j-pilot and see if that works.

---

### Post by fdimmling on 2006-06-17
An excellent way to make j-pilot sync with your Palm is described in the German J-Pilot Wiki and works perfectly here with my Tungsten E.

1) You create a file /usr/local/bin/palm_sync (using sudo vi or sudo gedit)

#!/bin/bash
PID=`pidof jpilot`
if [ $PID ]
then
   jpilot -s
else
   jpilot-sync
fi

2) You create a file /etc/udev/rules.d/10-visor.rules

BUS="usb" SYSFS{product}="Palm Handheld*" KERNEL="ttyUSB*" MODE="666" SYMLINK="pilot" RUN="/bin/su username -c '/usr/local/bin/palm_sync'"

(in one line! You have to replace username by your own user name!)

3) Set permissions

sudo chmod 755 /etc/udev/rules.d/10-visor.rules
sudo chmod 755 /usr/local/bin/palm_sync

There is no need to start j-pilot to sync, just plug in your Palm and press the Hotsync button.

Friedrich

---

### Post by pito on 2006-06-18
Hello Friedrich and all others...

I have been able to synchronize my Palm E2 with Ubuntu 5.10, I used pilot-link 0.12.0 pre 4 and recompiled jpilot. Never ever any problems problems with synch

Yesterday I moved to U-6.06.

The Palm does not want to synch anymore. I managed to get the 
    dlpsh -ip /dev/ttyUSB1
to work some times, mostly after power up, but it is not good.

Is there any body that has been able to synchronize in U-6.06 ???


/piotr

---

### Post by btlee on 2006-06-18
I have quite similar problem.
Once it occurs, I kill gpilotd or jpilot-sync.
For gpilotd, it is relaunched automatically, and then it starts to sync successfully almost always.
For jpilot-sync, it should be restarted manually.
My experience suggests that the first trial of sync is unsuccessful due to some unknown errors, and second trial skip the unknown problem(s).
Could it be a hint for fixing the problem?

---

### Post by fdimmling on 2006-06-19
From here bad news too. After installing the files as described above everything seemed to work perfectly with jpilot. The next day no chance to sync my palm with j-pilot. I will stay away from Dapper for the rest of the machines in my network for the time beeing.

Friedrich

---

### Post by hfdragon on 2006-06-19
[QUOTE=btlee]
For gpilotd, it is relaunched automatically, and then it starts to sync successfully almost always.[/QUOTE]

Tanks a lot ! now it works !!

I had no problems with breezy, and after my upgrade to dapper, no way to sync.

So I follwed this advice :
- killall gpilotd (from a terminal)
- press the sync button on my cradle

And it syncs !!!! :p

Update :
Opps, I spoke too fast, it worked once, and no way to sync again after this first sync.. :-(

---

### Post by can3p on 2006-06-19
Sync doesn't work for me too. =(
Sony clie TJ25.

pilot-xfer works from time to time and I couldn't figure out when it start to work. Any comments from maintainers?

---

### Post by btlee on 2006-06-19
[QUOTE=hfdragon]Tanks a lot ! now it works !!

I had no problems with breezy, and after my upgrade to dapper, no way to sync.

So I follwed this advice :
- killall gpilotd (from a terminal)
- press the sync button on my cradle

And it syncs !!!! :p

Update :
Opps, I spoke too fast, it worked once, and no way to sync again after this first sync.. :-([/QUOTE]

In my experience, you should kill gpilotd and restart it every your sync.
So, I prepare terminal whenever I am going to sync.
I know this is pretty silly, but no other ways at this time.

---

### Post by wastrel on 2006-06-19
As far as I know, the problem is that the gpilotd program doesn't work well with the USB due to the change to udev.

I am starting gpilotd before each sync and killing it afterwards.  Jpilot works with no problems as do the command line tools.  

To use jpilot, or the command line pilot-link tools, start the sync on the palm side first, then push the sync button on jpilot or hit enter on the command line.  

I don't know how well it works if you have a udev script set up to automatically sync jpilot or pilot-link when you start the sync on the palm side, this is something I haven't tested.

That's how it's working for me right now...

---

### Post by hfdragon on 2006-06-19
[QUOTE=btlee]In my experience, you should kill gpilotd and restart it every your sync.
So, I prepare terminal whenever I am going to sync.
I know this is pretty silly, but no other ways at this time.[/QUOTE]

I tried, "killall gpilotd" and press sync button, but it worked only once.

---

### Post by Ken.Lank on 2006-06-21
I've gotten gnome-pilot to work by configuring it to use /dev/ttyUSB0 insted of /dev/pilot.

---

### Post by btlee on 2006-06-21
[QUOTE=hfdragon]I tried, "killall gpilotd" and press sync button, but it worked only once.[/QUOTE]

sometimes killall doesn't work.
So, you'd better `kill -9 pid`.

---

### Post by can3p on 2006-06-22
I found the cause of all errors with my palm. When I press hotsync button on my palm, udev creates to devices(for example ttyUSB0 and ttyUSB1) and one symlink pilot, that points to ttyUSB1. But syncronisation goes only through the ttyUSB0 device. If ttyUSB2 and ttyUSB3 are created, than the device needed is ttyUSB2 etc.
udevinfo -p /sys/class/tty/ttyUSB2 -a and
udevinfo -p /sys/class/tty/ttyUSB3 -a produce absolutely identical data, so it's not remarkable, that udev gives wrong results. But it's a bug.
If I choose port ttyUSB0, syncronisation goes **every** time threough gnome-pilot, jpilot and pilot-xfer.

---

### Post by fdimmling on 2006-06-22
[QUOTE=can3p]I found the cause of all errors with my palm. When I press hotsync button on my palm, udev creates to devices(for example ttyUSB0 and ttyUSB1) and one symlink pilot, that points to ttyUSB1. But syncronisation goes only through the ttyUSB0 device.[/QUOTE]

Strange! My Tungsten E seems to sync via /dev/ttyUSB1. I set the device to /dev/ttyUSB1 in jpilot because /dev/pilot did not work and it synced - at least once. I do not want to speculate for how long. 

Friedrich :twisted:

---

### Post by can3p on 2006-06-23
This really looks strange, but I think, it's udev problem

---

### Post by dannemil on 2006-06-26
[QUOTE=can3p]I found the cause of all errors with my palm. When I press hotsync button on my palm, udev creates to devices(for example ttyUSB0 and ttyUSB1) and one symlink pilot, that points to ttyUSB1. But syncronisation goes only through the ttyUSB0 device. If ttyUSB2 and ttyUSB3 are created, than the device needed is ttyUSB2 etc.
udevinfo -p /sys/class/tty/ttyUSB2 -a and
udevinfo -p /sys/class/tty/ttyUSB3 -a produce absolutely identical data, so it's not remarkable, that udev gives wrong results. But it's a bug.
If I choose port ttyUSB0, syncronisation goes **every** time threough gnome-pilot, jpilot and pilot-xfer.[/QUOTE]

I have never had any trouble syncing my Palm using jpilot both under breezey and dapper with Palm at /dev/ttyUSB0. But no such luck when trying to sync with Evolution. Conduits are set up correctly, but pressing the hotsync button on the cradle results in ... nothing followed by a time out. I've tried all of the suggestions on the posts with gpilotd and nothing even comes close to initiating a sync.

Jim

---

### Post by pito on 2006-06-28
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds. 
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by saaz on 2006-06-28
[QUOTE=pito]
There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.
[/QUOTE]

Excellent..I hope the rumors are true. Looking forward to the new kernel then.

---

### Post by fragos on 2006-06-29
I've a Palm E2, Jpilot, Pilot-link and Ubuntu 6.06.  This is the first distro in years that I haven't been able to get my Palm to sync consistently.  Its pretty clear from all these posts that there is a problem -- I know not where.  Does someone know if this problem is being worked by the development team.  I'd hate to wait 6 month until the next distro release.  Truth is, I changed to Ubuntu after being a dedicated SuSE user for years.  SuSE 10.1 is a total bork.  The thouht of having to buy Windows to sync my Palm is beyond comprehension.  Please show me some light at the end of the tunnel.

---

### Post by fdimmling on 2006-06-29
I agree with you. Syncing a Palm is really one of the basic functions a desktop operation system should be able to perform. For me it comes almost next to the office suite. 

Does anybody know if there is already a bug report filed? 

Friedrich

[Update] Filed a bug report myself now.

---

### Post by pito on 2006-06-30
I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds.
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr

---

### Post by ChrisC on 2006-07-01
Inability to get Palm sync (or a decent desktop app) working in Ubuntu 5.10 is the only reason that there's still a Windows 95 machine on the floor under my desk, connected to the KVM switch.  That's the only reason for the KVM switch, too :)

I just upgraded to Dapper, and notwithstanding the complaints in this thread, I hope to get something working in the next week.  It sucks not being completely sync'd all the time.

---

### Post by popie on 2006-07-01
I would like to sync my Palm V with jpilot using IRDA. Any tips?

Palm sync is really important to me, any tips would be appreciated.

---

### Post by shane2peru on 2006-08-19
> **pito said:**
> I had BIG problems to synchronize TE2 after I updated to Draper.

I managed it to synch with pilot-xfer only three times out of maybe hundreds.
I tried different tricks, nothing helped.

But...after rumors that kernel 2.6.15 is broken regardin udev and usb stuff.

What I did today was that I switched back the kernel from Version 2.6.15 to 2.6.12, and the sync works every time both from command line,pilot-xfer, and via jpilot.

I recovered the old archived manu.lst~ from Breeze and rebooted the OS.
Then I ran "sudo modprobe visor" and I am back in the bussines.

There are unconfirmed infos that the new kernel for Draper 2.6.17 work perfect as well.

Hope it will help others.

/piotr
Ok, how can I re-install that Kernel??  I guess I got rid of it too soon.  Thanks for the tip!

Shane

---

### Post by VoodooEx on 2006-09-05
Hi everyone, 

This is my first post and I hope this will be helpful.

I use gpilotd to sync my Treo 650 and Evolution, and I can do this consistently by invoking the gpilotd manually at a terminal.

At the same time I have a problem which I hope someone could help me with. After every sync, the records created on my Treo 650 are all marked private. How do I prevent it from being marked private.

Many thanks in advance. ;)

---

### Post by knowmad on 2006-09-11
Thanks for the ideas. Booting into 2.6.12-10 and running `sudo modprobe visor` allowed me to sync to my Tungsten E2 at /dev/ttyUSB1. Rather than removing the latest 2.15.x kernel, you can install the 2.6.12-10 kerne, reboot, enter the Grub menu and choose to run the 2.6.12-10 kernel. This saves you from the potentially dangerous operation of removing your running kernel.

---

### Post by blakeforeman on 2007-07-12
i hate to be this way with ubuntu but i've been hearing that kde enviroment has been doing alot better so for some people fed up with editing config and junk try to get kde i think they open the hotsync ports and close them properly and it sounds like that is the problem basicly i belive you would need to get the complete package to the networking for kde in order for it to be able to control ports and stuff tho. hotsync essentially/basicly in laymans terms has steps to syncing over bluetooth and correct me if i am wrong i might be, first the bluetooth pair needs to be made and kept alive, then the computer needs to know what the device can do (what it's capabilitys are) and then your computer needs to assign correct  port (channels/tunnels) to the correct programs. as far as hot sync is concerned, it is basicly simple, while your computer can listen on many ports all at the same time a phone is not that smart and hot sync only uses 2 main ports, 10 between phones, here's where complications arise and it's verry simple. hotsync cannot sync with just bluetooth, it is impossable for it to sync without help: it needs the help of something called a virtual serial port that means that basicly your blue tooth software needs to trick your computer into thinking that it's not really connected through blue tooth because bluetooth dosn't defaultly give out a sereial port because many things can be connected to your computer with bluetooth it at once and some things don't use a sereial port and some do,  so, pick one of  those 2 main ports, your device will tell you witch ports it trys and pick one of those 2 sereial ports and create the ports. now i'm sure that the people makeing these hotsync programs understand this better than i think that i do but here is where i belive the problem en-lies

 when your not syncing your phone the syncing application makes thone ports available to everything, this is where it goes rotten because when it comes time to sync your phone, whatever program that took that port can't give it back because it was told to use only that port  screwing up your palm sync the diffrance with kde is even more simple once it establishes the correct ports it runs in the bar all the time (like in windows)  and keeps that port freeand when that application or device comes along to take that port it tells it no or it will create a virtual port. again, i don't know what the creaters were thinking but that is how it is done when it works.

---


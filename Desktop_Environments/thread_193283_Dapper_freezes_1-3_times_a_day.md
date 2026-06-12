---
title: "Dapper freezes 1-3 times a day"
date: 2006-06-09
forum: Desktop Environments
---

### Post by jemt on 2006-06-09
Greetings.

I'm having some serious problems with Dapper, which I have been working on for 5 days now - and I just can't seem to re-produce the error - it happens ramdomly.

1-3 times a day, Dapper just freezes, and all I can do is hit the power off button. It mostly happens when I'm listening to music in XMMS from my new external USB harddisk, which is the main difference on this setup. I bought it when I upgraded to Dapper (was running Breezy before). So maybe the disk is causing the problem. But the problem usually happens when VMWare og Firefox is running and is open (has focus). Unfortunately I have no idea how to debug this.

It could also be the graphic card (ATI Radeon Mobility 6 (probably the Radeon 9000 series)). My wireless network card dosn't work as it is supposed to do in Dapper - worked great in Breezy though.

I'm considering going back to Breezy - only thing that keeps me on Dapper is the repositories with all the new, great, updated software - ie. Sun's Java 5/1.5. So if I can use the Dapper repos in Breezy, I will definately downgrade. Dapper is great, but I'm not sure it was ready to be released.

---

### Post by Dr. Nick on 2006-06-09
Not sure why your having problems. If you wanted a potential quick and dirty fix then install breezy and get it set how you want it. Then open synaptic and lock the kernel and other packages you dont want upgraded. Then switch your sources over to dapper instead  of breeezy and update.

I cant guarntee that will work flawlessly but its a idea

---

### Post by jemt on 2006-06-11
Hi Dr. Nick.

Thanks for your reply. I would be more interested in a solution on how to debug this problem though - ie. what log files to look into, what to look for etc. Your solution would also require that I knew what packages to lock - it is probably not the kernel alone that's causing this problem.

I would really appreciate some help - I'm tired of switching to a new Linux distribution, each time a new version is released of the distro I'm currently working with. Some years ago I used Mandrake, but switched to Knoppix becuase a newer version af Mandrake became incompatible with my system. I moved from Knoppix because of the same reason, and now I haft to move from Ubuntu to yet another distribution. The Linux Community seems to have a problem with keeping their distributions compatible with hardware that was working on previous versions.

Any help is greatly appreciated :)

---

### Post by viz_e on 2006-06-12
I also have some troubles with dapper:

* Dapper hangs once or twice a day: the HDD starts working like crazy for minutes. Sometimes I can fire up a top and see that the processor is dominated from either Xorg, firefox or thunderbird. Only fix: hard reboot.

* While using firefox, it sometimes happens that the page gets "refreshed" automatically, causing also an hang on for few seconds. Very annoying.

* Thunderbird is configured with an IMAP account. Once every two days, it starts downloading all messages headers from scratch... You can guess how much does it take (above all for the "Sent" and "Trash" folders).

* I have the "local" problem. Every time that I run something in the terminal (like oocalc) I get
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```
and it is also impossible to set the right charset.

Altogether, I sadly have to say that I am really disappointed by dapper, since Breezy did not have such problems (at least not the above-mentioned ones). I am considering to try again a fresh install and see whether I have some more luck.

---

### Post by Ctrl+Alt+Del on 2006-06-12
Hardlocking computers are most of the time hardware or driver issues. The best way to track it down is probably by trying to eiliminate possible causes one by one. Try unplugging your external drive and see if it still happens. If that is not the culprit i think i'd start looking at vmware as the possible offender, i very much doubt you'll find logfiles of what went wrong, a hardlocked machine rarely has the time to log what went wrong, and even if it could it might not be a wise idea as it might cause filesystem corruption.

---

### Post by TheFifth on 2006-06-13
I'm also getting Hard locks at least twice a day.  This computer has been running Ubuntu from Hoary, upgraded to Breezy and now upgraded to Dapper.  I've had no problems at all with the previous two installs, but only developed problems since the update to Dapper.

I've installed XGL and Compiz since I've updated, so I don't know if that has anything to do with it.

I've also installed VMWare Player, which seemed to coincide with the locks starting.  Now this could be just coincidence as I updated a lot of things all at the same time, but it does seem to tally with what someone has said above.

---

### Post by sam hassell on 2006-06-13
dunno if this will help, but i started having similar hard locking problems after running automatix with almost all the options on.

i fixed it. not entirely sure what was at fault though. i got rid of swiftfox, stopped using azeurus and, i think most importantly, stopped using the desktop search applet. theres a few threads around on problems with it and beagle. hth.

---

### Post by TheFifth on 2006-06-13
Hi sam,

I have run Automatix with a lot of the options on.  Typically I've not installed swiftfox, azeurus or the deskbar search applet!

As hard locks are normally driver related, I was wondering if it was something to do with the NVidia drivers that Automatix installed?  Anyone else here using them?

---

### Post by zeus77 on 2006-06-13
[QUOTE=viz_e]
* Dapper hangs once or twice a day: the HDD starts working like crazy for minutes. Sometimes I can fire up a top and see that the processor is dominated from either Xorg, firefox or thunderbird. Only fix: hard reboot.
[/QUOTE]

For what it's worth, I've got the same problem... Exactly.  Once or twice a day, HD cranks, Xorg runs like mad, mouse response time gets really bad, hard reboot required.  Hmph.

---

### Post by dspivey on 2006-06-13
I've had this exact same problem.  It is random, and is not related to hardware.  I dual boot on the same drive with dapper and fedora core 5; fd5 has no issues at all, either running gnome or kde.  i thought firefox was the problem so i installed opera; problem still occurs.  it doesn't appear that the system is actually locking up, but appears to be running so slowly that it might as well be frozen.  i can open apps and close windows, but it takes several minutes for each operation to execute.  i will try to run top the next time it occurs to see if i can pinpoint what is happening.

---

### Post by ketsugi on 2006-06-13
[QUOTE=zeus77]For what it's worth, I've got the same problem... Exactly.  Once or twice a day, HD cranks, Xorg runs like mad, mouse response time gets really bad, hard reboot required.  Hmph.[/QUOTE]

I'll report exactly the same problem. I used to have it with Xorg, and now I'm having it with Xgl.

My solution isn't a hard reboot, though. I just hit Ctrl-Alt-Bksp and then login again. That way I don't have to reset my uptime >_>

---

### Post by zeus77 on 2006-06-13
[QUOTE=dspivey]i will try to run top the next time it occurs to see if i can pinpoint what is happening.[/QUOTE]

you might even just keeping a copy of 'top' running at all times, and devote the top centimeter of your screen to displaying the most active process.  i never had the patience to wait the 15 minutes it would've required to open up a terminal, wait for it to respond, and type 'top'.

---

### Post by berzerke on 2006-06-14
I too have had the firefox issue and still search for a solution. As others have said, every page automatically refreshes, causing the HD to go into overdrive, the CPU to shoot to 100% and responsiveness to tank. Waiting a short time usually allows things to return to almost normal. I have had top running in the background and notice that after every episode, X.org consumes more memory. The only way to free that memory is to log out and log back in. A reboot has not been necessary, although I have done a CTRL-ALT-BKSP as others have already suggested.

I migrated from Mandriva to Breezy and never had the problem with Mandriva, but did have it in Breezy (and now Dapper). I had installed and run Firefox from/in my home directory, so the binaries (but maybe not the shared libraries???) were exactly the same. I've wiped out my .mozilla directory and run without plugins and extenstions for a while (How do people live without adblock!?!?) but the problem still occurs.

So at this point, it doesn't appear to be plugins, extensions, settings (Firefox settings at least), or Firefox itself. I'm not running any VMware, so that may not be the cause TheFifth. dspivey has reported Opera has the same issues, so that leaves that out. Any suggestions anyone???

---

### Post by ranpha on 2006-06-14
I got the same problem. Running ubuntu on two complty different systems. thr the same age but on is intel the othr is AMD. Other chipset etc. Both running wireless card also different. Bth have the prblem when running firefox, bittorrent (azureus) and amule tht th system becomes a tank in response. I was thinking swap because when the slowiness starts even moving my mouse gives hdd response. That isn't correct. I tried turing acpi off no succes.  So i has to be somthing in the software. I was thinking network manager first. But now I think xorg is the problem. Because on Sarge (runnng Xfree86) everthing works great with eachother. So i'm thinking now is there a way to get rid of Xorg and have Xfree86 instead. (i also think Etch Debian has this same problem but haven't tried it out yet)

PS both system had 256 and 320 mb memeory. System monitior has no swap enabled or in use.  I tried putting in 512mb into one system and it seems that everthing is working no but i will kep you up to date

---

### Post by matrooswolf on 2006-06-14
[QUOTE=jemt]
But the problem usually happens when VMWare og Firefox is running and is open (has focus). Unfortunately I have no idea how to debug this.
[/QUOTE]
Reporting the same problem.  

System comes to a halt, accessing the HDD like hell.  I hit CTRL+ALT+BACKSPACE and get out of memory errors with vmware and beagle.

In my case it happens only when I use vmware, and use it together with firefox of beagle.
So I think there is something wrong with vmware (I'm using vmware server with windows xp on it).  And I don't know if this is important, but I use it when Xgl is running.

But it is difficult for me to tell: is it Dapper?  Is it Vmware?  Is it Xgl?  Is it the combination?  

I had no system freezes otherwise ...

---

### Post by ranpha on 2006-06-14
What kind of ram are you running??? Because i just inserted 512 md ram in my laptop and it seems that i don't hav the problem anymore. Also i think that the swap can't be touched by the OS??? 

Maybe the system does not have enough ram to progress everthing and with swap no accesbile the whole system crashes.

Maybe a programmer or maintainer can take a look at this

(when i install vmware btw i have to be SUDO to run it???? this wasn't before final release , beta flight 7 let me run it as ormal user)

PS MY SWAP IS GONE!!!!!!!!!!THAT could explain a lot


Solution: I made a swap partion for some reason did wasnt enabled or anything
try this  sudo mkswap /dev/hdaX && sudo swapon /dev/hdaX  (X being your partion)
to know what partion you need sudo fdisk -l

Now when i opn a page with lost of pictures and have azureus and amule on it uses my swap partion

---

### Post by zeus77 on 2006-06-14
I see this with only the following running: Firefox, Thunderbird, and Evince (default Gnome pdf viewer).  No VMware or anything else.

And I encounter this problem with and without Compiz/Xgl.  

If the problem does point to xorg, could it possibly also be related to the video drivers?  For the record, I have a Nvidia GeForce FX Go5200, and I'm using the nvidia video drivers with RenderAccel enabled.

EDIT: Holy crap, my swap was inactive, too!  When I installed Ubuntu, I let it make the swap partition, and I thought everything was fine... not sure how it got turned off or disabled.  Even fdisk showed a valid swap partition, but then 'sudo swapon -a' wouldn't turn it on.  I needed to run mkswap first.  Bizarre... will report back if this fixed the slowdowns...

---

### Post by sam hassell on 2006-06-14
fifth, that could be it, i have been playing A Tale In The Desert, and most of the lock ups occurred while that was running. I uninstalled the nvidia-glx, and reinstalled it (i reverted to my original sources.list after running automatix) and have not had problems since, though I have not been playing the game. Will post again later.

---

### Post by brt on 2006-06-14
i also had random lockups on a quite old computer, i found out that the CPU cooler was full of dust, so the cooling effect was really bad, leading to a lockup whenever there was massive cpu usage - a quick vaccum cleaner session and the machine was fine again :D

---

### Post by viz_e on 2006-06-14
I have already reported about these hard locks, but I forgot to mention that sometimes I also loose the windows decorator (during them, when the mouse is still "a bit" working).
I don't think that it is a fan (overheating) issue, because my temperature is constant and neither it is a graphic card driver trouble, because it is an ati mobility (and not a nvidia as some of you reported).

Today I got an "almost" hang up opening oowrite and what I could see, was that the cpu throttling was not working (fixed CPU frequency... the lowest...).

I substituted powernowd by cpufreqd and up to now (only few hours) nothing (bad) happened... let's hope ;)

Btw. I have never used Automatix.

---

### Post by berzerke on 2006-06-14
I've done some further experimentation on the problem. As I said before, the problem doesn't seem to be in Firefox itself. It just seems that Firefox (and Thunderbird) trigger something. I suspect that those who have the problem with VMware are in the same boat as I have yet to run VMware on this machine.

I was running the xorg nvidia drivers (nv) and decided to try the official drivers thinking it was a driver issue too. I didn't use Automatrix to install. I left Firefox open all night with only a simple static page. At the start, xorg was using a little less than 2% of my memory. By morning, it was up to 39%! No flash or Java on the page either.

So it appears that it's not the drivers (Anyone using non-nvidia cards?). My swap is on and working, so it's not a swap problem. I'm starting to think it is a xorg bug, possibly specific to Ubuntu.

---

### Post by viz_e on 2006-06-14
> [(Anyone using non-nvidia cards?)

As mentioned in a previous thread, I am using an ati mobility card. I also do not use VMware.

---

### Post by berzerke on 2006-06-14
Well, that pretty much kills the "it's the drivers" idea.

BTW, searching through the bug reports turned up Bug #6279. Basically, the ones posting there have come to same conclusions I have.

---

### Post by viz_e on 2006-06-14
> Well, that pretty much kills the "it's the drivers" idea.

Yeah... firefox and thunderbird are still something in common (like Xorg). Since I changed powernowd to cpufreqd I still do not have any hang (which can be plausible, I switched only few hours ago), but firefox still hangs for a couple of seconds every few minutes. That's annoying...

---

### Post by matrooswolf on 2006-06-14
[QUOTE=zeus77]
EDIT: Holy crap, my swap was inactive, too!  When I installed Ubuntu, I let it make the swap partition, and I thought everything was fine... not sure how it got turned off or disabled.  Even fdisk showed a valid swap partition, but then 'sudo swapon -a' wouldn't turn it on.  I needed to run mkswap first.  Bizarre... will report back if this fixed the slowdowns...[/QUOTE]

My swap is inactive too.
A lot of people seem to be having this problem.

 I'll try to do the mkswap and 'sudo swapon -a' thing, but I want to know more about it first (am afraid to loose data), and I think my fstab is mixed up.

Any help appreciated to sort it out (I posted my fstab in another thread already: 
[http://www.ubuntuforums.org/showthread.php?p=1138478#post1138478](http://www.ubuntuforums.org/showthread.php?p=1138478#post1138478)

---

### Post by dspivey on 2006-06-14
I had another 'freeze/crash' today, but couldn't see top since i was in a different workspace and couldn't open the one that top was running in.  i can still move the mouse, and the seconds will tick by on the clock at a rate of 4-5 seconds for every real minute that passes.  i tried ctrl-alt-backspace but everything went off the screen except the desktop background and the mouse pointer (which was completely frozen at that point).  i was running firefox, top, and a proprietary java app at the moment of the freeze/crash.  i'm now running top again and will stay on the same workspace so i can see what is going on at the moment another freeze occurs.

btw, my swap was inactive as well, so i followed the instructions to enable it.

---

### Post by Amon_Re on 2006-06-14
I too *had* hard lockups with dapper, in my situation, the solution was a BIOS upgrade, seems that the latest kernels in Dapper are rather fussy about it.

Might help some of you guys.

For reference: My mobo is an Asus K8N4-E Deluxe

---

### Post by viz_e on 2006-06-15
> btw, my swap was inactive as well, so i followed the instructions to enable it.

Which instructions?

---

### Post by zeus77 on 2006-06-15
[These]("http://www.ubuntuforums.org/showpost.php?p=1138222&postcount=4") instructions might help...

---

### Post by viz_e on 2006-06-15
Ok, I tried your suggestions. I will post here in case of success or problems... :cool: Thx a lot.

Btw, my swap is always empty (with 1.5 Gb RAM) and cat /proc/swaps leads:

Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       1005440 0       -1

---

### Post by viz_e on 2006-06-15
Uhm... my swap is working now... and my Xorg is using 80% of the memory: 1.5 Gb Ram + 1 Gb swap... that's much I guess :confused: 

So, I would say that Xorg 7 is definitely the problem.

---

### Post by viz_e on 2006-06-15
I just had a crash (no really a crash... HD working like crazy, no responsiveness, blabla, you know). So cpufreq instead of powernow and making sure swap works is not the solution. :sad:

---

### Post by dspivey on 2006-06-15
I came in this morning and my system is frozen/crashed again.  Top was open and it showed the following:

mem: 774476k total, 535992k used
swap: 1429772 total, 0k used
 
I couldn't see which processes were taking up all the memory (Xorg only showed 2.6%MEM); they didn't show in the list even though I was able to totally maximize the window before the system came to a complete standstill.  Firefox was the only application running, besides background tasks, of course.

viz_e:  The instructions that zeus77 gave were exactly what I was referring to.  Thanks, zeus77!

---

### Post by TheFifth on 2006-06-15
I've switched back to metacity from Compiz and XGL, and (touch wood!) I have not had a hard lock in 3 days.

When my machine was locking the mouse would work perfectly, but I could not click anything and also could not type anything.  The Num Lock and Caps Lock lights on the keyboard would not switch on or off either, so I guess the keyboard was completely inactive.

Anyway, I'll press on without XGL and Compiz for a bit and hope for the best!

---

### Post by mike4ubuntu on 2006-06-15
My desktop froze when I hit the eject button on my DVD drive.  I hit CTRL-ALT-BACKSPACE to restart the desktop.  After I logged in again, I got the HAL Failure dialog and it froze again.  I then hit CTRL-ALT-F1 and logged into terminal, and typed:

```
sudo reboot -f
```

Nothing.  It wouldn't shut down and restart.  The system just hung.  I finally had to push the power button on the box.

Is there some way of telling the system to just restart no matter what?

---

### Post by matrooswolf on 2006-06-15
My problems are fixed (for now anyway ;))

Swap was inactive due to wrong partition numbers (thanks to Partitionmagic).

Since swap is active, I had no crashes, but I will report back if I have (I hope not ;))

---

### Post by brt on 2006-06-15
[QUOTE=viz_e]I have already reported about these hard locks, but I forgot to mention that sometimes I also loose the windows decorator (during them, when the mouse is still "a bit" working).[/QUOTE]

when the window-manager "goes away" you are not able to change the focused window, but you can still use the gnome-panel e.g. to click on a custom starter which starts metacity , and `voila ...` the borders are back again :D

---

### Post by clintonthegeek on 2006-06-16
I'm experiencing a total freezup in Dapper as well... the mouse and keyboard are completely unresponsive, including Ctrl+Alt+Backspace. Also, this is happening in Kubuntu, usually while using Konqueror (but I do have it open 90% of the time).

Just thought I'd let you know that, so I'm pretty sure it's not just a Firefox/VMWare/Gnome/XGL thing. I tried the swap thing... didn't help any.

For the record I'm on a Pentium Iv 1.2ghz with 256mg of RAM, Creative SoundBlaster Live! 5.1, and a Intel 740 AGP video card (which sucks btw ;), throwing in my old GeForce IV soon).

However, half of the times that it freezes directly coincides with getting a new messege in Kopete, because the *ding* sound ends up skipping getting all static-y over my speakers RIGHT when it freezes. So, it might be an Alsa thing, maybe a Xine thing (I admittedly don't know too much in that area) or a network thing. But, it has frozen as well when I was just using Konqueror and Amarok, or Konqueror and doing an apt-operation (when I reboot and try to continue it, I can see that it has always frozen during dpkg setting up my downloaded packages).

Anyways, best of luck to those hunting this down! I'm considering switching back to Breezy until it's all over. :)

-Clinton

edit: added some more system stats.

---

### Post by viz_e on 2006-06-20
Today I have experienced a freeze "live" with top open. 1Gig of swap full and 1.5 Gb Ram almost full (60Mb free). At every refresh of the table, at least 5 Mb less were at disposal and at about 40 Mb RAM left, the notebook freezed.

87% of the memory was used by Xorg and more than 10% by Thunderbird. I tried to close thunderbird in last seconds, but that couldn't help (after 4 seconds... kaboom ](*,) )

So, this is definitely a memory issue. Any progress so far? :-\"

---

### Post by dspivey on 2006-06-20
My system seems to freeze most often after waking it from sleep mode.  I left the system on all weekend and used it all day yesterday without a problem, but came in this morning and it was frozen up again.  No applications were running (such as Firefox, Thunderbird, etc.).  Are there any log files that we should be posting that may help some of our more knowledgeable fellow Ubuntuns figure this one out?

---

### Post by viz_e on 2006-06-22
Any news? Anybody tried a fresh install? This is very annoying... every day 1-2 freezes... ](*,) ](*,) ](*,)

---

### Post by ber89 on 2006-06-22
as others we (2 peoples) are experiencing a total freezup in Dapper as well (average 3 freeze a day)... the mouse and keyboard are completely unresponsive, including Ctrl+Alt+Backspace. Also, this is happening in Kubuntu 

For the record we are on T30 thinkpad on a Pentium Iv 1.8 ghz with 768mg of RAM and a 16MB RADEON 7500 ATI Mobility video chipset

---

### Post by viz_e on 2006-06-22
Keeping track of top during work, it is evident how Xorg eats more and more memory. I usually boot my pc at 8 o'clock and at 12 o'clock I have the first freeze of the day.... :confused: 

Any other experiencing this?

---

### Post by dspivey on 2006-06-22
I was running the 386 kernel on a Pentium 4, so I updated to the 686 kernel; no change.  My computer was frozen when I came in this morning.  The screensaver was frozen on the monitor so I knew it had crashed before I even woke it out of sleep mode.  

This issue does seem to be languishing a bit, with no help in sight.  It's getting a tad disheartening, and Fedora Core 5 is looking better by the minute (Suse 10.0 was pretty good, but 10.1 was a definite step backwards).  I've never experienced these kinds of issues with FC5, running both Gnome 2.14 and KDE 3.5 (Xorg 7.0).

---

### Post by fozzieb on 2006-06-23
I started getting total hangs just the other day, it only happens when i'm in firefox, nothing else.

I'm going to re-install and remove firefox (i'll try opera) and see what happens.

I have seen else where problems with the flash-nonfree plugin, could this be the problem (even though no flash on site when it hangs, it is still installed)


cheers.

---

### Post by ddumanis on 2006-06-23
I had this problem with a Dell 640C with a Mobility Radeon 7500. I solved it (I think) by doing:

**sudo dpkg-reconfigure xserver-xorg**

and manually picking the VESA driver instead of the ATI driver (which is what the live CD installed).

So far I've been able to watch DVDs, use mail and openoffice, etc. without a crash.

I'll post updates here. Meanwhile, try it--it couldn't hurt and actually improved my screen video quality. (No more funky stripes in dialog boxes.)

Dave

---

### Post by bond00 on 2006-06-24
I'm having the exact same problem. It's not associated with any specific program as far as I can tell. I run multiple servers on it, and it'll just lock up periodically. I've performed multiple fresh installs and all have the same outcome...FREEZE. I'm wondering if maybe it could be something with network activity in general. Mine seems to lock up when I'm either connected via SSH or SMB. Too much network activity causes it to lock up?

This is ridiculous. I thinking about just using FC5...I've heard it's stable as a rock. I'll  try reconfiguring X11 and post my results.

---

### Post by clintonthegeek on 2006-06-24
[QUOTE=ddumanis]I had this problem with a Dell 640C with a Mobility Radeon 7500. I solved it (I think) by doing:

**sudo dpkg-reconfigure xserver-xorg**

and manually picking the VESA driver instead of the ATI driver (which is what the live CD installed).

So far I've been able to watch DVDs, use mail and openoffice, etc. without a crash.

I'll post updates here. Meanwhile, try it--it couldn't hurt and actually improved my screen video quality. (No more funky stripes in dialog boxes.)

Dave[/QUOTE]
BZZT! Nope. Froze up seconds after KDE loaded. I hope your luck continues though! It's almost ALWAYS freezing while there is a sound playing, be it a message in Kopete, a song in Amarok (more than once RIGHT when a song ends, and the beginning of the next should start) or in this case, the KDE start up noise.

I've been considering going back to breezy, or hopping to Fedora too (just to stay current), although I'd hate to becasuse I LOVE Kubuntu.

Just a thought, could it be merely that since summer is coming around, everyones computer is just starting to overheat? The freezing slowed considerable once I took out my Intel 740 AGP card (which I read has HORRIBLE overheating problems) and threw in an old ATI Mach 64 PCI card. I'm getting CPU temperatures topping out at about 58 Celsius. But that doesn't quite explain why the same symptoms aren't happening in Breezy.

-Clinton

---

### Post by jlrussell on 2006-06-25
I am having the same problem myself.  Initially, the hardlocks were occuring every 10 to 15 minutes.  On a whim, I installed the non-opensource drivers for my ATI video card using instructions found [here.]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")  These were complete hard locks.  I could not move the mouse, Ctrl-Alt-Bksp, soft reset.. none of that.  The only thing that would work would be to power the computer down.

Changing the driver initially seemed to fix that problem.  But I began to experience locks every few hours in which I can move the mouse, but that's about it.  I cannot restart X, I cannot change to another terminal and again... the only thing I can do is power down the computer.

After being directed to this thread by a very kind soul, I saw that my swap file was not activated, so I went through the instructions I found in this thread and viola... Well, I thought.  I was able to use my computer all yesterday evening and night without incident (at least 6 hours) and I left it logged on working on stuff all night and it was still working when I got up this morning.

I was typing a message rejoicing that it seems I have been able to get rid of the locks when the system locked again.  ](*,)

---

### Post by viz_e on 2006-06-26
> After being directed to this thread by a very kind soul, I saw that my swap file was not activated, so I went through the instructions I found in this thread and viola... Well, I thought. I was able to use my computer all yesterday evening and night without incident (at least 6 hours) and I left it logged on working on stuff all night and it was still working when I got up this morning.

I was typing a message rejoicing that it seems I have been able to get rid of the locks when the system locked again. 

Enabling the swap only postpones the crash... you simply make more memory available, but at some point also that would be full and then... kaboom... ](*,)

---

### Post by vinodis on 2006-06-26
The screen saver always freezes the Dapper for me.
So I disabled it.

---

### Post by Tobius on 2006-06-26
I just installed Dapper as a fresh install on my Shuttle. I've monitored the temperature and it's not overheating. I've tried running this app and that as well as running no apps at all, but I still get freezes (nothing responds).

The only thing special that I did during my install was remove prism54 and install ndiswrapper to get my wireless card to work. Everything else was handled by the install CD and Synaptic.

So add another poor soul to the hard freeze mix. With the machine sitting still (not running any apps except for Xorg) I get maybe an hour before it freezes. :-k

---

### Post by k225yt on 2006-06-26
Had the same (?) with Dapper on Acer TM2303WLMI laptop (768 Mb RAM, swap works, but is not used, no Xgl, etc). A couple of times it froze with nearly no programs running, maybe just a Konqueror window. BUT after a minute (or slightly more) of being frozen it resumed working.

---

### Post by dmizer on 2006-06-26
i've been strugling with this issue since breezy on a troublesome laptop.  finally gave up and installed fc5 on that box.

here's to show i gave it my best shot, and maybe it will help some of you.  most everything i did will work in dapper too:

[http://ubuntuforums.org/showthread.php?t=158359](http://ubuntuforums.org/showthread.php?t=158359)
[http://ubuntuforums.org/showthread.php?t=185560](http://ubuntuforums.org/showthread.php?t=185560)

---

### Post by nicolas314 on 2006-06-26
Reporting the same lockups here but somewhat less violent: on my desktop
computer I experience a total lockup of the machine after one hour or so.
Everything is frozen hard for a couple of minutes then I regain control and
everything works again. Leaving a terminal open running 'top' shows the main
power-consuming process is Xorg, nothing else seems relevant.

I also run Dapper on a laptop (Dell Latitude D610) and experience the same kind
of lockups, this time about 10 minutes after booting. Total freeze for about 30
seconds and then I regain control. I experienced up to 3 such freezes in a row.

After the lockups both machines seem to be running fine.

Both machines are running totally different hardware and the very same Dapper,
both were running fine with Breezy.

For reference:
Desktop is AMD Sempron with NVIDIA GeForce 5200
Laptop is Intel Pentium M with Intel Graphics chip

---

### Post by fozzieb on 2006-06-26
Ok i've switched to Fedora 5 to test for up to a week, just to make sure it's not my system.

can't be a gnome thing as kde users are reporting error too, can't be nvidia driver as ati failing too, Intel and Amd users both reporting error.

I will let you know how I get on in FC5

Cheers.

---

### Post by dspivey on 2006-06-26
I can save you the time, fozzieb.  I've got FC5 as the second part of my dual-boot system, along with Dapper, and it doesn't exhibit any of these problems.

---

### Post by clintonthegeek on 2006-06-26
So, has anyone filed a bug report or something of that ilk about this problem? I don't know how, but it would probably be a good idea, to get the Ubuntu developers' attention.

In the meantime I'm resizing my Kubuntu home partition and installing Fedora Core 5 on a seperate partition... hope I can work well in that until this gets addressed.

-Clinton

---

### Post by dmizer on 2006-06-26
difficult to file a bug on a problem that doesn't have a source yet.  there's no way that i've been able to determine to pinpoint the source of this problem.  kind of pointless to submit a bug report without knowing the cause.

---

### Post by Tobius on 2006-06-26
Well, it's been over 12 hours so far and nothing has crashed. All I did was disable the screensaver (technically I selected blank and dragged it up to the max; 20 minutes). Has anyone else tried this and had any luck with it?

---

### Post by mozetti on 2006-06-27
[QUOTE=vinodis]The screen saver always freezes the Dapper for me.
So I disabled it.[/QUOTE]

Same here.

---

### Post by fozzieb on 2006-06-27
The screensaver is not active on my system, so it never kicks in.

I'm in FC5 now (good to know it works ok) I will stay with it until we can figure out this bug, ubuntu for me is a much better platform.

Cheers.

---

### Post by viz_e on 2006-06-27
My screensaver is also disabled... but this does not help. An other remarkable thing is how regular are these freezes in the last days: I boot my notebook at 8.30 at work and about at 13 I get the first freeze in the day. The second one is more later and it depends on how much I am staying here ;)

---

### Post by gadgetwizard1 on 2006-06-27
OK..i have

oooops froze again!

tried all the 

oooops froze again!

different tips on the forum to stop the

oooooops froze again!

freezing problem with no..

ooooops froze again

luck at all!

I have changed back to 5.04 and have been running that for a good two weeks with no freezes at all..

Changing to 'vesa' made no difference and i have also compared my xorg file from 5.04 to 6.06 and they look the same..both use the ati driver.. i'm really running out of ideas with this one. BTW i also tried FC5 and that does not freeze at all. I do prefer Ubuntu though so in the mean time i'm gonna stick with what works until it's no longer supported and then try something else.

---

### Post by fozzieb on 2006-06-27
added a poll [here]("http://www.ubuntuforums.org/showthread.php?p=1186988#post1186988")


tell us what distro you have and what browser

I know not all options are there but most common ones are.

Cheers

---

### Post by dmizer on 2006-06-28
has anyone gotten this fixed?  if so, how (other than changing distro or version)?

assuming you were using the computer at the time, keep a record of exactly what you were doing at the time of the lock up ... click by click.

mine seemed to happen most frequently while clicking on menu items in the gnome panels.  i also had frequent problems when playing streaming media.

how many here are using transparency?  what other kind of desktop tweaks do you have?

---

### Post by gadgetwizard1 on 2006-06-29
I don't have any tweaks at all to the desktop. The freeze seems to happen when i click on the menu. Although it has happened at other times randomly. 

I can't find anything in the logs. The whole thing just stops. CTRL ALT DLT does not work, mouse does not work, keyboard does not work, the only way to clear it is to hold down the power button and reboot. As soon as the reboot is up everything works again until the next freeze. 

As i have said, until this is fixed or someone better than me can find a fix then i shall continue with 5.04. Which works perfectly.

Shame really, i liked the look of 6.06 and was ready to show it off to my friends and relatives.

---

### Post by dalu on 2006-06-29
I'm having a similar weird behaviour:

- @boot-up xorg takes longer than usual to load, giving a few seconds of black screen **before** the gdm login screen

- leaving the system as it is, doing nothing but staring at the screen, I notice a different ram usage in *top* and gnome monitor; I don't know if this is normal or not. the value in top is almost double.

- when I start clicking on menus and panels (not even opening programs, just browsing the menu) the memory value in top starts skyrocketing.

- started mplayer. after 50 minutes my ram was filled up (according to top) and later on swap is being used (1 gig ram). gnome monitor keeps saying it's ok at about 150mb used.

- closing all the open apps doesn't reduce memory consuption.

- restarting xorg frees up abou 50% ram, but the leak gets bigger again in no time.

- this happens in both ubuntu and xubuntu.


this is my first post, hello everyone :)

---

### Post by dolby on 2006-06-29
i have the same problem too. random freezes mostly when surfing. only thing that seems to "work" is the mouse pointer.tried by turning RenderAccel -->off in xorg.conf but it didnt really help. hope someone finds a solution for this asap

---

### Post by diesis on 2006-06-29
I have experienced random freeze of Dapper in these days.
Now I have passed more than 30 hours without a freeze.
The only difference is that now I don't use my PCMCIA wireless DLINK card.
It uses madwifi drivers.
**Maybe the problem is in madwifi.**

---

### Post by phillywize on 2006-06-29
Ugh...this is bad.

When my machine locks up, it's Xorg that does it...I know this because I can still log in from another machine using SSH (or NXClient, or whatever).  I usually save myself from having to reboot (and risk damaging my ext2 file system...bleh...need an ext3 driver for XP) by killing the Xorg process over the remote connection.  Right after I kill the process, I get a gnarly half-screen of green graphic gibberish, and then I guess the Xserver restarts and puts me back at the Ubuntu login screen.  What a pain.  And such a widespread problem.  A real shame for dapper.

---

### Post by SkyNet2029 on 2006-06-29
I also have occasional lockups, usually when I am running way too many processes. At any rate, this is a fresh install off the Dapper Cd from ship-it. Install was with no hiccups, picture perfect. Never used Automatix on this install . (I have previously and no problems there.) All I do is open up the dvd or a cd drive and then close it (empty), forcing the OS to rethink its state in life, dump the used memory, and i'm good. It only happens when I haven't used the machine for a couple of hours though, weirdness. For what its worth, my 'swappiness' is set at 70, with a gig of swap space, 256Mb sdram. Who knows. Only thing it actually coincides with is use of shipit cd. My previous install was breezy upgrade to dapper. Reinstalled just to clean up the HD. I have yet to restart over this 'issue' though, since I also like to type in 'uptime' and just smile. :lol:

---

### Post by dalu on 2006-06-30
the problem is still there after a fresh reinstall, no update no nothing.
could it be related to the partition table? When I had dapper installed without partitions (just swap) it seemed to work...

---

### Post by YourDoom123 on 2006-06-30
[QUOTE=viz_e]I also have some troubles with dapper:

* Dapper hangs once or twice a day: the HDD starts working like crazy for minutes. Sometimes I can fire up a top and see that the processor is dominated from either Xorg, firefox or thunderbird. Only fix: hard reboot.

* While using firefox, it sometimes happens that the page gets "refreshed" automatically, causing also an hang on for few seconds. Very annoying.

* Thunderbird is configured with an IMAP account. Once every two days, it starts downloading all messages headers from scratch... You can guess how much does it take (above all for the "Sent" and "Trash" folders).

* I have the "local" problem. Every time that I run something in the terminal (like oocalc) I get
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```
and it is also impossible to set the right charset.

Altogether, I sadly have to say that I am really disappointed by dapper, since Breezy did not have such problems (at least not the above-mentioned ones). I am considering to try again a fresh install and see whether I have some more luck.[/QUOTE]

hmm that looks very familiar... u didn't happen to add edgy repos to your sources.list file did you? i'm assuming not given your post, but given that the error is EXACTLY the same error that everyone who was testing edgy until last week saw... if you are using the edgy repos, then you need to upgrade, cause the problems were fixed. if not, sorry, i have no idea.

---

### Post by diesis on 2006-06-30
[QUOTE=phillywize]
When my machine locks up, it's Xorg that does it...I know this because I can still log in from another machine using SSH (or NXClient, or whatever)[/QUOTE]

Not in my case.
My machine totally freezes, keyboard and mouse are totally unrsponsive.
And this happenso only when using the pcmcia madwifi card.

---

### Post by viz_e on 2006-06-30
> 
hmm that looks very familiar... u didn't happen to add edgy repos to your sources.list file did you? i'm assuming not given your post, but given that the error is EXACTLY the same error that everyone who was testing edgy until last week saw... if you are using the edgy repos, then you need to upgrade, cause the problems were fixed. if not, sorry, i have no idea.

No, actually I only use Dapper repository... :roll: Both the lockup problem and the locale problem are quite spread, according to this forum and I assume that not all the people is already testing Edgy. Thank you for the suggestion anyway...

---

### Post by viz_e on 2006-06-30
[QUOTE=diesis]
**Maybe the problem is in madwifi.**[/QUOTE]

I have the madwifi driver installed, my I never use the wireless connection... I hope an update of Xorg will come out soon, this is one way to find out what is it happening.

How can I get back to Xorg 6.8 without reinstalling breezy? Is it possible?

---

### Post by ketsugi on 2006-06-30
Maybe not the Edgy repos, but what about the Xgl repos (which I am using)...?

---

### Post by Lster on 2006-06-30
I've had breezy crash once, but that's it. My Windows Xp computer crashes hourly - no joke!

---

### Post by Jango on 2006-06-30
That happened to me, when I tried to hook up my webcam and then scanner I believe. In my case that happened only when u actually connect the device to computer & they start to communicate. As many other problems that one was solved after update :)

---

### Post by Titan1958 on 2006-06-30
My Dapper freeze once a day since I installed new NVidia drivers :( Coincidence????

---

### Post by diesis on 2006-06-30
Today it has frozen without madwifi card.
The freeze occured when a gaim window tried to open over a gnome-terminal window.

---

### Post by cineboy on 2006-06-30
I am also getting complete freeze. No hard drive activity though, just locked up (keyboard, mouse, everything frozen) and must reboot. Can happen every 20-30 minutes, or I can run for a while longer. Seems to happen mostly when browsing in firefox. log files show nothing that appears related to issue.

I have a newish (4days) install with only a few programs installed, including Linksys NT drivers for WIFI card and HP printer dirvers, and what came with unbuntu install. Running ibm thinkpad t30.

I may try different browser, but currently at a loss.

---

### Post by dolby on 2006-06-30
i have a geforce2 mx/mx 400 graphics card and not installing the nvidia driver seems o have done the trick

---

### Post by Gnobody on 2006-06-30
My machine freezes whenever I play opengl games for more than a few minutes at a time (especially Enemy Territory), I thought it was a thermal problem at first but I've even re-applied thermal paste to all my componants and my temps have always been fine .  Could it be the NVidia drivers? It locks solid, and I hear a noise coming from my speakers that sounds like continous beeping

---

### Post by dspivey on 2006-06-30
I, too, experienced a long beeping sound today when my system froze again.  The beep is continuous and didn't stop until I shut down by holding the power button.

---

### Post by Gnobody on 2006-06-30
[LEFT]What were you doing at the time?  Do you have the propriatary Nvidia drivers installed?
[/LEFT]

---

### Post by dspivey on 2006-06-30
No, I don't have the Nvidia or ATI drivers installed.  The PC was frozen when I woke it from sleep this morning; the beep didn't start until the desktop came all the way up.

---

### Post by Tobius on 2006-06-30
I am definitely getting frustrated along with the rest of you now. I had previously thought that disabling the screensaver had fixed my freezing issues, but that was only a fluke that worked for a short while. What I have been able to surmise is that the problem appears to have something to do with reading/writing to the drive.

After a random period of time my machine will freeze up and when this occurs my clock continues working (turn on the seconds) and my mouse responds as well. But nothing else responds except for Ctrl-Alt-Backspace which takes me to a command prompt which will allow me to type in my username, but will never return to a password prompt. Instead I am presented with screen output like the following (about 30 seconds apart):

[17179694.756000] ata1: command 0x25 timeout, stat 0x58 host_stat 0x61
[17179724.756000] ata1: command 0x35 timeout, stat 0x58 host_stat 0x61
[17179754.756000] ata1: command 0x25 timeout, stat 0x58 host_stat 0x61
[17179784.756000] ata1: command 0x25 timeout, stat 0x58 host_stat 0x61
etc, etc, etc.

I'm using a RAID controller, but no raid configuration. My hard drive is a Seagate SATA 80GB. Whenever this happens my hard drive light will go out and come back on approx. once a minute.

Any ideas what else I can test to troubleshoot this further?

-tm

---

### Post by phillywize on 2006-07-01
So I'm seeing at least two things.

1.  Many people have either madwifi or Nvidia drivers (I have nvidia)

2.  The nature of the Xorg failure is one of three things:

[INDENT](a) the machine becomes sluggish, and is overwhelmed by the Xorg, thunderbird, or firefox process, but is otherwise functioning, if VERY slowly.

(b) the machine locks up, Xorg maxes out the CPU, but the machine is still accessible remotely.  You can get it back by killing the Xorg process remotely. (my situation)

(c) the machine locks up, and is absolutely, completely, flatly inaccessible, even remotely.[/INDENT]

Are there other patterns here?  Are bug reports filed (if so, under what?) (if not, I've never filed a bug report, but I'm happy to give it a shot, or augment current ones with logs, anecdotes, or whatever will help).

This seems like a widespread problem.  It's an unfortunate thing for Dapper, which is such a fine release otherwise.  But it's an embarassing comparison to XP...without this lockup problem, Dapper would be more stable than my XP install.  *With* it, I've got an unstable OS that I can't have confidence in.  I mean, even if XP has its problems, at least I know it's not going to wedge on me once or twice a day (I know, I know, many linux faithful seem to be unable to have a stable XP install.  Not me.)

Anyhow, I am exasperated.  One of these crashes took  a good bite out of my /home partition and spat it into lost+found as unintelligible and useless gobbledy-gook.

---

### Post by ketsugi on 2006-07-02
phillywize, that seems to describe my issue perfectly. I'd also add that if I use Xgl instead of Xorg, the same thing happens with the Xgl process.

I'm wondering if everyone who's experiencing this problem has the Xgl/Compiz repos enabled? I thought that perhaps it's the newer graphics libraries that are causing the problems.

---

### Post by viz_e on 2006-07-02
[QUOTE=ketsugi]phillywize, that seems to describe my issue perfectly. I'd also add that if I use Xgl instead of Xorg, the same thing happens with the Xgl process.

I'm wondering if everyone who's experiencing this problem has the Xgl/Compiz repos enabled? I thought that perhaps it's the newer graphics libraries that are causing the problems.[/QUOTE]

When I try Xgl, Xorg is still loaded (found via top). Is this the case for you too? This would explain, why you get the freeze while using Xgl.

---

### Post by phillywize on 2006-07-02
[QUOTE=ketsugi]phillywize, that seems to describe my issue perfectly. I'd also add that if I use Xgl instead of Xorg, the same thing happens with the Xgl process.

I'm wondering if everyone who's experiencing this problem has the Xgl/Compiz repos enabled? I thought that perhaps it's the newer graphics libraries that are causing the problems.[/QUOTE]

I don't run xgl/compiz or have those repos enabled...for me, it's just plain old Xorg 7.0 and Gnome.  My hunch is that this isn't one problem, but 3 or 4.  Maybe it's the nvidia drivers for me, xgl for you, madwifi for others, and something else altogether for still other people.  What a wreck!

I may try using the generic video driver, but it causes my screen to flicker.  Bleh.

Another related thought:  this seems to be a tough bug to catch since the lock-ups are random and fairly infrequent.  So it's hard to figure out whether corrective measures accomplish anything.

---

### Post by fozzieb on 2006-07-02
Yes, but all these drivers work on other distro's so it is still an problem with ubuntu and not the drivers or hardware.

---

### Post by ketsugi on 2006-07-02
[QUOTE=viz_e]When I try Xgl, Xorg is still loaded (found via top). Is this the case for you too? This would explain, why you get the freeze while using Xgl.[/QUOTE]

Nope, I mean when I load Xgl as my server in my gdm-custom.conf (or whichever file it is, I can't recall offhand), and this problem occurs, I see the Xgl process in `top` sucking my CPU dry.

---

### Post by phillywize on 2006-07-02
[QUOTE=fozzieb]Yes, but all these drivers work on other distro's so it is still an problem with ubuntu and not the drivers or hardware.[/QUOTE]
Quite true.

Which leaves me with...why?

](*,)

---

### Post by viz_e on 2006-07-03
[QUOTE=phillywize]
Another related thought:  this seems to be a tough bug to catch since the lock-ups are random and fairly infrequent.  So it's hard to figure out whether corrective measures accomplish anything.[/QUOTE]

It seems to be dependent, on how fast your memory is sucked... I have a crash about every 4 hours and the memory usage is monotonically increasing with time... :|
The only way to stop this process is to Ctrl Alt Backspace until you can...

---

### Post by fozzieb on 2006-07-03
I done afresh install on friday, the only things i have not installed yet are:

Amarok
K3b
Java support
Flash-nonfree

so far my system seems stable, but i will wait until friday before i get my hopes up.

does anyone else use these app's?

Cheers

---

### Post by dspivey on 2006-07-03
I use Sun Java fairly regularly, but I have had the crashes when Java wasn't running.  I also have Macromedia's Flash installed, but have crashed several times without my browser even being opened.  I have Amarok installed, but have only used it once in the last 3 weeks.

---

### Post by phillywize on 2006-07-03
[QUOTE=viz_e]It seems to be dependent, on how fast your memory is sucked... I have a crash about every 4 hours and the memory usage is monotonically increasing with time... :|
The only way to stop this process is to Ctrl Alt Backspace until you can...[/QUOTE]
Hmmm...I should see if I'm having a memory leak too.  I have a gig of memory, so I think it would take a long time for a leak to impact my performance (given my usage -- web browsing, etc., a gig is overkill...just had extra ram lying around).

Forgive the newb question, but I assume I can just look at the memory usage for the Xorg process in top, and check on it periodically to see if it's headed inexorably upward?

Thanks...

---

### Post by fozzieb on 2006-07-03
[QUOTE=phillywize]
Forgive the newb question, but I assume I can just look at the memory usage for the Xorg process in top, and check on it periodically to see if it's headed inexorably upward?

Thanks...[/QUOTE]


As far as i know that is correct.

@dspivey  

I had the crashes before even when running nothing but the app's i mentioned were still installed, now they are not installed and everything seems fine (so far)

Cheers.

---

### Post by viz_e on 2006-07-03
[QUOTE=phillywize]Hmmm...I should see if I'm having a memory leak too.  I have a gig of memory, so I think it would take a long time for a leak to impact my performance (given my usage -- web browsing, etc., a gig is overkill...just had extra ram lying around).[/QUOTE]

1.5Gb RAM - 1Gb Swap --> 4h... :-? :-? 

I usually use gaim, thunderbird, firefox and kile, so neither something special or memory hungry...

---

### Post by phillywize on 2006-07-03
[QUOTE=fozzieb]I had the crashes before even when running nothing but the app's i mentioned were still installed, now they are not installed and everything seems fine (so far)[/QUOTE]

Of those apps you mentioned, I am running k3b and sun java.  I think I may also have the non-free flash installed.  I tend to suspect that they aren't causing the freezes for me inasmuch as they don't seem to figure into the pattern at all.  In fact, there doesn't seem to be much of a pattern at all.

And I can't find any evidence in my log files either.  Maybe I'm looking in the wrong places, but the X log and others just don't seem to catch the event.  Although, I have to think that since my system doesn't look up COMPLETELY; that is, only the specific X session locks, there's no reason why the system inherently *couldn't* log the event.

I am not home now, but I am going to check into the memory leak angle.

---

### Post by fozzieb on 2006-07-03
[QUOTE=phillywize]I am going to check into the memory leak angle.[/QUOTE]

Sounds like a plan ;)

---

### Post by phillywize on 2006-07-04
[QUOTE=fozzieb]Sounds like a plan ;)[/QUOTE]
Well, of course now that I've committed to this course of action, Xorg has become the rock-solid graphics, forget it's there, not-a-peep server it has always been touted as.

Waiting for it to mess up...

---

### Post by illegaltender on 2006-07-05
Thank god, I'm not alone.  My problem appears to be the same as those in this thread.  My freezes seem completely random.  It used to freeze and be completely unresponsive, not being able to move my mouse, but I think installing flgrx changed that.  After that was installed, my mouse would move, but everything else is still unresponsive.  Although, if music is playing before the freeze occurs, it continues to play.  Both of these situations resulted in no combination of keystrokes being responsive.  My memory use hasn't went over 200mb, for what I have seen.  

I previously thought my random freezing was caused by my ATI card, but you guys have me thinking otherwise.  Just to confirm, there is no fix for this as of right now?  I absolutely love Ubuntu and I don't want to have to give up on it for a silly reason like Windows being more stable.:)

---

### Post by pangloss on 2006-07-05
I just voted in the related poll. I've been experiencing this issue sporadically:

mouse is not frozen, but applications seem unresponsive to mouse activity (e.g., can't click/drag windows, can't select other windows, can't select menus, etc. After minutes, I can somtimes get a mouse-click to register and switch windows. I can ctrl-alt-F# to switch ttys.

keyboard seems to work however: can start top in a (already open) terminal window and see that xorg is eating ~90% cpu. in an open firefox window, I can use shortcuts to close tabs or even tab between location bar and search bar.

FYI: using Dell Latitude D600 laptop with ATI card and 1.5 GB RAM. Only tweaks to a clean-install of Dapper with all updates was to install Sun JDK, network-manager, and SCIM.

EDIT: Just noticed that "user-switching" seems to make the freeze happen with slightly more regularity. FWIW, no such problems for the six months I was using Breezy on the same hardware.

---

### Post by BSDDomi on 2006-07-05
Hm I seem to be the only one who has no problems whatsoever with Ubuntu Dapper. I had a hard freeze a couple of weeks ago when Dapper was still beta when I had to hit the power button since nothing else would work but I haven't had any problems since - using Gnome. I use an Acer TravelMate 4101 WLMi laptop with Intel graphics. I believe that xorg is the problem here since I installed OpenBSD 3.9 on my desktop a couple of weeks ago and it froze the minute I had set up xorg and I also read about problems with the new versions of xorg.

---

### Post by sabitha on 2006-07-05
sometimes i got freezes too when i use webcam with gyach enhanced. but sometimes not.  ........ :confused:  i've never got this when used breezy =D>

---

### Post by Thund3rstruck on 2006-07-05
I have had this issue as well and I was able to isolate it to VMWare Server running WinXPSP2. Since weening myself off of VMWare (currently only using it for NewsLeecher) I have not had the issue

---

### Post by ketsugi on 2006-07-05
One other thing I've noticed is that for me, the issue only shows up when I'm actively using the computer. I can leave my system on all night without any problems, but once I start using it the Xorg issue will show up, sometimes within an hour.

---

### Post by phillywize on 2006-07-05
[QUOTE=Thund3rstruck]I have had this issue as well and I was able to isolate it to VMWare Server running WinXPSP2. Since weening myself off of VMWare (currently only using it for NewsLeecher) I have not had the issue[/QUOTE]
Interesting.  I too have vmware server running.

Presently I'm checking on the memory leak angle, and I'll look into the vmware server thing after that.  Sun Java also seems to be a common thread, but so many people have that installed that it doesn't reveal much if a bunch of us lock-up plagued types also have it running.

Is there any way to up xorg's logging level so that it will log every little thing?  My logs are clean as a whistle after a lock-up.

---

### Post by dspivey on 2006-07-05
I don't have vmware running (or installed).

---

### Post by phillywize on 2006-07-05
Ok, I filed a bug on this problem here:  

[http://launchpad.net/distros/ubuntu/+bug/51991](http://launchpad.net/distros/ubuntu/+bug/51991)

Jump on!  The more the better...

---

### Post by viz_e on 2006-07-06
[QUOTE=ketsugi]One other thing I've noticed is that for me, the issue only shows up when I'm actively using the computer. I can leave my system on all night without any problems, but once I start using it the Xorg issue will show up, sometimes within an hour.[/QUOTE]

This is not the case for me. I often get a freeze when I come back to the office after lunch, after about 4 hours of up time.

---

### Post by craigi on 2006-07-06
New Ubuntu user here who is very happy to see others are having the same problem.  Well, I'm not happy there's a problem, but it's nice to know I am not alone.

I've only been setting up Ubuntu for the past two days, but I've already experienced hard lockups (No mouse, no force-closing X, etc).  It requires a hard shut off of my computer and a restart.  I think I've had three.  One while playing World of Warcraft, and the other two just browsing websites (Firefox) with no other notable programs running in the background.   Actually, I may have had Amarok running at the same time

I am using an nVidia 6800 with the drivers that come in the repo.  I am also using a Netgear WG311T wireless card, SoundBlaster Audigy 2, and other standard hardware.  System is installed on an ATA hard drive.  There are two mounted NTFS drives located on a SATA controller and I do not have VMware installed.

I didn't discover this thread until today and I am at work at the moment, so when I get home I will reinstall a fresh copy of Ubuntu with minimal additional software and hardware installed.  I will also try some of the suggestions in this thread.  

Let's get this resolved for everyone! :D

---

### Post by dmizer on 2006-07-07
just fyi ... in top, to watch memory usage, you have to change the sort.  to change the sort in top do the following:
<shift>+f and select the letter 'n'  ... the n switch will sort the open processes with the biggest memory hog at the top of the list.

---

### Post by Shigun on 2006-07-07
> **craigi said:**
> New Ubuntu user here who is very happy to see others are having the same problem.  Well, I'm not happy there's a problem, but it's nice to know I am not alone.

I've only been setting up Ubuntu for the past two days, but I've already experienced hard lockups (No mouse, no force-closing X, etc).  It requires a hard shut off of my computer and a restart.  I think I've had three.  One while playing World of Warcraft, and the other two just browsing websites (Firefox) with no other notable programs running in the background.   Actually, I may have had Amarok running at the same time

I am using an nVidia 6800 with the drivers that come in the repo.  I am also using a Netgear WG311T wireless card, SoundBlaster Audigy 2, and other standard hardware.  System is installed on an ATA hard drive.  There are two mounted NTFS drives located on a SATA controller and I do not have VMware installed.

I didn't discover this thread until today and I am at work at the moment, so when I get home I will reinstall a fresh copy of Ubuntu with minimal additional software and hardware installed.  I will also try some of the suggestions in this thread.  

Let's get this resolved for everyone! :D

My symptoms are similar (I made an addition to the bug post about it as well), and I can attest that a fresh install of Ubuntu does not help.  I went from x86 6.06 to Amd64 6.06, and back, and experienced it on both x86's.  Did not have the Amd64 version installed long enough to tell.

My issue though, is I have never had a freeze where the mouse still worked.  Mine has **always** been a total freeze, with no operation at all.  I require a complete reboot.

---

### Post by craigi on 2006-07-07
I didn't get much time to fool around last night, but I did download and install Kubuntu, so I will stress it tonight to see if I have similar problems with hard lockups.

---

### Post by shanepardue on 2006-07-07
i too have had this issue, but it has only arisen recently. i've been running dapper since the beginning without problem, but since i installed my nvidia card, it started. my freeze is of the kind that the mouse and sound still operate while the rest of the system is completely unresponsive.

i see that this has been a problem for everyone else since dapper has been released.

i haven't seen any solutions yet..am i missing something?

---

### Post by phillywize on 2006-07-07
> **phillywize said:**
> Well, of course now that I've committed to this course of action, Xorg has become the rock-solid graphics, forget it's there, not-a-peep server it has always been touted as.

Waiting for it to mess up...
I haven't seen anything that looks like a serious memory leak.  I have watched for one over a good 5 days of intermittent use (I sleep my machine rather than shutting down/rebooting).  I have kept top running the entire time, and Xorg memory usage has gone up 13 mb from about 27mb to 40mb.  This doesn't seem earth-shattering, and won't slow my system appreciably.  I'm not even sure the 13 meg uptick would be attributable to a memory leak.  I will continue to keep an eye on it.

Of course, in the past 5 days, I have not had a freeze either.  So maybe whatever causes the memory leak hasn't happened in that time.  I will continue to watch.

I've noticed some people say that firefox is usually running when xorg wedges.  I think firefox is often running when I have problems too, but then again, I *usually* have it running.  :-k

---

### Post by ketsugi on 2006-07-08
I find that usually when I have the Xorg problem, the process' memory usage has gone up to about 200mb+.

---

### Post by viz_e on 2006-07-08
> **phillywize said:**
> I have kept top running the entire time, and Xorg memory usage has gone up 13 mb from about 27mb to 40mb. 

You are lucky then... ;) After about 4 hours it uses here more than 80% of 2.5Gb (1.5Gb RAM and 1Gb SWAP)... ](*,) ](*,) ](*,)

---

### Post by phillywize on 2006-07-08
> **viz_e said:**
> You are lucky then... ;) After about 4 hours it uses here more than 80% of 2.5Gb (1.5Gb RAM and 1Gb SWAP)... ](*,) ](*,) ](*,)

Wow betewen you and ketsugi, those are some major league memory leaks.  Still waiting for mine to mess up so I can take a look at the memory usage.  It seems like the leak happens pretty rapidly.  I'm not even sure I have it though.  We shall see...

---

### Post by crmccreary on 2006-07-08
I run a desktop with dapper. No problems. Never crashed.
On the other hand, I also have a Dell Inspiron 4100 with only 256MB memory, ati radeon mobility 9000. Hard lockups often. Often with Firefox. Swap is active (at least according to top)

---

### Post by william_nbg on 2006-07-09
Same problem on my wifes computer.

I recently upgraded both computers up to Dapper. Mine seems fine, I've never had a crash - though, I do have 2gigs of ram.

But my wife's computer crashes randomly, once, twice maybe more per day (and I'm catching hell for it, so I hope we find a solution soon).

On her last crash, I logged on to her via ssh and ran 'top' - sure enough, her 'xorg' was eating her entire cpu. 

After reading this entire thread, I'm not sure were to go??

Everything I can think of has been tried.

---

### Post by phillywize on 2006-07-09
> **william_nbg said:**
> After reading this entire thread, I'm not sure were to go??

Everything I can think of has been tried.
Heh...join the club.  I noticed you did, William_nbg, but others are heartily encouraged to add to [this bug report]("https://launchpad.net/distros/ubuntu/+bug/51991").*

Are you able to get the machine back if you do this, or something like it:
```
sudo kill -9 [xorg pid]
```

There seems to be two varieties of this problem -- ours, which is a lock-up, where you can still login remotely, and see that xorg's cpu usage is at 99%+.  Then others seem not to be able to login remotely at all.  Which might be a different issue altogether, or it may just be that some don't have a second computer lying around to login from, so they can't tell one way or the other.

*By the way, anyone know how to get a bug noticed, triaged, and all that?  I'd love to see if ours could get some attention from people with more knowledge than, for instance, me.

---

### Post by william_nbg on 2006-07-09
To Phillywize

Haven't tried the:

sudo kill -9 [xorg pid]

but will next time her pc freezes.

I just did a killall xorg from my computer, remotely, and was dropped back to her gdm screen.

Regarding the bug, yes I added to someone eles' bug report on launchpad. It was already reported earlier on this thread.

---

### Post by phillywize on 2006-07-09
> **william_nbg said:**
> To Phillywize

Haven't tried the:

sudo kill -9 [xorg pid]

That will do exactly the same thing as the killall command you've been using...i.e., drop you back to the login screen.  It seems to have no ill effects though.

---

### Post by Gus Tarballs on 2006-07-10
I think there are several different sources for all the freezes. 
One problem might be the madwifi/wlan component.
There is a bug-report "[madwifi] Semi-random system lockups in Dapper" ([https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773)) Bug #37773 that describes similar system behaviour.

Bug #15178 "fglrx hangs/crashes" ([https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/15178](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/15178)) might be relevant for others.
A search for "freeze" and "dapper" returns 170 Bugs...

In my case the system (Thinkpad x24) randomly freezes with no possibility to recover locally (I have not tried connecting via ssh yet). Firefox is running most of the time. I have madwifi running and this might be the source of the problem. A suggested solution (see discussion for Bug #37773) is replacing madwifi with madwifi-ng. I will try this next.

---

### Post by josepdin on 2006-07-10
> **berzerke said:**
> I've done some further experimentation on the problem. As I said before, the problem doesn't seem to be in Firefox itself. It just seems that Firefox (and Thunderbird) trigger something. I suspect that those who have the problem with VMware are in the same boat as I have yet to run VMware on this machine.

I was running the xorg nvidia drivers (nv) and decided to try the official drivers thinking it was a driver issue too. I didn't use Automatrix to install. I left Firefox open all night with only a simple static page. At the start, xorg was using a little less than 2% of my memory. By morning, it was up to 39%! No flash or Java on the page either.

So it appears that it's not the drivers (Anyone using non-nvidia cards?). My swap is on and working, so it's not a swap problem. I'm starting to think it is a xorg bug, possibly specific to Ubuntu.
 I am running a Dell Laptop and, I believe, an ATi video.  I'm sure it's not nvidia.  Same lockup problem here, as well.  Mostly when firefox is running, but not necessarily doing anything.

---

### Post by jvictor on 2006-07-10
Have u guys tried disabling AGP on nvidia cards .. that solved my problem.. well I dont game , so its not a big deal not to have AGP on for me :rolleyes:

---

### Post by william_nbg on 2006-07-10
> **jvictor said:**
> Have u guys tried disabling AGP on nvidia cards .. that solved my problem.. well I dont game , so its not a big deal not to have AGP on for me :rolleyes:

How do you disable the AGP??

Like I said earlier: looking at the frozen computer remotely, and running top, xorg is maxed out.

---

### Post by vampiric_blade on 2006-07-10
I've noticed that this problem has gone away (3 days no probs) since I disabled vbesave from the system services menu in the kde control center (system settings).

Edit:  I am running the nvidia drivers with agp enabled.

---

### Post by zjcim on 2006-07-10
r u using a ati card?
before ,my ibm x24 laptop just freeze frequently like yours

finaly i change the driver to fix it .
 install vesa diver ,and ¨dpkg-reconfigure xserver-xorg ¨ select the vesa not ati for the driver,and comment the ¨load dri¨ in xorg.conf

---

### Post by vampiric_blade on 2006-07-10
> **vampiric_blade said:**
> I've noticed that this problem has gone away (3 days no probs) since I disabled vbesave from the system services menu in the kde control center (system settings).

Edit:  I am running the nvidia drivers with agp enabled.


NM.  Just had my first freeze.  Bye Bye Dapper; hello Mandriva :)

---

### Post by jejones3141 on 2006-07-11
I have been having the problem of x.org freezing (but the mouse cursor still able to move, and the computer accessible via ssh) since Breezy Badger; it has to do with the nvidia proprietary driver (and possibly the VIA KT600 chipset).

For me, it started when I switched to a system I built using the ECS KT600A motherboard. The MX400 gfx card I was using gave weird errors, so I upgraded to an MX4000. Then I started to get the hangs with the nvidia driver.

I tried ATI, but couldn't get decent performance from the card I had.

Today I recalled that I have an MX4000 PCI card, and switched to it. I got the nvidia driver going, checked some GL screensavers to make sure they worked fine, started doing some browsing, and poof--the screen froze, the mouse cursor could still move. Unlike earlier freezes, though, it was able to notice ctrl-alt-bs and, after five or ten minutes, kill and restart the x.org server.

This has been a problem with the nvidia proprietary drivers literally for YEARS. Take a look at [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=31858") and [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=73231") on the nVidia Linux forum.

BTW... the MX4000 card that caused the problem got moved to another system of mine, using an ECS K7S5A motherboard and an Athlon 2100. Works like a charm with the nvidia proprietary driver and Dapper Drake. (compiz dies on it, but that's still experimental, so that's to be expected for now.)

I can't wait for an open source graphics card so I can tell ATI and nVidia both to go do something rude and anatomically impossible.:evil:

---

### Post by ketsugi on 2006-07-11
I disabled AGP on my X setup and so far no problems... Hopefully it stays that way.

To disable AGP (assuming you're using the Nvidia drivers), edit your /etc/X11/xorg.conf file and look for a line that says

```
        Option          "NvAGP" "1"
```

and change the 1 to a 0.

---

### Post by jejones3141 on 2006-07-11
> **ketsugi said:**
> I disabled AGP on my X setup and so far no problems... Hopefully it stays that way.

To disable AGP (assuming you're using the Nvidia drivers), edit your /etc/X11/xorg.conf file and look for a line that says

```
        Option          "NvAGP" "1"
```

and change the 1 to a 0.
Alas, it made no difference in my case.

---

### Post by Gus Tarballs on 2006-07-11
> **zjcim said:**
> r u using a ati card?
before ,my ibm x24 laptop just freeze frequently like yours

finaly i change the driver to fix it .
 install vesa diver ,and ¨dpkg-reconfigure xserver-xorg ¨ select the vesa not ati for the driver,and comment the ¨load dri¨ in xorg.conf

Thanks for your advice. I just changed my config and so far I have had no freeze in the last couple of hours. I will test it some more and post if any freezes occur.
How about your video performace? Will disabling DRI and using the vesa driver prevent hardware acceleration?
If so, that would be a solution for the freeze problem, but at a very high cost.

---

### Post by phillywize on 2006-07-11
> **ketsugi said:**
> I disabled AGP on my X setup and so far no problems... Hopefully it stays that way.

To disable AGP (assuming you're using the Nvidia drivers), edit your /etc/X11/xorg.conf file and look for a line that says

```
        Option          "NvAGP" "1"
```

and change the 1 to a 0.
I'm going to try that, since I do have AGP active...but I think I need it for ACPI sleep to work.  We'll see.  Devil and the deep blue sea...

I just had my first freeze in more than a week though...when I looked at the Xorg process in top, it was using a reasonable amount of memory (52 mb or so?).  In any event, it wasn't the 200mb or 1.5gb that people have had with memory leaks.  So I don't think my lockup problem is of the memory leak variety.

Thanks all...

---

### Post by jejones3141 on 2006-07-11
> **Gus Tarballs said:**
> Thanks for your advice. I just changed my conifg and so far I have had no freeze in the last couple of hours. I will test it some more and post if any freezes occur.
How about your video performace? Will disabling DRI and using the vesa driver prevent hardware acceleration?
If so, that would be a solution for the freeze problem, but at a very high cost.
If I understand rightly, the VESA driver supports the bargain basement VGA interface that everybody supports for backwards compatibility, and is utterly unaccelerated.

---

### Post by Tobius on 2006-07-11
This really sucks. I had to give up and install another distro (Suse) as the freezes were just happening too often to ignore. But I loved Ubuntu Dapper and really want to switch back when this issue gets resolved.

Some of you said that everything worked fine in Breezy, but then these freezes happen in Dapper. Have you been able to compare your xorg.conf files between the two? Maybe that will shed some light on things. Just a thought.

-tm

---

### Post by sdhoigt on 2006-07-11
First post.  Read entire thread, and I had that same problem as the majority of us is/was having.

My system:
-AGP Nvidia video card (seems to be the causing factor)
-Running proprietary Nvidia driver

My prob:
1. Freeze at seemingly random moments of user activity.
2. SSH from another machine reveals xorg running 99% CPU.

Summary of my "fix":
1. Ran sudo dpkg-reconfigure xserver-xorg
2. Deselected 'nvidia' and selected 'nv'

No more freezing after a good 24 hours of banging at the keyboard.  No more acceleration till this issue is addressed.  Nvidia, rot in hell.

SD

---

### Post by ketsugi on 2006-07-11
Ever snce I turned AGP off I've not had the problem, so that seems to be working for me.

---

### Post by dspivey on 2006-07-11
I seem to be the odd man out in this thread.  I'm having the freeze/crash issues as well, but DO NOT have an Nvidia (nor ATI) card or driver installed anywhere on my system.

---

### Post by Damwid on 2006-07-12
I have same problem on my IBM T30 with ATI 7500 video card since update to dapper, freeze always occur when screen redraw. Today I found another case that freeze everytime: start amule, change the "Standard client TCP Port" and "Extended client UDP Port" to another number, restart amule, then the computer freeze. So I guess this maybe not a video card problem.

---

### Post by Metacarpal on 2006-07-12
I ran into this today, and I have a thought:
This problem has less to do with video and more to do with wireless.  To check that: **if you're experiencing the bittorrent freeze and are NOT using wireless, please reply!**

But from what I've been seeing (and I'll admit to having skimmed a page or three), it is at least predominantly a problem for those of us using wireless to connect.

I tried running Azureus while specifically avoiding anything else that connects to the internet.  I was able to DL files through torrent for over an hour with no problems.  I played games to kill the time (majhongg and frozen-bubble) and had no problems... but if I opened Firefox, Synaptic, or anything else that connects to the 'net - BOOM-crash within minutes or less.

So I think it has something to do with how the torrent (and based on others' Amule problems, P2P in general) make use of the wireless connection, or in how the wlan is managed.

I'm praying this will be sorted out with the wireless improvements promised in the 2.17 kernel, but perhaps the lovely folks in Ubuntu dev can be of service.

---

### Post by ketsugi on 2006-07-12
Nope, sorry, my problems have nothing to do with wireless. I haven't managed to get my Linksys WPC54Gv2 card working with WPA under Ubuntu, so I'm relying on good ol' Ethernet 100.

Also, my freezes have nothing to do with BitTorrent.

I think we're looking at completely different problems here with similar symptoms.

---

### Post by viz_e on 2006-07-12
What about trying to get back to xorg 6.8 in dapper? Any idea how to do this?

---

### Post by william_nbg on 2006-07-12
The wireless therory dosen't sound bad to me.

We have a wireless network:

wife acx111

me ra2500

And my wife's computer, all but once, froze during internet activity.

Like I said earlier, I haven't experienced any problems with the Dapper upgrade, it's running perfect. 

My wife's computer suddenly stopped freezing, it's been 2 or 3 days now - knock on wood - let's wait and see.

---

### Post by phillywize on 2006-07-12
> **Metacarpal said:**
> I ran into this today, and I have a thought:
This problem has less to do with video and more to do with wireless.
I don't doubt that you're having wlan problems, but I have to agree with ketsugi here:
> **ketsugi]I think we're looking at completely different problems here with similar symptoms.[/QUOTE]
There's a definite wireless issue here, and a definite nvidia issue.  From my limited knowledge, lockups under linux are usually attributable to driver problems...so it makes sense that if you're having lockup problems, you've got a driver issue of *some* variety, but not necessarily the *same* driver issue as the next person.  Ergo, this should be three or four threads instead of one.

To that end, there is an nvidia driver bug report at [http://launchpad.net/distros/ubuntu/+bug/51991]("http://launchpad.net/distros/ubuntu/+bug/51991").

I know some people on this thread have had problems with madwifi drivers, and others some fglrx problems...here is a helpful post with links to bug reports on those:
[QUOTE=Gus Tarballs said:**
> I think there are several different sources for all the freezes. 
One problem might be the madwifi/wlan component.
There is a bug-report "[madwifi] Semi-random system lockups in Dapper" ([https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/37773)) Bug #37773 that describes similar system behaviour.

Bug #15178 "fglrx hangs/crashes" ([https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/15178](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/15178)) might be relevant for others.
A search for "freeze" and "dapper" returns 170 Bugs...

In my case the system (Thinkpad x24) randomly freezes with no possibility to recover locally (I have not tried connecting via ssh yet). Firefox is running most of the time. I have madwifi running and this might be the source of the problem. A suggested solution (see discussion for Bug #37773) is replacing madwifi with madwifi-ng. I will try this next.

---

### Post by Gus Tarballs on 2006-07-12
I agree to the "different problems, similar symptoms"-theory. 

I just wonder if there might be a problem with certain combinations of packages/hardware. 

In my case the Thinkpad X24 works without any problems since I switched to vesa drivers. However I don't think that the ati (or nvidia) drivers have a general problem. This would be a major bug and many other people would have noticed. 

I know this would be hard to prove but I think there are many people out there using the ati or nv drivers without any freezes...

---

### Post by Ingla on 2006-07-12
Hello.

I just discovered this thread while searching for Ubuntu crash information.

The thing is, I've been holding back on upgrading to Dapper to see what kind of upgrade problems needed addressing.

I've begun having total lockups ON BREEZY recently. Nothing works but hitting the button. This has never happened while I was actually at the computer ... I just come back to find a total freeze. Breezy has never had this problem in the months I've been using it.

Firefox has also been crashing a lot. This never used to happen ... it just turns off in the middle of reading a page. Also exhibits an automatic reload problem which causes the cursor to change to something similar to what Thunderbird shows when it's trying to move a folder. Sometimes this lasts a few seconds and I regain control. Sometimes it doesn't let go at all and I have to hit CNTRL+ALT+BCKSP (which doesn't work with the system freeze).

All of this (plus a few other oddities) are recent developments, which make me wonder if some system update isn't responsible. I usually just let Ubuntu update whatever the Update Manager wants to. Maybe some recent update has changed Breezy by updating to something that's standard in Dapper.

FWIW this is not due to a system upgrade or fresh install of Dapper. I haven't installed any new programs or changed any configurations, drivers, or anything else. Unfortunately, I haven't kept track of the routine updates, so I can't pinpoint what's happened.

I'm wondering if it's possible to get a list of the updates over the past month or two. Maybe that could narrow the field.

This is very bad, as I had almost been able to move business functions from XP to Ubuntu completely (there's still an issue of migrating a data base) and was hoping to use Linux exclusively. Now there's a serious stability problem!

It would also be interesting to know if any other Breezy users have caught this disease.

---

### Post by viz_e on 2006-07-13
> **phillywize said:**
> 
There's a definite wireless issue here, and a definite nvidia issue.


I am not using wireless and I have an ati card... My PC is up since 40 min and Xorg is already using 109Mb of RAM and 145Mb virtual.

My guess is that a lot of people have a problem related to xorg and not to drivers (at least directly).

Update: after 2h: 215 RAM, 291 Virtual

Update2: after 4h: 768 RAM, 804 Virtual (usually I have a crash after 4 hours, now the system is stable)

Update3: crashed 1Gb barrier of RAM after 4h40min

---

### Post by doboy007 on 2006-07-13
It's funny but Dapper seems to be more prone to freezing after ACPI resume. My general experience is that Dapper is less stable than Breezy and is less stable than Warty, particularly with respect to ACPI power management.

---

### Post by lonelypauly on 2006-07-13
Im having the same problem...computer locks up, typically when i have firefox open.  Ive noticed that firefox will just randomly crash/shut down in dapper...never happened in breezy.  During one lock up a week ago, my screen looked like a ROM-check from an 80's video arcade game...which makes me think it could be my vga driver.
I shut off my screen savers a long time ago, and that seems to make my crashes less frequent.

So where do we go from here?

---

### Post by phillywize on 2006-07-13
> **viz_e said:**
> I am not using wireless and I have an ati card... My PC is up since 40 min and Xorg is already using 109Mb of RAM and 145Mb virtual.

My guess is that a lot of people have a problem related to xorg and not to drivers (at least directly).

...

Update3: crashed 1Gb barrier of RAM after 4h40min
Yow!

So problem #4:  an xorg memory leak.

To whit, and in no particular order, it looks like this thread is covering:

-- madwifi freezes
-- proprietary nvidia driver freezes
-- xorg memory leak
-- fglx freezes

-- anything else?

Perhaps we should break this into 4 threads?  We could use this thread as kind of a diagnosis place to direct people who are having general lockup problems to the right place...since these various problems all have very similar symptomology.

---

### Post by phillywize on 2006-07-13
Here is a bug report that matches the nvidia issues.  It's fairly well-developed, and seems to go back to Hoary:

[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/13530]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/13530")

---

### Post by bbarrons on 2006-07-13
I also had to deal with the same issue this past week. I thought it was network related so I changed cards.... nope.... changed memory and even added 256...helped but didnt solve it. I took out my ati rage pro and put in an an old matrox mystique video and it solved the problem. The lockups were sudden and the only way to resolve was a hard boot. (powerdown)
 I have since reinstalled the ati card but removed anything I had done to try and make the card work better. I went with what was installed with dapper on fresh. has worked fine since.
 Bill

---

### Post by viz_e on 2006-07-14
Today there is an update of the xserver-xorg-core package, it does not seem to solve the memory leek, though. :-k

---

### Post by william_nbg on 2006-07-14
Yes, the new update seems to have fixed my wifes computer as well. She's been running all day and hasn't had a crash all day (knock on wood).

I'll keep you posted.

---

### Post by Shigun on 2006-07-14
I can possibly support the wireless mention.  I have a wireless card, and my computer now seems to freeze when I run bittorrent.  I first thought it was Azureus, so I downloaded bittornado, however it occurs with that client as well.

---

### Post by lamego on 2006-07-15
It could be related to ACPI, try adding the noacpi option on your kernel options (/boot/grub/menu.lst)

---

### Post by william_nbg on 2006-07-15
Two days of full-time use and my wife's computer still has had another freeze, she's happy, which means I have a chance to be happy.

Keeping our fingers crossed.

---

### Post by Shigun on 2006-07-15
> **Shigun said:**
> I can possibly support the wireless mention.  I have a wireless card, and my computer now seems to freeze when I run bittorrent.  I first thought it was Azureus, so I downloaded bittornado, however it occurs with that client as well.

Well, I kinda shot down my own Wireless theory.  I was running a game (Oblivion) via Cedega, had to run off, so I just turned off my monitor.  When I came back - frozen.

---

### Post by cineboy on 2006-07-15
I updated to the latest - just released -  xserver-xorg-core package and it appears my screen/system freezes have diappeared. I will continue to monior.

---

### Post by ctaggart on 2006-07-15
I removed Windows and installed Ubuntu Dapper last weekend.  I have been having a lot of stability problems.  It is freezing up every half hour or so lately.  I'm not sure what is causing it.  I used to run Gentoo on this desktop prior to Windows.  Back then, I didn't have a wireless network card. I have a wireless Netgear card.  That could be the problem, or it could be the xorg 7.0 release, or ACPI.  I've tried various ACPI kernel parameters without any luck.  I may disable the wireless card and see if that helps, but the main point in using the computer is for using the intarweb.  I also uninstalled the nvidia driver and reinstalled xorg, but no luck.

July 16 (next morning) update:

Even with ath0 disabled, it locked up overnight.  I wasn't running anything but the card game, freecell.  Taking a look at the modules, I'm obviously running more stuff.  Hmm, not sure why nvidia is still there.  I've got xorg using "nv".  I think I'll try disabling some modules and possibly even shutting down xorg to try and narrow down what the problem or problems are.

July 18th update:

It crashes when I'm not in X, so probably not xorg.  I had a crash during boot during or just after the file system check and the kernel spewed out a  bunch of stuff about interrupts and do_softirq.  I took a picture with my digital camera and will post it when I get a chance.

July 24th update:

It looks like the root cause of all this for my computer was a hardware problem.  One of my RAM modules went bad after 4 years of use.  Thanks for including the Memtest!

Cameron

---

### Post by Shigun on 2006-07-15
Well, I tried the noacpi kernel option.  Started up Azureus and about 10 mniutes later my system froze.  Still searching for a solution, or im going to have to start looking for a new distro.

---

### Post by handaxe on 2006-07-16
Other variables into the mix - I can trigger a lock-up by opening 2 external HD attached via separate usb ports.

Weird thing is, I have seen total lock-ups and a variety of partials - i.e. different functionalities remaining.

Acer TM 5612WSMi Intel Core duo, Nvidia GeF Go 7300, Intel Pro 3945 wireless, 1 gig ram.

This looks a messy one judging by this thread...

HA

---

### Post by alanphil on 2006-07-16
I've been running Dapper since late beta version, on a Thinkpad X30 laptop. I'm also running Dapper on two desktop machines. Both desktop machines have been very stable. The Thinkpad has the freezing problem. I've been trying various things to figure out the problem, but so far no luck. :confused: 

The last experiment was to try XFCE desktop. I was able to run for almost 48 hours without a problem. This morning I had a lockup which seemed unrelated to what I was doing. I did not have Firefox running, and was just tweaking configs in an email client (sylpheed). I've been running with Top open, but have not seen anything odd with memory use. 

At this point I'm thinking about a complete reinstall to see if that helps. I've installed and removed lots of stuff on this laptop, and wonder if I may have contributed to the problem. I may install a stripped down Xubuntu and run for awhile with no additional tweaks to see if a base system is stable. 

Are there any log files I could check that would provide insight into what is happening when the system freezes? Can we turn on additional logging so that we can start tracking this problem better?

---

### Post by alanphil on 2006-07-16
I've copied a portion of my system log below, that shows what was happening during the last freeze. Points to note: Restart at 9:54, Freezing CPUs at 10:18 -- what is that? I pulled the USB mouse (Restarting tasks) at 10:18:55 which didn't unfreeze the system, and so at 10:19:02 I hit the power button. Any clues to what the problem may be? Any help greatly appreciated! I really don't want to reinstall if I can fix this some other way! Thank You! ](*,) 


Jul 16 09:54:18 localhost syslogd 1.4.1#17ubuntu7: restart.
Jul 16 09:58:12 localhost kernel: [17180265.580000] pccard: card ejected from slot 0
Jul 16 09:58:12 localhost kernel: [17180265.648000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Jul 16 09:58:13 localhost kernel: [17180265.916000] device eth0 left promiscuous mode
Jul 16 09:58:13 localhost kernel: [17180266.236000] ACPI: PCI interrupt for device 0000:01:08.0 disabled
Jul 16 10:18:55 localhost kernel: [17180268.804000] Freezing cpus ...
Jul 16 10:18:55 localhost kernel: [17180268.804000] Stopping tasks: ======================================================================================|
Jul 16 10:18:55 localhost kernel: [17180269.344000] ACPI: PCI interrupt for device 0000:01:00.1 disabled
Jul 16 10:18:55 localhost kernel: [17180269.344000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Jul 16 10:18:55 localhost kernel: [17180269.344000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
Jul 16 10:18:55 localhost kernel: [17180269.344000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Jul 16 10:18:55 localhost kernel: [17180269.344000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Jul 16 10:18:55 localhost kernel: [17180269.344000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Jul 16 10:18:55 localhost kernel: [17181508.344000] **** SET: Misaligned resource pointer: da2e26e2 Type 07 Len 0
Jul 16 10:18:55 localhost last message repeated 4 times
Jul 16 10:18:55 localhost kernel: [17181508.364000] PCI: Enabling device 0000:00:1d.0 (0000 -> 0001)
Jul 16 10:18:55 localhost kernel: [17181508.364000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.364000] PCI: Enabling device 0000:00:1d.1 (0000 -> 0001)
Jul 16 10:18:55 localhost kernel: [17181508.364000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.364000] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
Jul 16 10:18:55 localhost kernel: [17181508.364000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.364000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.364000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.368000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.368000] ACPI: PCI Interrupt 0000:01:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.368000] ACPI: PCI Interrupt 0000:01:00.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:55 localhost kernel: [17181508.752000] Restarting tasks...<6>usb 2-1: USB disconnect, address 2
Jul 16 10:18:55 localhost kernel: [17181508.832000]  done
Jul 16 10:18:55 localhost kernel: [17181508.832000] Thawing cpus ...
Jul 16 10:18:55 localhost kernel: [17181508.992000] usb 2-1: new low speed USB device using uhci_hcd and address 3
Jul 16 10:18:56 localhost kernel: [17181509.200000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input5
Jul 16 10:18:56 localhost kernel: [17181509.200000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
Jul 16 10:18:57 localhost kernel: [17181510.720000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
Jul 16 10:18:57 localhost kernel: [17181510.720000] e100: Copyright(c) 1999-2005 Intel Corporation
Jul 16 10:18:57 localhost kernel: [17181510.724000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:57 localhost kernel: [17181510.748000] e100: eth0: e100_probe: addr 0xd0200000, irq 11, MAC addr 00:09:6B:60:D0:79
Jul 16 10:18:58 localhost kernel: [17181511.360000] pccard: CardBus card inserted into slot 0
Jul 16 10:18:58 localhost kernel: [17181511.360000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Jul 16 10:18:58 localhost kernel: [17181511.360000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 16 10:18:58 localhost kernel: [17181511.360000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
Jul 16 10:19:02 localhost kernel: [17181512.692000] ACPI: Power Button (FF) [PWRF]

---

### Post by phillywize on 2006-07-16
An nvidia driver-related theory that was getting a bit of airplay here over the last week or so is that there's a problem with the agp...

To that end, I disabled NvAGP in my xorg.conf, and have been freeze-free for about 4 days now.  Of course, that means **_absolutely nothing_**.  My freezes are anywhere from a few hours to more than a week apart.  A few stable days doesn't mean much.

But as someone said earlier, this problem *is* a mess.  This thread almost certainly represents a multiplicity of issues with similar symptoms.

---

### Post by Shigun on 2006-07-16
Well, i'm confused now.  Azureus is running, firefox is running, and I havent had a crash in several hours.

---

### Post by Tyltyl on 2006-07-17
Ok, I can add my weird experience.
Recently I had a strange problem on my PC (also on Windows): sudden shutdowns and reboot, PC doesn't even make *beep* on startup etc.
While trying to figure it out, my Ubuntu started to freeze occasionally and I thought it was still for a hardware problem, but it's not because I now have a new MoBo, a new power supply and I removed a bad RAM block.

1st freeze (before the system "upgrade"): About 20 minutes after a fresh startup. I was using K3B only and I was 85% in the burning. I could move the mouse but the system was completely unresponsive. I could even open the DVD rewriter although it was burning a second before.

2nd freeze (before the system "upgrade"): 5 minutes after a fresh startup while I was simply surfing. Only Firefox was opened and I could only move the mouse.

3rd freeze (after the system "upgrade"): After 1 or hour and a half. I had Firefox and XPN opened, and I was doing a huge untar of my backup (about 800 MB tarred of a 2.3GB backup).
Same as before I could only move the mouse around.

Nothing seems related to my previous problem and the situations  are very different.
I have Ubuntu since end november 2005 and never had such a problem, but I don't remember what changes were made before the freezes.
I have a P4 2.5GhZ, 512 RAM (before I had 1GB) and an ATI Radeon 9700.
Temperatures are more than ok now: about 38°C for MoBo, 30°C for CPU and about 38-40°C for the HD.

Now I only use Windows, since I don't want to cause anymore problems to my system since I had a critical upgrade.

EDIT: I forgot an important part. Before the upgrade I also used the 6.06 Live DVD and still had a freeze!!! About 30 minutes of use and I was using GAIM and Firefox. My HD wasn't even plugged in since I was trying to figure the problem.

---

### Post by Tyltyl on 2006-07-17
I just had another freeze while doing a search with Firefox on the forums.
I also made a backup with a huge tar and burned to a DVD without problems. So it seems impossible to me to reproduce, it's just completely random.

---

### Post by lean on 2006-07-17
I also experience crashes. The easiest way for me to crash is to open Armadillo Run in wine (an opengl game), and then tab out of the game. This made me suspect that it is an open source ATI problem.
How many of you are running with the default drivers and an ATI card?

I have tried to run the memory checker at boot, it shows no errors.

Also one of the crashes send me to a kernel error, with backtrace to IRC and ACPI.

---

### Post by lean on 2006-07-17
Okay, I have a reproduceble crash. Could other people please try it out.
I have made a bug report here:
[https://launchpad.net/distros/ubuntu/+bug/53228](https://launchpad.net/distros/ubuntu/+bug/53228), please reply in the bug.

---

### Post by Tyltyl on 2006-07-17
I would try to change my drivers, but I think it will be useless since it happened also with the live CD which uses the vesa and still caused a freeze.
The freezes once were very occasional, but now they are getting more and more frequent and I had 3 just this morning.

---

### Post by Shigun on 2006-07-17
Well, so much for my stability.  Started up Azureus last night, went to bed, woke up and my system had frozen at 3:49 AM.  Back to the drawing board.

---

### Post by Tyltyl on 2006-07-18
I used Ubuntu for a whole evening without problems. Then this morning it freezes after 30 minutes.
Still no clue...

---

### Post by handaxe on 2006-07-18
Just a thought - how many here have SATA drives?

At least one - Tobius - has the exact same error messages as do I. There were SATA problems during development and I believe SMART technol was patched into the Dapper kernel as is is integrated only from 2.6.16 onwards.

So is there a SATA related freeze as well as perhaps others?

HA

---

### Post by Pawel on 2006-07-18
> **phillywize said:**
> Yow!

So problem #4:  an xorg memory leak.

To whit, and in no particular order, it looks like this thread is covering:

-- madwifi freezes
-- proprietary nvidia driver freezes
-- xorg memory leak
-- fglx freezes

-- anything else?

Perhaps we should break this into 4 threads?  We could use this thread as kind of a diagnosis place to direct people who are having general lockup problems to the right place...since these various problems all have very similar symptomology.


Hello!


Me and my Brother have the same copmuters. On my machine - this problem never shows, on my Brtoher's machine it occurs usually when firefox is running.

My machine freezes only when i try to use apps with use OpenGL, like XMMS openGL plugin or planet penguin racer (for tests only).
Sometimes it freezes on xgl/compiz (now its disabled).
------------

It's not only NVidia users problem!
-> It's not only official ATI drivers users problem.
--> I think that it's also a bug in open source radeon driver (especially when you use openGL), but it isn't only the one case of this global problem.

PC:

RAM: 256 DDR II
CPU: INTEL Celeron 2,4 ghz
HDD: connected via IDE cable
MainBoard: Asrock sth. I don't remember what is it. At now i'm in  work so if sb. will be interested - i will wrote later.
Graphic: ATI Radeon 9250 (9200se/pro) by Excalibur.
-----

As people say:
Log files dosen't reproduce anything, that may be helpful...
System just freeze.

Only one difference between Dapper mine and my Brother is kernel.
My kernel version is 2.6.15-23(default kernel of dapper).
My Brother have the newest version of kernel.
---------------------------------------------

Thanks for people who try to slove this problem!
Best regards and sorry for my english :)

Paul

---

### Post by Tyltyl on 2006-07-18
> **handaxe said:**
> Just a thought - how many here have SATA drives?

At least one - Tobius - has the exact same error messages as do I. There were SATA problems during development and I believe SMART technol was patched into the Dapper kernel as is is integrated only from 2.6.16 onwards.

So is there a SATA related freeze as well as perhaps others?

HA

No SATA here, and it also happened to me with the Live CD without the HD plugged in.
That doesn't mean in can't also be caused by SATA though...could be everything to me.

---

### Post by Tyltyl on 2006-07-18
I changed the AGP 4x and disabled fastwrite. No change. I tried with XGL instead of Xorg and I still had 2 freezes, even without using Firefox (so FF it's not the cause)
No idea what else to do...maybe changing the ACPI options.

What I want to know is why this problem appears all of sudden to many people after months and months of use without problems.

---

### Post by alanphil on 2006-07-18
I gave up trying to fix the freeze problem on my laptop and have installed Zenwalk linux ([http://www.zenwalk.org/)](http://www.zenwalk.org/)). Basic install was easy, but I need to tweak some things to get suspend and battery monitor working. This Thinkpad X30 is much faster with Zenwalk, so if I can get everything working properly I don't think I'll miss Dapper on this machine. :-|

---

### Post by Tyltyl on 2006-07-18
> **alanphil said:**
> I gave up trying to fix the freeze problem on my laptop and have installed Zenwalk linux ([http://www.zenwalk.org/)](http://www.zenwalk.org/)). Basic install was easy, but I need to tweak some things to get suspend and battery monitor working. This Thinkpad X30 is much faster with Zenwalk, so if I can get everything working properly I don't think I'll miss Dapper on this machine. :-|

I know how you feel, I'm about to reinstall Ubuntu as a desperate move but I know it won't work since I have the same problem with the live CD. No hope.

I think that if I can't find a fix soon I will look at the bright side and try a new distro :)

---

### Post by gotung on 2006-07-18
I seem to be having this issue as well. On both a dual xeon and dual operton machine.


On the xeon machine everything, including keyboard just locks up. On the opteron machine one of the processors goes to 100% usage.

This issue seems to consistently pop up when I run Activity Monitor. But it also happens at seemingly random times.

I tried installing Fedora Core 5, and the same thing happened. Maybe it is a problem in the latest X.org with multiple processors? (and/or hyperthreading?)

For now I am just going back to Breezy, had zero issues with it.

---

### Post by cineboy on 2006-07-18
updated xorg and did not have a freeze up for more than 48 hours of computer continuously being on, and a fair amount of use. That after I was getting rather predictable freezes every 20-30 minutes. Then the freezing started up again. No idea what is causing it.

---

### Post by czerwinski1977 on 2006-07-19
Pew... I found somebody with the same problem now!

I also run a T30, system is SUSE 10.1 but problem is the same: The entire system freezes (sometimes) when I start aMule. It once happened when I pushed the "Preferences" button, and once or twice when running inkscape.

Once aMule is up and running it remains stable.

The problem is noticable since ~1 week. Maybe there is a buggy update known?

To understand the situation: I expect the bug to be located somewhere in the "system"-libraries and NOT in an application, because applications cannot crash the whole system. -- Is this right?

Thanks,

Cz.

---

### Post by czerwinski1977 on 2006-07-19
Ah, I forgot to say: I thought that maybe some files were severely screwed up, and I re-installed the system. Did not help... ;(

---

### Post by Shigun on 2006-07-19
Well, i'm sorry to say, this issue has pushed me too far.  I moved on to pure Debian now.  But, I have not been put off from Ubuntu forever.  I'm probably going to come back, when I know this issue has been resolved.  Until then, I am branching out farther and playing with more distro's.

---

### Post by ketsugi on 2006-07-19
I've managed to isolate my problem to xcompmgr. I don't know if that'll help anyone else though.

---

### Post by memas on 2006-07-20
I also have these sudden freezes.
I was thinking that maybe the problem starts from my USB keyboard.
So are all of us here use a USB keyboard or a USB printer?

---

### Post by Tyltyl on 2006-07-20
I restored a backup prior to the freeze problem.
I will see how long it will last...

---

### Post by Jhongy on 2006-07-20
I've just read through this thread, scary stuff.... the symptoms are similar, but usage patterns vary. Perhaps there is a common hardware problem?

Has anyone tested their memory with **memtest86?** Maybe your RAM is marginal... so an upgrade or change in usage pattern that places different demands on the memory subsystem surfaces (or eliminates) the problems. 

A quick fix might be to go into the BIOS and increase **memory CAS latency**, etc (there are a few settings) up to the most relaxed settings. (e.g., change to CAS 3 instead of CAS 2 or CAS 1.5).

Of course, CPU front-side bus shouldn't be overclocked if you've having lock-ups

When I first tried linux (Mandrake) a few years ago, I was turned away because my memory was overclocked and I was seeing lockups and filesystem corruption. This was after having run WinXP for a long time, and it being solid as a rock. Linux just placed different demands on the memory.

Just an idea.... and it would be consistent with observations regarding changing video drivers, disabling AGP, and ACPI standby impacting the problem.

---

### Post by Tyltyl on 2006-07-20
> **Jhongy said:**
> I've just read through this thread, scary stuff.... the symptoms are similar, but usage patterns vary. Perhaps there is a common hardware problem?

Has anyone tested their memory with **memtest86?** Maybe your RAM is marginal... so an upgrade or change in usage pattern that places different demands on the memory subsystem surfaces (or eliminates) the problems.

memtest86 stopped working for some reason, but if I use it from another source other than Grub it works and shows no errors.

Windows works like a charm though, I don't think it's a RAM problem, because we would all have a broken RAM.

> **Jhongy said:**
> 
A quick fix might be to go into the BIOS and increase **memory CAS latency**, etc (there are a few settings) up to the most relaxed settings. (e.g., change to CAS 3 instead of CAS 2 or CAS 1.5).

Of course, CPU front-side bus shouldn't be overclocked if you've having lock-ups

When I first tried linux (Mandrake) a few years ago, I was turned away because my memory was overclocked and I was seeing lockups and filesystem corruption. This was after having run WinXP for a long time, and it being solid as a rock. Linux just placed different demands on the memory.

Any reason why this problem only appeared recently and not before, especially to so many people?

---

### Post by Jhongy on 2006-07-20
Perhaps a new package is placing different demands on the RAM? Maybe because it's summer.. and hotter(?!)

The other thing that jumped to mind is a corrupted package or download somewhere that went undiagnosed. 

I suppose the latter problem could also be a symptom of the first... meaning that even backing off on the memory timings wouldn't resolve the issues.

Anyway, it's an easy thing to test... hopping into the BIOS and backing off on memory timings only takes a few seconds.

---

### Post by Tyltyl on 2006-07-20
> **Jhongy said:**
> Perhaps a new package is placing different demands on the RAM? Maybe because it's summer.. and hotter(?!)

The other thing that jumped to mind is a corrupted package or download somewhere that went undiagnosed. 

I suppose the latter problem could also be a symptom of the first... meaning that even backing off on the memory timings wouldn't resolve the issues.

Anyway, it's an easy thing to test... hopping into the BIOS and backing off on memory timings only takes a few seconds.

A corrupted package is also my idea, it probably has a conflict with some hardware. I now restored an old backup, so I will check.

If it still doesn't work I will try the RAM thing because I'm a bit scared about BIOS changes...bad experiences ;)

---

### Post by meep on 2006-07-20
Just wanted to add that I'm having this issue too.  I've been watching this thread the past couple of weeks, while rebooting about twice a day.  Yesterday, I let some updates install.  Now it's locking up every 20-30 minutes.  Second, when I leave the room and return much later, the system's sitting at a login prompt.  
I thought it was rebooting on it's own, but as I'm working on another computer on a kvm switch, I see that it's just crashing down to login prompt.  It's not going through a full reboot. 
Also, and I think I'm imagining it still, but I can reproduce the lock almost everytime I start typing.  If I'm replying to an email, and I type quickly and suddenly, it'll lock.  If I type the first few letters slowly and wait, it won't.  If I'm IMing someone, and I type quickly, it'll lock.  If I slowdown and wait, it won't.  If I type a search term in Firefox searchbox on toolbar, it'll lock.. unless I type slow and wait.
It doesn't explain what's going on when the computer is idle, but maybe it helps someone?  I was finally able to send an email by not starting the email fast.

The updates installed through the update-manager yesterday really made it tons worse.

---

### Post by dspivey on 2006-07-20
Still having the crashes here, too.

To answer some of the recent questions:

My keyboard is not USB, but my mouse is.

I dualboot with Fedora Core 5, and don't have these issues at all.

My frequency of crashes hasn't increased or decreased with updates.

---

### Post by petoro on 2006-07-20
I write only to say that I'm also having this freezing problem.

I use Ubuntu intensively since 2005, but the freezes have started to occur only 3 days ago.

I have a 4.5 years old notebook with this graphics card:

Radeon Mobility M6 LY

I have disconnected an attached USB flash drive to see if it is the cause of the hangings.


Petoro

---

### Post by meep on 2006-07-20
My screensaver/nvidia combo was causing the idle crashes.  When I tried to turnoff screensaver options, the preferences window wouldn't load.  It would crash when I tried to enter the options window, sending me back to login screen. 

I changed the xorg.conf to use nv for now.  I can adjust screensaver options again, so I doubt it'll crash as much now. :)  We'll see...

---

### Post by Tyltyl on 2006-07-20
I'm using a 1 month old (or so) backup and it seems more stable.
I only had a freeze, but while using the screensaver and is an issue that I occasionally had before. Still no freeze while actively using the PC or surfing.

---

### Post by Noxide on 2006-07-20
I was having these crashed for quite some time. After anything between 1 hour and 1 day suddenly the mouse cursor would go crazy for several seconds and the system would start working extremely slow, until I had to press the power button. This happened on both Gnome (ubuntu) and KDE (kubuntu).
Two days ago I replaced the 386 kernel with 686, and didn't have a crash since then. :-D 

Noxide

Edit: Well, seems it wasn't the solution. Crashes are now much less frequent, but still the same. ](*,)

---

### Post by alanphil on 2006-07-20
I've been researching other linux distros for my Thinkpad X30, since this freezing issue with Ubuntu. I've tried several distros on this machine and had issues with suspend not working, or wireless not working. ](*,)  

In the process I've been reading forums for Debian, Zenwalk, Arch Linux, and many other distros over the last few days. What I'm seeing is that this freezing problem is appearing in many distros. I don't see that anyone has it figured out yet, but the problem is more wide-spread than Ubuntu.

Seems to be a major issue on IBM Thinkpads, and may be related to recent kernel and/or Xorg or the interaction of these two. Lots of ideas being tossed out about problems with power management (ACPI vs APM), but no hard evidence that this is the issue. I'm going to try Ubuntu Breezy (with no kernel updates!) for awhile and see if I have better luck. 

In summary, a different distro doesn't seem the answer to this problem. A better approach may be to move to an old distro until this problem is solved.

---

### Post by shakumafu on 2006-07-20
Deciding not to read all 21 pages, the very likely problem could be the ati drivers. I had the ati driver in use on my laptop and it kept freezing randomly. I changed it back to vesa and it hasnt frozen since. I have had 2 desktops with nvidia cards (one integrated and one not) and have their proper drivers running and have never frozen.

I have also had bad memory(from ebay ](*,) ) causing system crashes so try running memtest86 just in case

---

### Post by Tyltyl on 2006-07-20
Still using an old backup with kernel 2.6.15-25-686 and no freeze.

EDIT: Talked too soon...

---

### Post by dspivey on 2006-07-20
thanks, shakumafu, but ati drivers aren't the problem.  several people on this post aren't using ati or nvidia drivers.  i'm sure some people are having the standard ati-related crashes, but that's not the primary cause behind all the posts in this thread.

---

### Post by petoro on 2006-07-20
Do you have an USB flash drive?

I had one attached.  This was my second USB device, the first is a USB mouse that I still use.

Since I removed the USB flash drive there haven't been any crashes.


Petoro

---

### Post by entangled on 2006-07-20
It's affecting me too, since the kernel before 26. 
My theory is that networking is unstable. I can freeze my system almost for sure by switching between wired and wireless interfaces, both of which work. Also I find that the DHCP address is just *lost* after a while and I have to ifdown-up to get it back.

On the other hand the freezes tend to occur when the system is left alone for a while and I've just found that I have power management set to sleep in 30 mins, so perhaps its that?

---

### Post by whatever69 on 2006-07-20
I think it's the kernel.  Can people post their kernels they're running?

I'm running:

**Linux ubuntuserver 2.6.15-25-k7 #1 SMP PREEMPT Wed Jun 14 11:43:20 UTC 2006 i686 GNU/Linux**

I was running 2.6.15-26-k7 but went back to 2.6.15-25-k7.  The "26" was crashing almost within 2 minutes of logging into Gnome.  No matter what I did.  When I changed back to 25, it didn't crash immediately.  I'm going to monitor this.

Hmm..this sort of complete crash just started happening recently.  I had been running Ubuntu since Breezy, and then upgraded Dapper with no problems.

I run a lot of torrents and LAN file sharing and like a lot of people, when left alone and there's lots of activity, Ubuntu crashes.  

I doubt it's hardware.  My system hasn't changed and I have top quality components.  No cheap knock offs.

So umm...who wants to sift through the changlogs for this kernel ](*,) 

[http://www.kernel.org/pub/linux/kernel/v2.6/]("http://www.kernel.org/pub/linux/kernel/v2.6/")

---

### Post by globetrotters1 on 2006-07-20
I updated from Breezy 5.10 to Dapper 6.06 yesterday. Update was a snap and worked perfectly.

I had system freezes in Breezy at the moment when XScreensaver got active. I have to say that I use the 32-bit version on a 64-bit AMD Opteron dual CPU system (because the graphics card driver is missing in 64-bit). Now I have two different screensaver menu points in Dapper-System-Preferences and the same behaviour. It freezes my system totally. Everything else is working fine until now.

By the way: I installed Breezy 64-bit AMD and that works just fine, also the screensavers. So, it might be an incompatibility with the 64/32-bits biting each other... :rolleyes: 

But I sometimes come back after more than 30 minutes and my screen got blank, but is active and the system is frozen. Only sometimes, not always. So now I switched the power settings to never switch off the screen and will see if it helps.

I'll check this thread now daily... and hope that someone can figure out what it really is

---

### Post by Tyltyl on 2006-07-21
I tried a few fresh reinstall of Dapper and it froze in a matter of minutes or even seconds. Strangely they were more frequent than with my "old" system.
I'm not excluding a hardware problem now...but strangely Windows works fine. I don't understand.

---

### Post by ketsugi on 2006-07-21
My kernel is **Linux Asahara 2.6.15-26-686 #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006 i686 GNU/Linux**

---

### Post by Tyltyl on 2006-07-21
I used both 2.6.15-25-686 and 2.5.15-23-686 and I'm having the same problem.
Same kernels as some time ago but without this problem. I just made another RAM test and no errors, but I can't find that CAS option in my BIOS...

---

### Post by Gus Tarballs on 2006-07-21
> **dspivey said:**
> thanks, shakumafu, but ati drivers aren't the problem.  several people on this post aren't using ati or nvidia drivers.  i'm sure some people are having the standard ati-related crashes, but that's not the primary cause behind all the posts in this thread.

As said before, there are probably many different sources for the problems here. 
In my case (Thinkpad X24) the ati drivers seem to be the source for all the freezes I experienced. 
Someone mentioned that switching back to vesa drivers might help. So I tried that for a couple of days and had not one single freeze. 
After the latest xorg and kernel updates I decided to give the ati drivers another try (video playback perfomance with vesa drivers is terrible). 
In the two days since I switched back to ati I had no freezes :D 
It may not solve all the freezing problems mentioned here but maybe updating and/or trying the vesa drives will work for some people.

---

### Post by viz_e on 2006-07-21
I am the guy with the memory leak (Xorg eating 1.5Gb+1Gb memory in ~4 hours). I started a deeper inspection and Xorg starts consuming memory as soon as thunderbird and/or firefox are open.

Xorg passes from an usage of 35-40Mb with some programs open to about 120 Mb by opening thunderbird. After that, it seems that memory usage starts increasing.

Anyone having this behavior? What is your memory usage near crashes? (even for those, that do not relate the problem to Xorg or Firefox...)

---

### Post by whatever69 on 2006-07-21
It crashed after switching to a different kernel, but not a complete computer freeze!

@ketsugi:  Hmmm....pretty much the same kernel as me.

@viz_e:  I have checked the memory leak theory yet.

Normally, the network card just dies and I can't even SSH into the machine.  This time, I was able to so.  So I decided to start vncserver and log in.  The default Gnome desktop did not load.  Just a grey backround.  The mouse cursor was an X.  That's it.  No icons, no nothing.

So I closed that.  Killed X.  and I restarted and everything is working again.  It's been close to 12 hours uptime now.

Btw, I also installed KDE.  It ran.  But when I tried to remotely  control the :0 desktop through VNC, it froze all of KDE when the "accept or deny" prompt came up.

So to reaffirm what some people are saying, it might be several factors.  Perhaps kernel + X are the cause.  I'm just guessing at this moment.

Still going to watch this thread for more clues...:-k

---

### Post by Tyltyl on 2006-07-21
I also think is that we have different cases with the same symptoms.
Some have solved by using the Vesa drivers, some with another kernel etc.
I've tried everything. Unplugged the audio card, the HD, tested the RAM, disabled the USB, reinstalled with old kernels, reconfigured Xorg, used XGL.
Nothing!

What is it then???

EDIT: By looking at the xorg log I noticed some errors with /dev/wacom

```

(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument

```

/dev/wacom is indeed missing. Could it be the cause of the freeze?

EDIT: fixed by removing some lines from xorg.conf.

---

### Post by Tyltyl on 2006-07-21
It still doesn't work with USB disabled and with the wacom error fixed.

I completely lost faith and control over it :-/
There's no sign of errors in the logs, I tried every piece of hardware, with fresh reinstall and backup with different kernels.

Heeeeelllppppp!!!

---

### Post by Pawel on 2006-07-22
Hello!

I know how to reproduce the bug! It works usually few minutes after system run (Ubuntu should working few minutes).

1. Open firefox and go to [www.avast.com](www.avast.com)
2. Wait until page loading will be finished.
3. Try to open menus, browse them, and then try to click eg. programs, updates or sth. else.
=====================

Yesterday on my Ubuntu:
-> desktop resolution goes smaller then my default //1024x768// - it was strange, it wasn't normal. My monitor OSD showed refresh rate by 78 Hz...
Picture on monitor was waveing

-> When i go to console (eg. ctrl+alt+F2) - and back to desktop: everything is fine!

-> At the same run, when i explore some phothos by firefox, picture on monitor agains go to strange resolution at 78 Hz, but picture was like...colour criss-cross or.. - like tV no synchro. Cursor looks like white square. Feew seconds later only reset help...

-> Next run... - few minutes later my monitor goes off (also when firefox was run). I try to switch off and on it, and then it's green led was blinking.
Then i switch into console and back again to Desktop mode, and it works.

-> System parameters at that time was in norm.

I hope that will be useful.

Best regards
Pawel

P.S. If you have a direct link to bug tracking system, where i can report this observations - please post it. Sorry - i don't have enough time today. :(

P.S.2 I'm looking through log files. Here's sth interesting:
> (EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(EE) RADEON(0): RADEONWaitForIdleCP: CP idle -1022
(EE) RADEON(0): Idle timed out, resetting engine...
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()


P.S.3. Today my monitor shows "sync. out of range" when Desktop goes down, and i try swith to console. Only reset helps...

Best regards
Pawel

---

### Post by Gus Tarballs on 2006-07-22
> **Gus Tarballs said:**
> As said before, there are probably many different sources for the problems here. 
In my case (Thinkpad X24) the ati drivers seem to be the source for all the freezes I experienced. 
Someone mentioned that switching back to vesa drivers might help. So I tried that for a couple of days and had not one single freeze. 
After the latest xorg and kernel updates I decided to give the ati drivers another try (video playback perfomance with vesa drivers is terrible). 
In the two days since I switched back to ati I had no freezes :D 
It may not solve all the freezing problems mentioned here but maybe updating and/or trying the vesa drives will work for some people.

The freezes started again ](*,) . I had to switch back to vesa. I noticed that this particular freeze happens when there is a lot of activity on the screen (like drawing a new window or dragging icons around). If using vesa-drivers is the only way to avoid the freezes I will have a big problem. Playing videos fullscreen leads to dropped frames because the vesa-driver is so slow :( 

Since it is most likely a driver problem I think the window manager should not matter but I wonder if people that use kde have the same problems.

---

### Post by Tyltyl on 2006-07-22
This morning I did an update and downloaded a new kernel and a xorg update.
Until now no freeze, I even watched 2 whole movies without a freeze (Return of the King is even a bit long).
Encouraging...

EDIT: Why do I always speak too soon? It just froze again. It sustained 6+ hours of DVD movies and switching between desktops while surfing, and it crashed now with only 1 app open (XPN). I just pressed CTRL + 2 to switch to desktop 2 and it froze up.

---

### Post by Efrain Valles on 2006-07-22
WHEN I first installed UBUNTU (hoary) I had all sorts of freezes... it turned out to be my little memory running out (256 m no swap) I set up a swap file and things moved along from there... I am using the same machine with dapper now and I have the SCREENSHOT-like freeze... I have an ati card and I have a swap so... it can't be memory... (at least for me) I changed my XORG.CONF  in the ati driver I changed to radeon and it seems to have done the trick

from

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```



to

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
EndSection
```

it worked for me... see it helps you...:D

EDIT: 1 day and a half was all it took ... it froze again ](*,) 

is anyone giving up on this one...???

---

### Post by Tyltyl on 2006-07-23
I would try to change the drivers but I know the standard vesa drivers cause problems even with my live cd.

---

### Post by meep on 2006-07-24
switching video driver back to default "nv" and setting up my swap space did the trick for me, so far.   it hasn't frozen or crashed since friday.  of course, now that i say that, i know i'm asking for trouble.

still, i'm noticing most problems when typing.  while typing this message, it just stops briefly and i think it's locked, but it comes back... as an example, if i press my left arrow to go back through this message, letter by letter, it'll stop briefly after 30 characters or so, then continue on, then stop, then continue, etc.  it's the same delay i'm noticing when typing and before last friday, it's when my freezes occurred.

---

### Post by Tyltyl on 2006-07-24
I added some voices in xorg.conf

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R300 ND [Radeon 9700 Pro]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option 		"UseFBDev" "true"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "off"

And now it hasn't frozen so much, only once while I was playing Enemy Territory, but it could be blamed to anything. While on the desktop it didn't happen anymore.

---

### Post by Tyltyl on 2006-07-24
I only had another freeze while playing Enemy Territory, for the rest it's all quiet apart from frequent Firefox crashes...which is a lot better than a total freeze!
The way it fixed is a mystery, maybe that line in Xorg.conf.

---

### Post by viz_e on 2006-07-25
> **meep said:**
> switching video driver back to default "nv" and setting up my swap space did the trick for me, so far.   it hasn't frozen or crashed since friday.  of course, now that i say that, i know i'm asking for trouble.

still, i'm noticing most problems when typing.  while typing this message, it just stops briefly and i think it's locked, but it comes back... as an example, if i press my left arrow to go back through this message, letter by letter, it'll stop briefly after 30 characters or so, then continue on, then stop, then continue, etc.  it's the same delay i'm noticing when typing and before last friday, it's when my freezes occurred.

I have also that problem while typing. I noticed that when this happens, Xorg jumps to the next "memory level". So, I am afraid that if you now wait long enough, also your swap partition will be filled and... kaboom...

I upgraded the ati drivers to the last release and now the memory leak seems to be even faster... ](*,) ](*,) ](*,)

EDIT: I switched from firefox+thunderbird to galeon+kmail. My Xorg memory usage seems to be constant (!) and I don't have those firefox-like "partial freezes" in galeon (!).

EDIT2: Well, the memory leak is still present, but at this speed rate I can at least use the laptop for the whole day without freezes (Xorg: 165Mb RAM + 203Mb Virt in about 3 hours, whereas usually my 2.5Gb of memory (1.5Gb RAM and 1Gb swap) are sucked in 4 hours.)
Summing up: it seems that firefox and thunderbird specially exploit the potential xorg bug.

---

### Post by Valavien on 2006-07-25
What kernel are you using ie 386, K7, 686 etc.

I have found since Dapper I can't use the K7 anymore as the system completely freezes.  Switch back to 386 and no problems at all.  I still would like to use the K7 though :confused:

---

### Post by eXecu7or on 2006-07-25
Another one here... Mine freezes when logging out of a session. As soon as I select log out, the system goes to gdm, but the login screen appears corrupted. There is however, a small color rectangle where the login text box should be. I've tried typing in blank a user, but as soon as I hit enter after the password. The system freezes (the login sound enters a "hiccup" loop).

In an other instance, the system freezes in the XGL session that runs on top of gnome (as set-up using tutorials), when maximizing and minimizing windows very fast several times... (as xgl is not stable, I think this should not count).

My specs: Pentium D805 2.6GHZ, 1GB DDR2, ATI X800 XL using the latest driver. Also the latest kernel from synaptic.

I'll keep an eye out for some kind of a memory leak in System Monitor (in one instance, I saw XGL's proccess eating around 90MB...)

---

### Post by mozz on 2006-07-25
+1

Freezes, boot errors, strange stuff going on with LVM, update problems, etc etc... a never ending story

I installed Dapper 6 (!!) times from scratch on a standard K7S5A AMD box and I got new errors every boot-up. Smells more like beta than stable...

Dapper really made me switch. From Ubuntu to Debian.

---

### Post by jrjr on 2006-07-25
So is Debian any better?
I've had it with Ubuntu

---

### Post by Efrain Valles on 2006-07-25
> **jrjr said:**
> So is Debian any better?
I've had it with Ubuntu

the GUI is the same... the Ubuntu people try to make it friendlier and more like your everyday computer... if you should install debian you will see the resemblance... the new debian  will launch will be released in december with 64 bit support...

I still use Ubuntu... and running the vesa drivers keep me from crashing now...

---

### Post by attackedbymars on 2006-07-25
Well I was having freezing issues as well and decided to start removing peripherals one by one, luckily for me it was the first one that I pulled that seem to help. Unluckily for me it was my 250GB SATA Western Digital Drive that I put in an external USB casing. Hope this helps!

Here is some basic information:
2.6.15-26-amd64-generic, xorg, nvidia driver 1.0.8.x

---

### Post by viz_e on 2006-07-26
I post the measurements of Xorg's memory usage, with 10min delay and using: kmail, galeon, gaim, kile, kghostview, yakuake, knotes, superkaramba, akregator on a IBM thinkpad T43p (1.5Gb RAM and 1Gb swap) with dualhead setup and latest ATI drivers.

```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5205 root      15   0 80132  39m 7812 S  3.9  2.6   0:09.57 Xorg
 5205 root      15   0 96204  56m  13m S  1.3  3.7   0:17.61 Xorg
 5205 root      16   0  158m 121m 9700 S  3.6  8.0   0:39.09 Xorg
 5205 root      15   0  116m  79m 9656 S  2.4  5.2   0:53.73 Xorg
 5205 root      15   0  136m  99m 9668 S  2.9  6.6   1:11.30 Xorg
 5205 root      15   0  119m  82m 8900 S  1.3  5.4   1:19.04 Xorg
 5205 root      16   0  119m  82m 8972 S  0.6  5.4   1:22.64 Xorg
 5205 root      16   0  120m  83m 9704 R  0.9  5.5   1:28.25 Xorg
 5205 root      16   0  114m  77m 8972 S  1.2  5.1   1:35.73 Xorg
 5205 root      15   0  119m  82m 8972 S  0.9  5.4   1:41.11 Xorg
 5205 root      15   0  114m  77m 8972 S  1.8  5.1   1:52.19 Xorg
 5205 root      16   0  158m 120m 9.8m R  3.5  8.0   2:13.22 Xorg
 5205 root      15   0  206m 168m  10m S  9.9 11.1   3:12.55 Xorg
 5205 root      16   0  254m 216m 9.8m R 10.2 14.3   4:13.90 Xorg
 5205 root      15   0  275m 238m 9.9m S  5.0 15.7   4:43.83 Xorg
 5205 root      15   0  252m 214m 9068 S  1.1 14.2   4:50.47 Xorg
 5205 root      15   0  243m 206m 9068 S  1.4 13.6   4:58.98 Xorg
 5205 root      16   0  243m 206m 9068 S  0.8 13.6   5:03.55 Xorg
 5205 root      15   0  244m 206m 9868 S 13.2 13.6   6:22.48 Xorg
 5205 root      15   0  244m 206m 9868 S 11.9 13.6   7:34.02 Xorg
 5205 root      16   0  244m 206m 9868 S 12.5 13.6   8:48.85 Xorg
 5205 root      16   0  244m 207m 9900 R 12.3 13.6  10:02.58 Xorg
 5205 root      15   0  244m 207m 9900 S 12.6 13.6  11:18.35 Xorg
 5205 root      16   0  244m 207m 9900 R  7.2 13.6  12:01.66 Xorg
 5205 root      16   0  244m 207m 9900 R 12.1 13.6  13:14.12 Xorg
 5205 root      15   0  244m 207m 9900 S 12.8 13.6  14:31.06 Xorg
 5205 root      15   0  247m 209m 9900 S 12.8 13.8  15:48.16 Xorg
 5205 root      16   0  258m 220m 9900 S 12.8 14.6  17:04.90 Xorg
 5205 root      15   0  270m 232m 9900 S 12.8 15.3  18:21.95 Xorg
 5205 root      15   0  280m 242m 9900 S 12.7 16.0  19:37.90 Xorg
 5205 root      15   0  300m 263m 9900 S 10.4 17.4  20:40.32 Xorg
 5205 root      15   0  359m 321m 9900 S  4.3 21.2  21:06.40 Xorg
 5205 root      15   0  380m 342m 9900 S  2.7 22.6  21:22.39 Xorg
 5205 root      15   0  393m 355m  10m S  1.8 23.4  21:33.22 Xorg
 5205 root      15   0  405m 367m  10m S  2.2 24.2  21:46.42 Xorg
 5205 root      16   0  424m 386m  10m R  3.2 25.5  22:05.57 Xorg
 5205 root      16   0  445m 408m  10m S  4.0 26.9  22:29.64 Xorg
 5205 root      15   0  463m 426m  10m S  5.1 28.1  22:59.99 Xorg
 5205 root      15   0  477m 439m  10m S  3.7 29.0  23:21.96 Xorg
 5205 root      15   0  495m 458m  10m S  2.8 30.2  23:38.59 Xorg
 5205 root      16   0  540m 502m  10m R  5.7 33.1  24:12.88 Xorg
 5205 root      15   0  575m 537m  10m S  7.3 35.4  24:56.91 Xorg
 5205 root      15   0  533m 496m 9452 S  4.6 32.7  25:24.56 Xorg
 5205 root      15   0  532m 495m 9452 S  2.9 32.7  25:41.78 Xorg
 5205 root      16   0  521m 483m 9456 R  3.3 31.9  25:44.00 Xorg
 5205 root      16   0  521m 483m 9456 R  0.0 31.9  25:44.00 Xorg

```

The memory usage keeps growing (not monotonically) and does not explode really fast. Probably tomorrow I'try the same experiment with thunderbird and firefox to show the difference.

Do anybody have comments on this data?

P.S. In the last jump from 537m to 496m, I have just closed galeon...

---

### Post by Pawel on 2006-07-26
I think there is a problem with kernel...

When i used breezy'e kernel (2.6.12.x) - dapper didn't freeze!

You also should try this.


Tomorrow i'm going to compile my own kernel. Best regards

Pawel

---

### Post by viz_e on 2006-07-27
> **Pawel said:**
> I think there is a problem with kernel...

When i used breezy'e kernel (2.6.12.x) - dapper didn't freeze!

You also should try this.


What is the fastest way to install breezy's kernel?

---

### Post by viz_e on 2006-07-27
Here comes the memory test while using firefox instead of galeon and thunderbird instead of kmail.

```

5248 root      15   0 80416  39m 7840 S  0.0  2.6   0:08.98 Xorg
 5248 root      16   0  124m  86m 9384 S  2.7  5.7   0:25.43 Xorg
 5248 root      15   0  165m 127m 9808 S  3.6  8.4   0:47.11 Xorg
 5248 root      15   0  306m 268m  10m S  5.3 17.7   1:18.74 Xorg
 5248 root      15   0  444m 405m  10m S  3.8 26.8   1:41.29 Xorg
 5248 root      15   0  571m 533m  10m S  0.8 35.1   1:45.86 Xorg
 5248 root      15   0  690m 652m  10m S  1.4 43.0   1:54.28 Xorg

```

The delay is 10 minutes as before, so the memory leak is much more evident in this case. Moreover, I had no time to really use the other programs listed in my previous thread...

Here is the output of xrestop:
```
xrestop - Display: localhost:1
          Monitoring 32 clients. XErrors: 0
          Pixmaps:  302483K total, Other:     141K total, All:  302624K total

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
3c00000   538  154    1 2634   76   257689K     19K 257708K   ?   <unknown>
2c00000    30  136    1   97   31     9296K      5K   9301K   ?   <unknown>
2e00000   109  152    1  301   79     7488K      8K   7497K   ?   Ubuntu Forums - Edit Post
2800000    93   14    3  307  192     6175K     10K   6186K   ?   superkaramba
1600000    68  124    3   63  123     5192K     10K   5202K   ?   KDE Desktop
1800000    35    9    0   27   74     5138K      2K   5140K   ?   <unknown>
3000000    67   90    3  125  102     4852K      9K   4861K   ?   Yakuake
2600000    53  108    3   61   50     4127K      7K   4135K   ?   <unknown>
1a00000   102  126    3  258  248      807K     14K    821K   ?   kicker
1c00000    82  124    0  156  135      697K      7K    705K   ?   <unknown>
3a00000    12    2    1    2   30      396K      2K    398K   ?   <unknown>
2a00000   118   16    3   51   67      194K      7K    201K   ?   17.10 - 20.10.2006
1400000    43  125    1   79  322      163K     12K    175K   ?   <unknown>
1200000    42  125    0  121  343      141K     11K    153K   ?   kwin
0c00000    16  124    1   14   27       62K      4K     67K   ?   <unknown>
0e00000    10    6    0   21   38       22K      1K     24K   ?   <unknown>
2400000     7    8    0   16   22       18K    888B     19K   ?   <unknown>
3800000    10    5    0   27    7       15K    528B     15K   ?   <unknown>
3400000     6    9    0    6    9        3K    576B      4K   ?   <unknown>
0200000     0    2    1    0    0        0B      1K      1K   ?   <unknown>
1e00000     6    2    0    0   24        0B    768B    768B  5442 khotkeys
2200000     6    2    0    0   20        0B    672B    672B   ?   <unknown>
0800000     3    2    0    0    6        0B    264B    264B   ?   <unknown>
3600000     2    2    0    0    6        0B    240B    240B   ?   <unknown>
1000000     2    2    0    0    6        0B    240B    240B   ?   <unknown>
0600000     1    0    0    1    3        4B     96B    100B   ?   <unknown>
3e00000     1    2    0    0    0        0B     72B     72B   ?   <unknown>
2000000     1    2    0    0    0        0B     72B     72B   ?   xrestop
0a00000     1    2    0    0    0        0B     72B     72B   ?   <unknown>
4000000     0    2    0    0    0        0B     48B     48B   ?   <unknown>
3200000     0    2    0    0    0        0B     48B     48B   ?   <unknown>
0400000     0    2    0    0    0        0B     48B     48B   ?   <unknown>
```

---

### Post by tabinin on 2006-07-27
I tried a few things in this thread and so far, the only thing working for me was to switch from the nvidia driver to nv using the dpkg-reconfigure xserver-xorg routine.  This has taken me from hourly freezes to none in the last 6 hours or so.  The only drawback has been loosing my tv-out set up, but you can send a signal to your TV if your xorg is frozen solid.

Thank you to everyone who has added to this thread!

---

### Post by meep on 2006-07-30
Yes, I've been freeze-free for over a week now too.  I only switched to nv driver and activated swap.  I miss Google Earth. :(  But this keeps me from reinstalling ubuntu (or a different distrib) from scratch.

---

### Post by meep on 2006-07-30
well, my computer was super-slow after some long and busy firefox sessions, so i rebooted.  after reboot, it locked within 5 minutes in the middle of a gaim conversation.  :(

---

### Post by farno on 2006-07-30
i don't speak english very well, so for me it's hard to read all this thread.
i would like to know if there is a solution to this problem:
often dapper crashes, the mouse is blocked, i can't open the emergency terminal. i can only push on the power button and turn off the computer.
this appens in different situation, also when i use few programm.
i don't know which informations could be usefull. my coputer is an acer aspire 3023, with an ati video card, configured with fglrx driver (as suggested on italian wiki).
i don't know what to do.
with breezy i didn't have this problem.
please help me!
p.s.: somebody suggest to don't use fglrx driver and to use vesa, but i need 3d acceleration to watch dvd...

---

### Post by vampiric_blade on 2006-07-30
I finally nailed down my lockups to faulty ram. I have had my dapper box up for 9 days now w/no probs.

---

### Post by eeefresh on 2006-07-31
For what its worth, I am having the same problem.  I've got a Sony Vaio laptop with an ATI 9000 Mobile card, 1.0 gHz, 256 MB of RAM.  Mine locks up about once every hour, and so far it seems to only happen when I am using Firefox, but then again I use it 90% of the time I am on the laptop.

Mine doesn't hang, it freezes completely.  The mouse arrow won't move at all, and if I leave it on, its still locked when I return later.  

Hopefully the developers can fix this.  I just started with Linux and was really getting into Ubuntu, but lockups can be a deal-breaker.

---

### Post by farno on 2006-07-31
i'm trying to use the driver from ati.com instead of the driver fglrx in repositories.
at the moment i didn't have crashes

---

### Post by Pawel on 2006-08-01
> **viz_e said:**
> What is the fastest way to install breezy's kernel?

try to use first dapper kernel: 2.6.15.23

Just edit your /boot/grub/menu.lst
----------------------------------

Few observations from me and my brother:

1. Dapper doesn't freeze on his first kernel (2.6.15-23)
2. Dapper doesn't freeze on the newest kernel (2.6.17.7) with DISABLED /dev/agpgart module !
--------

Today i will wrote some other infos on Launchpad.

best Regards
Pawel

---

### Post by Panik on 2006-08-01
Dapper has been running very stable for me (about 3 weeks without reboot) up until a few days ago.  I had a power outage, and then it started hanging and needed a hard reboot.  It would continue to hang within a few minutes of boot.  

I thought maybe the power outage harmed some hardware, but after digging a bit, the outage caused my cmos to reduce my cpu clock to a "safe" level.  After returning it to standard rates, my system is stable again (hopefully).  It has been running 14 hrs with no problem.

For the record, I am running nvidia drivers w/KDE.

Linux 2.6.15-26-k7 #1 SMP PREEMPT Mon Jul 17 20:36:04 UTC 2006 i686 GNU/Linux

---

### Post by dmizer on 2006-08-01
> **meep said:**
> well, my computer was super-slow after some long and busy firefox sessions, so i rebooted.  after reboot, it locked within 5 minutes in the middle of a gaim conversation.  :(
upgrade to gaim2 beta3.  gaim has a frekish quirk where it spawns mutiple instances of itself after a while.

i think this is only the case if you don't use tabbed conversations (ie, all conversations are in different windows).  but i do know that there is a problem with the gaim that shipps with linux.  same happened on breezy, dapper and fedora core.  gaim2 beta3 is awesome.

---

### Post by go2dell on 2006-08-01
> **Valavien said:**
> What kernel are you using ie 386, K7, 686 etc.

I have found since Dapper I can't use the K7 anymore as the system completely freezes.  Switch back to 386 and no problems at all.  I still would like to use the K7 though :confused:

Just wanted to chime in that I have found exactly the same thing.  The nvidia driver also causes lockups, but I can almost predict these.  The random kernel lockups (most commonly "soft lockup detected on CPU#0") occur under the K7 kernel but appear to be completely eliminated under the 386 kernel.

---

### Post by madchicken on 2006-08-02
For those like me are using ati/radeon driver (the open source one) try not using the default ubuntu theme (borders, controls and icons): there's a bug in the ati driver with the new cairo causing some error during rendering of the UI with the ubuntu theme...I suspect this bug is also causing SOME of our freezes.
I changed my theme and I didn't have a crash in the last two days, that is for me...incredible.
I'll try my system for some day, and if I don't have crashes I'll report in launchpad.
You can find the bug I'm talking about [here]("https://launchpad.net/bugs/34435").

---

### Post by madchicken on 2006-08-02
For those like me are using ati/radeon driver (the open source one) try not using the default ubuntu theme (borders, controls and icons): there's a bug in the ati driver with the new cairo causing some error during rendering of the UI with the ubuntu theme...I suspect this bug is also causing SOME of our freezes.
I changed my theme and I didn't have a crash in the last two days, that is for me...incredible.
I'll try my system for some day, and if I don't have crashes I'll report in launchpad.
You can find the bug I'm talking about [here]("https://launchpad.net/bugs/34435").

---

### Post by viz_e on 2006-08-02
> **madchicken said:**
> For those like me are using ati/radeon driver (the open source one) try not using the default ubuntu theme (borders, controls and icons): there's a bug in the ati driver

Is this true only for the open source ati driver or you simply don't know if fglrx drivers are affected too?

Thank you for the advice.

---

### Post by madchicken on 2006-08-02
> **viz_e said:**
> Is this true only for the open source ati driver or you simply don't know if fglrx drivers are affected too?

Thank you for the advice.

Well, I don't know about the fglrx driver. Try reading the bug issue and the upstream at freedesktop (in the last comment Mark Shuttleworth has linked it), maybe you'll find some information.

Regards,
Pierpalo

---

### Post by Oracle of Wuffing on 2006-08-03
I started having the problem a day or two ago- everything's locked up, can't use mouse, can't use keyboard, so I have to power button it.  I've got an ATI All-in-Wonder 9800, AMD Sempron 3300 processor, and Asus K8V-X motherboard.

This last incident, I was running Puzzle Pirates (Java-based game, launched from FireFox but FireFox was closed at the moment), GAIM, and XChat.  I'm going to try switching to the VESA drivers and upgrading to the GAIM beta, and I'll jump back if I get another freezing.

---

### Post by vampiric_blade on 2006-08-04
I m starting to think that my lockups have smething to do with firefox.  I had a 9 day run with no lockups, but had 2 in the past 2 days.  Both times I noticed that I had firefox minimized to the taskbar.  I have been using konqueror for the past 20+ hrs and have had no problems.   I dont think the fglrx or nvidia binary drivers have anything to do with this, as I experienced crashes with both.  I believe firefox is the culprit here.

BTW:  I have always used the 386 kernel.

---

### Post by Oracle of Wuffing on 2006-08-04
I haven't yet switched over drivers, but I did have it freeze again three hours ago.  Xorg wasn't taking up loads of memory, and Firefox wasn't running, either (different problems, same symptom, I guess).  Just the terminal with top in it.

Edit: Wait, GDesklets, I had that running, too...

---

### Post by vampiric_blade on 2006-08-04
> **Oracle of Wuffing said:**
> I haven't yet switched over drivers, but I did have it freeze again three hours ago.  Xorg wasn't taking up loads of memory, and Firefox wasn't running, either (different problems, same symptom, I guess).  Just the terminal with top in it.

Edit: Wait, GDesklets, I had that running, too...

I make it a habit to always alt+ctrl+f1 to do a ps -A to check to see if firefox or seamonkey remain in memory when I come back to my pc.    I installed seamonkey last night to see if things would be any better, but it seems that both firefox and seamonkey don't always clear the ram they use when they exit and their processes don't always stop.  I am positive that my lockups are due to this.    With seamonkey, it is especially easy to tell.  You'll know its loaded when you run it and it asks you to choose a profile as one is already in use...   

Stop using firefox for a bit and see if that clears things up.

---

### Post by viz_e on 2006-08-05
> **vampiric_blade said:**
> 
I m starting to think that my lockups have smething to do with firefox


> **vampiric_blade said:**
> 
Stop using firefox for a bit and see if that clears things up.

Check out my posts a couple of pages ago about the memory leak using and without using firefox. It seems that firefox only make the things (really) worse, not being the original source of the problem, though.

---

### Post by mournahan on 2006-08-05
I got it I think.  I disabled ACPI in the boot up process by following [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491) and disableing it.  my boot is faster and havent froze yet(fingers crossed will reply if fails).

Update: been up now for over 24 hours with no freezing at all.  Let me know how you make out with this.  :D

---

### Post by farno on 2006-08-06
i had new crashes with the official ati driver ando also using the old kernel (2.6.15.23)
i don't know what to do...

---

### Post by sammydee on 2006-08-06
Well I had random lockups like these as well, I'm using the latest 686 kernel with the oss ATI drivers. I have also tried with the original stock kernel and fglrx drivers, same problem. I tried changing the applications I used methodically to pinpoint the source of the problem.

I've been running a while now with no lockups, after I switched from Gaim to kopete. I realised that all the crashes had happened after I'd been running gaim and had at least two conversations open, or had been running it for a long time. Now, cross fingers, the problem should hopefuly be sorted.

I just posted this in case somebody found it useful.

sam

---

### Post by farno on 2006-08-06
i don't use gaim...
i don't believe taht gaim is the problem

---

### Post by Linuturk on 2006-08-06
I've got a problem. Everytime I log out of my session, and I try to log back in, my system hangs. No hard drive activity, no nothing.

---

### Post by Oracle of Wuffing on 2006-08-07
You can take my name off of having this problem... As I've been able to recreate this event in Windows XP, which tells me that my specific problem (though not necessarily the other problems here) is something outside of Ubuntu.

---

### Post by Tyltyl on 2006-08-09
I've given up a few weeks ago, no idea what's causing the problem.
I even changed the RAM and same problem. The only thing could the graphic card, but it's strange since it has always worked.

It's totally random, I even used it 2 days without crashes, then it started crashing while playing Enemy Territory, 2-3 times then I could play the whole day. Then only FF crashed, then only the screensaver and since 2 days ago it started crashing on the desktop again.
People say that it still happens while using old kernels and drivers, so what is it? Do we have a mass hardware problem?

Or could Gnome be the cause? Or other common libraries?

---

### Post by william_nbg on 2006-08-09
Not sure either what all these crashes are about. I wrote much ealier in this thread regarding my wife's computer crashing. I'm pretty sure it was her wlan card which uses the acx driver. I even found errors regarding the wlan card and driver in the log file. I was going to go out and pick up the card which I use since I've never had problems with it, and my wife's being pretty old now. But her computer hasn't crashed for over 2 weeks, and she uses it every day for work. I'm hoping there was a fix for the problem in the last kernel upgrade. Like I said, I'm not sure, but 2 weeks is a long time without a crash.;)

---

### Post by jetblack on 2006-08-09
I had this same issue. My system ran fine for a couple of days, but then it started to hang after about an hour or so of use. When I checked /var/log/messages, I noticed it was filling with errors from my cd-rom drive.

```
hdb: command error: status=0x51 { DriveReady SeekComplete Error }
hdb: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
```

I think the drive was failing, because eventually it thrashed horribly and stopped responding entirely, devouring my ubuntu cd in the process. I've replaced the drive and the IDE cable and now my log doesn't fill up with that error and the system doesn't hang (or hasn't for 12 hours). However, on boot I do get a single instance of that error in /var/log/messages. Is that normal, or am I about to have the same thing happen?

I see that other people have had this issue at different times, for example [here](http://www.ubuntuforums.org/showthread.php?t=186017). Would I be better off not using 6.06 for now? I'm hoping that it was the drive failing that caused the errors I saw, and not vice-versa.

---

### Post by madchicken on 2006-08-09
Hi to all...googling around I found this for those using fglrx driver:

[http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29)

maybe can help someone...

---

### Post by Tyltyl on 2006-08-09
> **madchicken said:**
> Hi to all...googling around I found this for those using fglrx driver:

[http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29)

maybe can help someone...

Great, that's interesting. Too bad it doesn't explain how to change that setting since it's not in my BIOS :P

However it has worked for almost half a year and no idea why it started giving problems right now.

EDIT: Ok, fixed by changing the aperture size to 64 MB. I will see if it works.

---

### Post by jrjr on 2006-08-09
.

---

### Post by jrjr on 2006-08-09
.

---

### Post by vierranet on 2006-08-09
quick fix workaround but it works..

Using gedit from the command line:

"sudo gedit /boot/grub/menu.lst" (without quotes)

scroll down to the kernels list, on the kernel line add the following:

noapic
nolapic
pci=noacpi

the kernel line will now look something like:

title Ubuntu, kernel 2.6.12-10-k7
root (hd0,0)
kernel /vmlinuz-2.6.12-10-k7 root=/dev/sda3 ro quiet noapic nolapic pci=noacpi splash
initrd /initrd.img-2.6.12-10-k7
savedefault
boot

Then use Automaix or Synaptic to download BUM (Boot Up Manager) once done goto Services from the Administration menu to disbale the following:

acpid
apmd
powernowd
acpi-support

:cool:

---

### Post by viz_e on 2006-08-10
Is it safe to disable acpi in a laptop? Don't you loose the temperature control, CPU freqeuncy throttling, ...?

---

### Post by kwickone on 2006-08-10
Well, just thought I would chime in as well.  I am having Ubuntu freezes on an annoyingly frequent basis.  I'd say every couple hours or so, but there is not specific time interval.  I am on an HP NW8000 laptop with the fglrx drivers.  The two apps I always seem to have running are Firefox and VMWare Server.

These lock ups have only happened in the past week or so, which leads me to believe that some update is the culprit.  I seriously hope a future update fixes the issue.  Right now, I cannot work with Ubuntu as I never know when it might hang on me (e.g., during an online financial transaction, editing a long email, etc.).

And I too would like to know the ramifications of disabling acpi...

Thanks.

---

### Post by jlh on 2006-08-10
I have the same basic problem. 

I installed v.6.06 on my IBM Thinkpad T30 a couple weeks ago from a Canonical installation disk.  Randomly, the entire computer freezes, and all I can do is shut down using the on/off button.  I can't predict whether the freeze will be early in a log in session, or come after a couple hours use.  Nor have I detected any pattern to what triggers the freeze.

It's a real drag.  I've switched to Ubuntu from Suse, which I ran for nearly two years.  Never had a comparable problem.  Although there are really nice features to the Ubuntu distro, I can't see myself using it unless there's a fix in relatively short order.  

Who can do anything that really matters when the entire computer may freeze for no identifiable reason at any given moment?

---

### Post by NotAPervert on 2006-08-10
Hello all,

I have finally found some common ingredients in the crashes.

I also have been experiencing entire system freezes seemingly randomly for quite some time now.

Unlike some people in this thread, the crashes I experience do not involve cpu usage hitting 100% and the mouse cursor moving slowly.  The crashes I experience are complete hard-freezes.  No cursor movement, no nothing.

I'm running Kubuntu 6.0.6.1 on an emachines m5312 laptop which has an Ati chipset and integrated video card.

I noticed the crashes were almost always related to firefox.

While browsing fark, I surfed to foobies and from there to this website:
[(note it is NSFW!)]("http://babestatus.com/babes/Jessi-Capelli/")

This page CONSISTANTLY freezes my entire system when viewed in firefox.  It does not freeze my system when viewed in konqueror.  If the freeze in firefox does not happen the moment the page is loaded, it happens while scrolling it using the synaptic trackpad scroll.

**If I disable Load DRI from my xorg.conf, and repeat the same procedure, the page no longer causes the system to crash.**

Can someone (who isn't easily offended by NSFW websites) duplicate this behavior and confirm that unloading dri is a fix?

Good times!

---

### Post by Tyltyl on 2006-08-11
Since I changed the AGP aperture size to 64MB I haven't had a crash in 2 days, with the only exception of the screensaver which I changed.

---

### Post by sound_dezign on 2006-08-11
Just to help with some more information, my system also freezes.
I'm running ubuntu 6.06 on a Compaq Evo N410c Laptop
It has an ATI Mobility Radeon M6 16MB
1.2GHz mobile P3
512MB SDRAM
Atheros AR5212 Cardbus

I observe no CPU usage during a freeze. The screen just locks and I cannot use the mouse or keyboard. The only way to get around it is by holding the power button for a few seconds to switch the laptop off.

The problem seems to occur very randomly. It has occured when I have only been running OpenOffice Presentation (very embarressing, as it was a presentation on the power and stability of Linux!!)
It has occured with just Evolution running.
It has also occured with just firefox running.
Most of the time it happens while I have many programs running, so there is no way of telling which one could be.

ACPI is running, the CPU fan comes on regularly, the screen will switch itself off after a timeout period, etc.

I tried going to that NSFW site to see if firefox would crash my laptop, but it worked fine, scrolling and clicking on links.

Andy

---

### Post by kwickone on 2006-08-12
OK, I was able to stop my system from freezing, but it took installing a fresh Ubuntu to do it.  That tells me pretty definitively that it was a driver issue.  As many of you do I'm sure, I tended to "muck" with my system.  Trying this here, and that there.

I have not updated my drivers to fglrx yet, and until I find a need to, I will stick with the default ones.  This time I did not install Compiz and XGL.   I had previously mucked with my sound settngs...not even sure why.  I will try not to do that again :) 

So, in summary, I am happy with Ubuntu again.  :-D   At least now I can actually use it again with no freezes at all, and the apps I use the most:  VMWare Server, GAIM, OpenOffice, Firefox all work fine.

---

### Post by fatmtbiker on 2006-08-13
> **jlh said:**
> I have the same basic problem. 

I installed v.6.06 on my IBM Thinkpad T30 a couple weeks ago from a Canonical installation disk.  Randomly, the entire computer freezes, and all I can do is shut down using the on/off button.  I can't predict whether the freeze will be early in a log in session, or come after a couple hours use.  Nor have I detected any pattern to what triggers the freeze.


I have the same problem with my t30.  I can be in notepad or firefox and it just stops.  Couple of times a day.  I am going to see if the ati driver fixes the issue from easyubuntu but the site seems to be down the last few days.

---

### Post by olliek on 2006-08-14
I'm also having similar problems.  My browsers/Frostwire/terminal all crash.  Sometimes just dissappearing with a segmentation fault and sometimes dropping me back to the login screen or restarting itself.
I've found though that if I start up in recovery mode, I don't have any of these problems!
I've also had problems when installing OpenSuse and Fedora 5 but Freespire was ok.  XP also works flawlessly and my aim of weening the kids off it seems doomed to failure!

---

### Post by thebasard on 2006-08-15
My Dapper freezes also and I think it has to do with VMware Player.

Scenario 1: Running vmplayer using a virtual disk that is on an external USB hard drive.  System locks hard and the only way to recover is powering off.

Scenario 2: Running vmplayer using a virtual disk that is on the internal hard drive.  System locks hard and the only way to recover is powering off.

Seems to lock hard more frequently using the internal disk.

---

### Post by gustl87 on 2006-08-16
hi @ all ! here is the solution !

i am using an ati m6 - and i got the same strange freezes.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "ati" and if freezing continues, you might edit it as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english. #enjoy

---

### Post by sound_dezign on 2006-08-17
I believe I have found one cause of my system freezes.

I have mainly noticed the freezes while Evolution is running.

My system just froze, so I decided to be patient and waited for a while. I noticed that my system wasn't actually frozen, the mouse would move, but only very slowly. It took a while but I managed to open a terminal and run top. Evolution was using pretty much all of my RAM and SWAP space. I killed evolution and my system instantly started running properly again.

I urge people to be patient if they get this problem and try to work out if a program has stolen all of your system memory.

---

### Post by logi-linux on 2006-08-18
Hi, 

I have a similar problem. I'm using a xSeries IBM server running dapper and it's freezing a lot. What I discovered is that if you load this page in Firefox (latest version): 

[http://www.digitalhobo.com/?p=83](http://www.digitalhobo.com/?p=83)

Mine ALWAYS freezez totally and needs a hard reboot. I removed firefox and it's been going for 8 hours now without a hitch. 

It also froze doing other stuff but FireFox could have been open on those occations. 

regards, Logi

edit:
I´m using Kubuntu 6.06 - just so you know

---

### Post by viz_e on 2006-08-19
It looks like that firefox is often mentioned for these problems...
I started using galeon instead of firefox. Yet the memory leak is always present, but the fulling up of the memory is now much slower. At least I can use the laptop at work without having to reboot once or twice a day.
Am I right, if I think that galeon still has something to do with firefox (code shared or something)?

---

### Post by jrjr on 2006-08-19
.

---

### Post by ketsugi on 2006-08-20
I have no problems with that page either. I noticed my problems went away once I stopped using XGL.

---

### Post by viz_e on 2006-08-23
Upgraded xserver-xorg-core with the new (non-buggy) version and memory leak is still there... :-(

---

### Post by whatever69 on 2006-08-24
I believe I have solved my problem:

11:05:55 up 13 days, 14:24,  2 users,  load average: 0.76, 0.47, 0.32

Mine was crashing without running anything...but now I was logged into Gnome for 13 days straight.  I always believed it was a driver issues.  Here's my fix:

Section "Device"
        Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
        Driver          "via"
        BusID           "PCI:1:0:0"
        [COLOR="Red"]Option          "VBEModes" "true"[/COLOR]
EndSection

I added that one line. However, I have been consistantly updating my system, so maybe it was something else.  Either way, my system doesn't crash as before.

I also run my setup on a 1600x1200 resolution on a 20" HP L2035 monitor.

Hope that helps somebody out there!

---

### Post by Tyltyl on 2006-08-25
After I changed the AGP Aperture Size the freezes have become less frequent, but after some they started again to be annoying.
Xorg + fglrx + memory leak = bad

Why doesn't anybody fix it yet? Don't they know it yet?

---

### Post by trcook on 2006-08-25
Ok, so I was having some problems with dapper: it was freezing all the time,especially after installing the propriatary ati drivers for my radeon 9600. After trying all sorts of stuff i finally tried booting in the 2.6.15-23-386 kernal (I had installed and was using the 686 kernel until that point.) since then I have had no real problems. 

Anyone else have an experience like this? Maybe incompabibilities between the 686 kernal and the ati drivers. (i had installed the ati drivers while running the 686 kernal btw). Can anyone tell me what kind of speed hit I'm looking at using the 386 kernel insted of the 686? Will I notice it (i mostly use the computer for web and office stuff but I run some openGL games too).

---

### Post by rjdohnert on 2006-08-26
Last time I had this error with Linux my RAM was going bad.  Do a memtest and see how your RAM is.

---

### Post by viz_e on 2006-08-29
After the last upgrades, the situation is going even worse. The Xorg memory leak is still there and now it consumes also a lot of CPU: always at least 10% without doing anything.

This problem is becoming really annoying and I am wondering if I should change distro... (even though I really like kubuntu, since 5.04).

---

### Post by AlbertTatlocksCap on 2006-08-30
I have the same problem with Ubuntu freezing 

I have it on a P4 1.8 with 1gb Ram now and it is fine

Although previously I installed it on an old Hp Vectra PII 400 with 512 Mb Ram and MGA200 on board - regularly just freezes (usually in screen saver mode) and I have to do a hard reboot

---

### Post by Tyltyl on 2006-08-30
I have a gdesklet monitor installed and I don't notice any particulary leak. There's one with XGL but not that bad since I crash even with 1GB of free RAM + swap.

---

### Post by xtknight on 2006-08-30
VMware is heavy on virtual memory usage.  Try reducing the max memory size of your virtual machines to see if it helps.  Defragging them may help.  I've found reiserfs fragments the virtual machines a ton so put the VM on either ext3 or xfs.

---

### Post by Metacarpal on 2006-08-30
> **trcook said:**
> <snip> Can anyone tell me what kind of speed hit I'm looking at using the 386 kernel insted of the 686? Will I notice it (i mostly use the computer for web and office stuff but I run some openGL games too).

There are a lot of conflicting theories on this subject.  The concept is that the -386 kernel is compiled to generically support most processors, so the -686 kernel won't change much for most users.  Most people encourage use of the -686 kernel on principle, while some benchmark tests ([such as this one]("http://www.ubuntuforums.org/showthread.php?t=25282&highlight=386+686+benchmark+results")) indicate that the performance difference is almost negligible.

---

### Post by eeefresh on 2006-09-04
I have been having complete lockups requiring a hard reboot for weeks now.  Sometimes I could go hours between lockups, and at other times I could have a few in five minutes.

After several hours of hair pulling and no fix in sight, I   decided to go back to Breezy Badger this weekend.  However, I thought I would post what didn't work in case its any help to the group.

My laptop is a Sony Vaio PCG-GR300 with a 1 gHz Pentium processor and 512 MB of RAM.  I was dual booting with XP ad everythingw as working fine on the windows side.

1. Ran memtest at startup.  Turned it off after 7 hours...how long does that thing take???  It was still showing all 512 MB, so I assumed it was okay (it was working in Windows, after all.)

2. Unplugged the USB mouse...still had freezes.

3. Switched to VESA drivers.  I thought I configured everything correctly, but afterwards my laptop couldn't get past the login screen.  I would sign in, then it started running some script, then BOOM! Back to login.  I had also run Automatrix but never installed any of the cideo card drivers through it.

4. Never installed XGL/Compiz, so I know that wasn't an issue.

The only thing I never tried was switching Internet browsers...I just couldn't part with all my Firefox extensions. 

Been running 5.10 for three days now without any issues.  I would love to come back to Dapper someday if anyone can ever find a fix!

---

### Post by Tyltyl on 2006-09-04
I had no luck even by running Dapper with a noacpi option.
It just freezes for no reason, no one has a 100% sure explanation.

---

### Post by jlh on 2006-09-04
I had random, unpredictable freezes running dapper on my Thinkpad T30.  I use an ATI graphic card.  I'm told there is a feature in dapper that is enabled by default, which does not play nicely with the ATI card.  The fix, which I followed, and which seems to have worked is this:

Edit the /etc/X11/xorg.conf file.
Under Section "Device", add:

Option "RenderAccel" "0"

Use the quotation marks in the edit.

Save and reboot.

---

### Post by mediocre on 2006-09-04
Hey, gustl87, I just tried your suggestions (modifying xorg.conf) including the changes you marked as "maybe", and so far, so good. I've also trimmed down rcS.d and rc2.d considerably to the following:

rcS.d
hold                                S08loopback           S25brltty             S55dns-clean
README                              S10udev               S30checkfs.sh         S60displayconfig-hwprobe.py
S01mountvirtfs                      S11mountdevsubfs      S35mountall.sh        S70screen
S01readahead                        S15module-init-tools  S39readahead-desktop  S70x11-common
S02hostname.sh                      S17procps.sh          S40networking         S80bootmisc.sh
S05keymap.sh                        S20checkroot.sh       S45waitnfs.sh         S85urandom
S07linux-restricted-modules-common  S22mtab  

in rcS.d, moved to hold:
S13pcmciautils  S25mdadm-raid  S26lvm  S27evms  S40pcmcia  S55pppd-dns


rc2.d
hold         S11klogd   S20dbus     S20nvidia-kernel  S50hdparm   S89atd   S99kdm       S99rmnologin
S10sysklogd  S19cupsys  S20makedev  S20rsync          S89anacron  S89cron  S99rc.local  S99stop-readahead

in rc2.d, moved to hold:
S05vbesave  S10powernowd.early  S18hplip  S20festival     S20powernowd    S25mdadm    S99acpi-support
S10acpid    S14ppp              S20apmd   S20laptop-mode  S25bluez-utils  S98usplash  S99timidity

This really is a bit of a problem, isn't it. I sure don't want to go through a distro switch, though. I'm fairly new to Ubuntu, and hope that the Powers That Be are monitoring this.

Nick

PS - Oh, yeah, AMD 3100+, 1 GB mem, Nvidia, when it freezes (hopefully FROZE) no mouse, no keyboard. I would try top as soon as symptoms showed (frenetic hard disk activity) but nothing weird, very low cpu & memory usage right until the total freeze-up.
N

---

### Post by edwardecl on 2006-09-04
Well my computer locks up when i try to boot using the latest linux kernel (k7) but thats a different story alltogether... although the same kernel runs fine on another machine...

latest 386 kernel is fine though how odd :).

Thats the only problems ive had with linux freezing... apart from quitting X when using with an ati card in my machine... that randomly locks up the computer... but it is a x1600pro AGP though...

---

### Post by meep on 2006-09-05
Well, I was still having the issues pretty regular.  So I burned some isos and wiped my pc.  Right now I'm running off Slackware, because I couldn't get Gentoo LiveCD installer(s) to run.  I also burned a copy of Ubuntu, too.  I'm not determined to leave Ubuntu or anything, just figured as long as I'm installing fresh, I might as well check out some of the alternatives, you know?

So, I'm very hopeful that a fresh Ubuntu will be the final trick to putting this behind me.

---

### Post by madchicken on 2006-09-05
Well, I don't think is only an Ubuntu problem. I think this is a Xorg 7 related problem linked with a kernel issue (maybe AGP module?). Maybe the modularization of X that comes with Dapper has some issue.
Initially I was thinking it was an ati driver issue, but switching to vesa driver led me to the same results. 
Then I thought it was a powernowd problem, but disabling it didn't make any difference.
I also tryed patches from Paul Drain ([http://64.71.152.24/](http://64.71.152.24/)) but they didn't worked for me...
Well...I tryed many solution, enabling and disabling a number of service and features on my system, but none of them solved my problem. Now I switched to Xorg-air (aiglx) and it seems that my system is going better (I had some crash, but playing a lot with compiz...so I think this can actually happen).
This is very funny: a beta (or maybe alpha?) release of the upcoming accelerated server is better than the stable one? Of course I am also using the beta radeon driver from freedesktop.

For **meep** : does Slackware uses Xorg 7 or is it still with the 6.8?

For all the others: do you know if other distro running Xorg 7 are freezing like Ubuntu Dapper?

---

### Post by madchicken on 2006-09-05
> I also tryed patches from Paul Drain ([http://64.71.152.24/](http://64.71.152.24/)) but they didn't worked for me...

Sorry...the site was closed by the author. So you can't find patches at that link.

---

### Post by sailor2001 on 2006-09-05
had 512 ram and was freezing up like everyone else.... install 512 more and haven't had a freeze-up since (couple - 3 weeks) still belive it (freeze-up) has something to do with the swap file

---

### Post by meep on 2006-09-05
Slackware was using xorg6.8, I believe.  I've reinstalled Ubuntu6.06 now, though.  No lockups so far, but we all know it's rather random and unexpected.  For me, it was infuriating because 9 out of 10 times, it would lock at the exact moment I began typing something.. IM, email, forum post, etc. It's a little funny. :)

Sailor:  I agree, I think it had to do with the swap file too.

---

### Post by eeefresh on 2006-09-05
I forgot to add in my post that my swap file was fine.  I had allocated 512 MB to it, and it showed up under *Disks* and also in my memory gDesklet.  So I doubt the swap file was an issue for me, either.  My laptop does have an ATI card, though, so maybe that was part of the issue.

Meep - I reinstalled Dapper from scratch *three times*, and each time I got the lockups, although not right away.  Hopefully you will have better luck.

My lockups always seemed to occur when I was in Firefox, but then again, I am always using it, so it might have been coincidence.  I don't think it was memory leak in the browser, though, because I remember one lockup occurring right after I first opened Firefox.

---

### Post by mediocre on 2006-09-05
Hmmm... I think I can replicate my freeze up, which is to say, I know of a series of events that will cause it.

I had the system up for over 30 hours after applying the changes I mentioned earlier, but just a few minutes ago, I caused the crash. The thing is, it seems so unlikely, that it's only now that I've put it together that this has happend *several* times before:

I had closed everything but a konsole (using kubuntu desktop over a fairly clean ubuntu install). I opened my cd-writer device (I mean I pushed the button on the cd-writer that opens the door--I hadn't launched any software at this point). The door wouldn't open and there was no activity light. I pushed the button a few times more (well, what would YOU have done???) when bzzzzzzzzzzzzzzzzz went my hard drive, and plenty of blinkity-blink on the HD activity light. Within a minute, I had no mouse, no keyboard, nothing. Previous experience has taught me that I can wait until the cows come home, the system won't be back. 

Nothing unusual reported by top, but here is a bit of /var/log/kern.log from JUST before the crash:

Sep  5 18:48:24 heracles kernel: [17278062.196000] hdd: irq timeout: status=0xd0 { Busy }
Sep  5 18:48:24 heracles kernel: [17278062.196000] ide: failed opcode was: unknown
Sep  5 18:48:24 heracles kernel: [17278062.196000] hdd: DMA disabled
Sep  5 18:48:54 heracles kernel: [17278092.196000] hdd: ATAPI reset timed-out, status=0x80
Sep  5 18:48:54 heracles kernel: [17278092.196000] hdc: DMA disabled
Sep  5 18:49:23 heracles kernel: [17278121.188000] ide1: reset: master: passed; slave: failed
Sep  5 18:49:29 heracles kernel: [17278126.392000] hdd: status timeout: status=0x80 { Busy }
Sep  5 18:49:29 heracles kernel: [17278126.392000] ide: failed opcode was: unknown
Sep  5 18:49:29 heracles kernel: [17278126.392000] hdd: drive not ready for command
Sep  5 18:49:59 heracles kernel: [17278156.392000] hdd: ATAPI reset timed-out, status=0x80
Sep  5 18:50:28 heracles kernel: [17278185.384000] ide1: reset: master: passed; slave: failed

So... what??? Is it really the cd-writer that's causing the grief? Can anyone else verify/support this? BTW: /dev/hdd is my cd-writer, /dev/hdc is a dvd-rom reader. I'm going to keep trying to replicate this.

Nick.

---

### Post by Tyltyl on 2006-09-06
I disabled ACPI 2.0 from the BIOS and I ran 2 days without a freeze yet.
But I also changed the renderaccel in xorg, so I don't know which of the two did the job.

---

### Post by eeefresh on 2006-09-06
For those of you who have said you made some tweaks and got Dapper working witout freezes, please continue to provide updates and let us know if the fix is still working. 

Several have posted that they thought they fixed it, only to post an update later saying it didn't work.  Has anyone been able to remain freeze-free with Dapper for more than a few days?

---

### Post by mooha on 2006-09-06
Hi All,
I have Toshiba A60/256RAM   ATI Mobility Radeon 7000 IGP   

Yesterday I had the same thing as the First Post here, with XMMS and USB disk, today, I tried something and every thing works fine without any problems like: system slow-up or any thing Like that wich is:

$ sudo dpkg-reconfigure xserver-xorg

My mistake when I first installed Dapper and had this problem is that when I configured xserver I putted 64000KB, so I had that problem specialy when I wanted to make sure about it I instlled KDE then TuxRacer to test graphics it Freeze.
So all I did is to change it to 32000KB for ATI Mem.:-D 

Hope is gonna work for some of you all, 
Wish you the Best

---

### Post by wordsmythe on 2006-09-06
I don't have anything fancy running, and the only problems I've had have been  with Firefox vs. Flash and java.

---

### Post by Tyltyl on 2006-09-06
> **eeefresh said:**
> For those of you who have said you made some tweaks and got Dapper working witout freezes, please continue to provide updates and let us know if the fix is still working. 

Several have posted that they thought they fixed it, only to post an update later saying it didn't work.  Has anyone been able to remain freeze-free with Dapper for more than a few days?

Still working without freezes after about 2 days.
I disabled ACPI 2.0 in the BIOS and put renderaccel "0" in xorg.conf

Sorry, but I still have to check which of the two fixed the problem.

---

### Post by meep on 2006-09-06
"Has anyone been able to remain freeze-free with Dapper for more than a few days?"

I was freeze-free for a couple weeks at a time.  Getting rid of the Nvidia drivers fixed most of my original problems.  Focusing on whether my swap was Truly active helped, too.  I'd be interested in how folks are doing it with no freezes after a month or so.  I saw the Renderaccel tip in some other forums, too, so maybe that'll help.  

I'm using Gentoo now and eyeing Arch.  So if my Gentoo breaks, there's a good chance I'll try Arch next.  I think I saw the Renderaccel issues in the Gentoo forums.  And, we know those Gentoo users are serious hackers, so hopefully they're on to something...

---

### Post by Tyltyl on 2006-09-07
Ok I removed the "renderaccel" from xorg and I'm still freeze-free, so in my case it was the ACPI 2.0.
Strange but true...many problems with the same symptoms, probably it's all originating from the kernel.

---

### Post by grahams on 2006-09-08
Seems I have a similar problem and I can reproduce it very quickly. I have a Compac n610c laptop and I only ever seem to get system freeze under the following circumstances :-

 With an external monitor in dual screen mode set to 1600x1200 and laptop screen set to native 1400x1050. 
 Then using either firefox or thunderbird on the external monitor. 
 In this mode I expect to freeze within 20 mins. 

Without connecting the external monitor I do not get the freezes and even with the external monitor connected I do not get freezes if I open firefox or thunderbird from the laptop screen.

The n610c has an ATI graphics chip and I'm running  2.6.15-26-686.

---

### Post by madchicken on 2006-09-08
> **grahams said:**
> Seems I have a similar problem and I can reproduce it very quickly. I have a Compac n610c laptop and I only ever seem to get system freeze under the following circumstances :-

 With an external monitor in dual screen mode set to 1600x1200 and laptop screen set to native 1400x1050. 
 Then using either firefox or thunderbird on the external monitor. 
 In this mode I expect to freeze within 20 mins. 

Without connecting the external monitor I do not get the freezes and even with the external monitor connected I do not get freezes if I open firefox or thunderbird from the laptop screen.

The n610c has an ATI graphics chip and I'm running  2.6.15-26-686.

Yes, but this seems a problem related to xrandr. They are working on it:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/47775](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/47775)

bye

---

### Post by edu65 on 2006-09-08
Does the problem disappear when you use a 386 kernel?

Sounds similar to the problem described by canadianwriterman in this thread:

  [http://ubuntuforums.org/showthread.php?t=231766](http://ubuntuforums.org/showthread.php?t=231766)

---

### Post by mediocre on 2006-09-09
Regarding my post #312--it was a no-go. Still experience freezes when opening the cd-writer door if the system has been on for more than about 24 hours. 

Now, in addition, I've added "noacpi" to the kernel boot line in /boot/grub/menu.lst, so that it looks like this:

kernel     /vmlinuz-2.6.15-26-386 root=/dev/hda5 ro noacpi

About 36 hours now with no sign of the bug, which is, as usual, meaningless. I'll report back on this.

---

### Post by mediocre on 2006-09-10
And, the bug is still there. Wow. I've disabled just about everything I can, I think...

N

---

### Post by eeefresh on 2006-09-10
:(

---

### Post by Tyltyl on 2006-09-11
> **mediocre said:**
> And, the bug is still there. Wow. I've disabled just about everything I can, I think...

N

I tried the noacpi too, but just like you I still had the freeze problem.
What I did it was to disable ACPI 2.0 from the BIOS. Give it a try.

---

### Post by grahams on 2006-09-11
I installed and then booted from the 2.6.15-26-386 kernel and was able to freeze my system within 7 minutes, just by running firefox (on this forum site), on my external monitor (dual monitor config). My problem does not appear to be a 686 kernel issue. If I get time I'll see if I can install the initial dapper kernel and try to freeze my system.

---

### Post by EnderTheThird on 2006-09-11
I'm pretty sure that the option is actually "acpi=off" and not "noacpi" for the entry in grub.  I used to have problems with my computer occasionally freezing and/or locking up, with the only fix being to manually restart the computer.  But I added "acpi=off" to the appropriate entry in /boot/grub/menu.lst and now it's running like a champ.  Here's the main entry in my menu.lst, just so you can see exactly what line I'm talking about (underlined):

```

title		Ubuntu, kernel 2.6.15-26-686
root		(hd1,0)
_kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sdc1 ro quiet splash acpi=off elevator=cfq_
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

```

Hope that helps you guys out.  I haven't had any problems since I put that in there!

EDIT:  Also note that if you use "acpi=off", your shut down option won't actually shut down your system.  It will halt everything, but you'll have to power down manually when it gets to that point during shut down.  Restarting your computer should still work just fine though.

---

### Post by viz_e on 2006-09-13
Dual head seems to be the problem here. If I run kubuntu without the external monitor (even with firefox) the Xorg memory leek seems to be solved, or at least is very low.

Anyone having a memory leak without a dual head?

---

### Post by grahams on 2006-09-14
Hi 

I've only had freeze issues with a dual head config and only when running firefox or thunderbird on the external monitor. Never seen an issue if I run them on the laptop's main screen even in dual head mode.

What are you using to detect memory leaks? free?

---

### Post by viz_e on 2006-09-14
> **grahams said:**
> Hi 
What are you using to detect memory leaks? free?

I am using top. Check my messages #237 and #240 of this thread.

---

### Post by grahams on 2006-09-15
> **grahams said:**
> I installed and then booted from the 2.6.15-26-386 kernel and was able to freeze my system within 7 minutes, just by running firefox (on this forum site), on my external monitor (dual monitor config). My problem does not appear to be a 686 kernel issue. If I get time I'll see if I can install the initial dapper kernel and try to freeze my system.

I've found dropping the resolution on the external monitor from 1600x1200 in xorg.conf to 1400x1050 cures the rapid freezing, at least I had no issues for over 1hr using thunderbird and firefox. After going back to 1600x1200 in xorg.conf and restarting X my system frooze in 10 minutes. 

I'll try to do more tests tomorrow.

---

### Post by eeefresh on 2006-09-15
> **EnderTheThird said:**
> I'm pretty sure that the option is actually "acpi=off" and not "noacpi" for the entry in grub.  I used to have problems with my computer occasionally freezing and/or locking up, with the only fix being to manually restart the computer.  But I added "acpi=off" to the appropriate entry in /boot/grub/menu.lst and now it's running like a champ.  Here's the main entry in my menu.lst, just so you can see exactly what line I'm talking about (underlined):

```

title		Ubuntu, kernel 2.6.15-26-686
root		(hd1,0)
_kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sdc1 ro quiet splash acpi=off elevator=cfq_
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

```

Hope that helps you guys out.  I haven't had any problems since I put that in there!

EDIT:  Also note that if you use "acpi=off", your shut down option won't actually shut down your system.  It will halt everything, but you'll have to power down manually when it gets to that point during shut down.  Restarting your computer should still work just fine though.


Ender - Is this trick still working for you?  I tried it last night and I still experienced a freeze.  I did a fresh install of Dapper, made the acpi=off change, and then my laptop froze a few minutes later while using Automatrix.

---

### Post by grahams on 2006-09-15
My tests are looking good :)

If I lower the screen resolution via xorg.conf or system->preferences->screen res on either the external monitor or laptop screen my freezing issue stops. I've been working all day at 1600x1200 external and 1024x768 on the laptop screen (which is capable of 1400x1050). 

The video chip in a Compaq n610c is an ATI radeon mobility M7. 

Here is my xorg.conf which allows dual head mode.
------------------------------
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        Screen         "aticonfig-Screen[1]" LeftOf "aticonfig-Screen[0]"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

#Section "Device"
#       Identifier  "aticonfig-Device[0]"
#       Driver      "fglrx"
#       BusID       "PCI:1:0:0"
#EndSection

#Section "Device"
#       Identifier  "aticonfig-Device[1]"
#       Driver      "fglrx"
#       BusID       "PCI:1:0:0"
#       Screen      1
#EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1400x1050"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]"
        Device     "aticonfig-Device[1]"
        Monitor    "aticonfig-Monitor[1]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1600x1200"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

---

### Post by fahadi on 2006-09-21
2 years of using suse 9.1 on my laptop I decided to use a new flavour of linux, xubuntu.

After installing it I started to notice what everyone on this thread has noticed that xorg process starts to eat more and more cpu cycles.  

At first I thought, its cos the video card driver was not correctly identified by installation process but after manually fixing this problem, Xorg process according to TOP starts to eat to many cpu cycles, not straight away but slowly builds it self up to doing this and I have no idea why or what action is causing it.

This thread is 34 pages long and no one seems sure why this problem is happening.

I did goto this site 
[https://launchpad.net/distros/ubuntu/+bug/51991](https://launchpad.net/distros/ubuntu/+bug/51991) to add my problem to the bug list.

Like everyone else on this thread I am desperate for a solution, 

Regards Fahad

---

### Post by warpzone on 2006-09-22
I've heard mention of this particular interation of the freezing bug earlier and wanted to add my name to the list. I'm using Kubuntu 6.06. The specifics are:

------

1) Firefox slows down or crashes completely, and the webpage randomly refreshes, freezing Firefox and any open GTK-based apps during the long refresh. KDE apps do not seem to be affected by the freezes (for instance, I can still chat using Kopete and Konversation without problems)

2) 'top' reveals that xorg and firefox memory usuage increase rapidly, until the ram and swap are full and the system becomes unusable and crashes.

3) Restarting xorg will reset the memory used by firefox and xorg.

4) It seems a program, usually Firefox, is required in order to kickstart the xorg memory leak. Closing the program, however, will not stop the leak and eventually xorg must be restarted or the system will crash. 

--------

I'm not sure if this is just a firefox memory affecting xorg. Installing a previous version of xorg did not solve the problem, I'm going to mess with the firefox config and see if I can come up with anything.

Hope somebody finds a solution, this is my first major problem with the software so far.

---

### Post by cashon on 2006-09-23
I believe the problem lies in the kernel 2.6.15-26-686. After I revert back to using 2.6.15-26-386, I did not experience any more freezing...

And just FYI, kernel 2.6.15-27-686 has just been released! I just upgraded my dapper and I think 2.6.15-27-686 has fixed the freezing problem...

I have been using Dapper since its official release and I only encounter this one serious bug only since its release. So, you Ubuntu user out there, don't just because of freezing and you tell the whole world that Ubuntu is not good or want to revert back to the stupid, useless, crap W!

Regards,

Ubuntu Die Hard!

---

### Post by eeefresh on 2006-09-23
> **cashon said:**
>  I just upgraded my dapper and I think 2.6.15-27-686 has fixed the freezing problem...

Can anyone else confirm this?  If it seems to be fixed now, I can finally ditch Breezy and reinstall Dapper...

---

### Post by egoldtech on 2006-09-23
Hi, may be is graphic card (ATI Radeon Mobility 6 (probably the Radeon 9000 series))
because I have IBM T30, and happens the same thing,  and a friend of mines with the same laptops, has the same problem.
I have the lastest drivers/

---

### Post by warpzone on 2006-09-23
As stated earlier, there is an iteration of this bug that involves firefox randomly refreshing and locking up, which also seems to kick start the xorg memory leak. I fixed this problem on my comp, I hope it will help others. Here's how:

Open your package manager, and in the search bar, type 'driver'. Scroll down until you see the list of xorg input drivers and xorg display drivers. On my comp, and I'm assuming this is by default, EVERY display driver and EVERY input driver were installed. A bit of overkill, eh? So get rid of every driver you don't need. If you have specialized hardware, you'll know the drivers you need. If not, remove every driver except keyboard and mouse input, anything ending in dev, vesa (as a fallback option), and whatever display driver your video card requires. Everything else can probably be safely removed. Now restart your computer.

I'm not sure if this a solution, it seems so, though. If freezes still occur I will repost. Regardless, though, most of those drivers are not needed, so removing them will help system performance. 

Happy solution hunting, I hope something more solid appears.

EDIT: The Firefox freezing problem persists, and xorg appears to continue to devour memory. However this problem only persists when firefox is running, so I'll investigate it from the firefox memory leak angle instead.

---

### Post by fahadi on 2006-09-27
Well I managed to solve my problem of xubuntu slowing down to almost a complete a halt, in the grub start-up options i added acpi=off and that was it the Xorg process which was eating so much cpu has stopped doing this and my Linux seems more stable and working, but something else has happened, the start up tune that I get when the log in screen appears seems stuck in a loop and keeps repeating it self over and over even once i have logged in, its annoying, so not sure how to configure my sound on the laptop to make it stop.

Side note I have been experiencing this Xorg problem but my Linux kernel was the 386 version and not the 686 version

---

### Post by Tyltyl on 2006-10-01
Argh! We are at it again! Since when I disabled ACPI 2.0 from the BIOS and used a noacpi option in the boot it worked FLAWLESSLY for more than month and a half.
But then I upgraded the kernel to 2.6.15-27-686 and started freezing again.

I forgot to add the noacpi line in the boot options, I did and the system is much much more stable, but it still occasionally freezes.

:-| :-| :-|

EDIT: Yeah, it froze up again. Everytime I post here that it works or that it's stable the whole ******* machine freezes. And nobody helps me!!!

---

### Post by eeefresh on 2006-10-01
> EDIT: Yeah, it froze up again. Everytime I post here that it works or that it's stable the whole ******* machine freezes. And nobody helps me!!!

I feel your pain, Tyltyl.  The Ubuntu community is typically very helpful, but I think everyone is stumped by this issue.  I haven't filed a bug report, but several others have.  Until someone finds a fix that actually works, I'm sticking with Breezy Badger.  It works flawlessly for me, though I can't use the latest version of AmaroK.


Hopefully this issue won't resurface in Edgy.

---

### Post by viz_e on 2006-10-02
How many of you having this problem, is actual using a dual head setup? I do and when I restart without the external monitor, everything seems to work fine (no Xorg memory leak, to be precise).

---

### Post by grahams on 2006-10-02
I only see freezes when an external monitor is attached. Lowering the resolution my laptop LCD and/or the external screen seems to stop the freezing, but this is a work around rather than a fix.

---

### Post by grahams on 2006-10-02
I've just updated to 2.6.15-27-686 and the freezing has returned even at lower resolutions.

---

### Post by eeefresh on 2006-10-02
> **viz_e said:**
> How many of you having this problem, is actual using a dual head setup? I do and when I restart without the external monitor, everything seems to work fine (no Xorg memory leak, to be precise).

No dual head here.  I'm running a P-3 laptop.

---

### Post by fahadi on 2006-10-03
Have any of you tried to switch acpi off ?

I did this and it worked for me, but now i have a sound problem that doesn't exist when acpi is on !!!

Not sure whats going on wish i just stuck to suse 9.1.

](*,) 

also not using dual monitor here

---

### Post by altaaa on 2006-10-03
My work laptop (HP NX6110-Celeron1.4-768MB-i915) also froze. I used dapper with aiglx/compiz:
- I tried changing memory modules; to no avail.
- I tried disabling ACPI in menu.list (there's no option for it in the BIOS), but this made my system REALLY slow.
- I tried a dozen other things, dma, swap, most I can't remember but none worked.

So now I have reinstalled dapper. Updated all packages, installed the multimedia codecs 'n stuff through apt-get with a little help from ubuntuguide.org (so no Automatix - read somewhere it can really mess up your system), and I'm running stable. I left the laptop on all night, and in the old situation it would have froze for sure. But now, this morning, it was still going strong.

Don't know about the rest of you, but if I have to choose between a stable system or state-of-the-art eyecandy, I'm going for stability.

It's a shame that the nicest distro by far suffers from such serious stability issues, because from what I've read here (and elsewhere), a lot of you aren't even running unstable software (i.e., xgl/aiglx/compiz/beryl) and are still experiencing crashes and freezes and stuff like that. 

All I can say is: Don't give up! Somebody is bound to fix these problems.

[SIZE="1"]Just my 2 cents :-D[/SIZE]

---

### Post by madchicken on 2006-10-03
Hi guys. For those using the ati radeon driver (not the fglrx) it seems that the latest driver in edgy is fixing the problem of hard locks.
According to [this]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/47775") bug report (see last comments) the fix still doesn't solve crashes using the dual head.
I'm testing breezy now and for two days I didn't had hard locks using a single monitor...

Bye

---

### Post by originof on 2006-10-03
well, on forum.ubuntu-it.org (italian forum), we have resolved the problem removing powernowd..


sudo apt-get remove --purge powernowd

---

### Post by grahams on 2006-10-03
> **originof said:**
> well, on forum.ubuntu-it.org (italian forum), we have resolved the problem removing powernowd..


sudo apt-get remove --purge powernowd

Did not work for me - frooze within 5 minutes after removing powernowd and rebooting.

---

### Post by grahams on 2006-10-03
Do we need to submit a bug report somewhere other than launchpad as from [https://launchpad.net/distros/ubuntu/+bug/51991](https://launchpad.net/distros/ubuntu/+bug/51991) doesn't look like it's assigned to anyone.

---

### Post by eeefresh on 2006-10-03
> **madchicken said:**
> Hi guys. For those using the ati radeon driver (not the fglrx) it seems that the latest driver in edgy is fixing the problem of hard locks.
According to [this]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-ati/+bug/47775") bug report (see last comments) the fix still doesn't solve crashes using the dual head.
I'm testing breezy now and for two days I didn't had hard locks using a single monitor...

Bye

Please let us know if that is still working in a few days, madchicken.  So did you install the new ATI driver in Breezy?  How did you do it?

---

### Post by madchicken on 2006-10-04
> **eeefresh said:**
> Please let us know if that is still working in a few days, madchicken.  So did you install the new ATI driver in Breezy?  How did you do it?

Sorry, but I don't know if you could install the new driver in other versions than edgy. Maybe you could download the source code from freedesktop and compile it, but I'm not sure of this, because edgy uses Xorg version 7.1 (Breezy is actually using version 6.8 and Dapper the version 7).
I really hope that the Ubuntu community will backport the driver if it really solves the hard locks issue.

I'll post here my experience using edgy and the new driver/Xorg version.

Bye

---

### Post by Tyltyl on 2006-10-04
Is it safe to remove powernowd?

Strangely the problem reappeared when I upgrade to kernel 2.6.15-27 and even if I downgrade the problem remains.
No matter if I use noacpi, acpi=off, noapic, nolapic etc. That only fixed for one month and then for some reason started again.

Oh btw, sorry for being that angry and thanks everyone for the support.

---

### Post by madchicken on 2006-10-04
> **Tyltyl said:**
> Is it safe to remove powernowd?

Yes, it is. If you want something similar to powernowd you can use laptop-mode (check the config file in /etc/laptop-mode/laptop-mode.conf) or cpufreqd instead.
But removing powernowd didn't solve the problem for me and for many other in this thread.

Good luck.
Bye

---

### Post by Tyltyl on 2006-10-04
Same here :(
Removed powernowd, I rebooted as a precaution and got a freeze in 9 minutes :(
Thanks anyway for the suggestion.

But since I have the same problem with Slax I think the problem must be in some acpi setting, or broken/bugged package that they have in common...
My hardware seems all ok.

---

### Post by dyous87 on 2006-10-04
Any of you who are experiencing lock ups and are using the ATI drivers, have you tried switching to the fglrx ones instead. It may solve your problems.

---

### Post by grahams on 2006-10-04
Looks like a fix is on the way, at least for setups like mine (ATI graphics and dual monitor). I installed 6.10 (edgy eft) nd I've been a happy little camper with 3 days of no freezing at all. 

6.10 seems to be very stable, even though it's using gnome 2.16 and everything seems to work fine :D 

I will report back if my freezing issue returns.

---

### Post by javarunner on 2006-10-05
Me too!  I have a dual-boot laptop (XP Pro/Ubuntu) that locks-up in Ubuntu about once every day.  This morning I started up, got the desktop, slid a couple of desktop shortcuts around, then it froze.  Mouse was only thing that moved.  I turned off the laptop, restarted and of course it warned me about incompletely dis-mounted drive.  Ran recovery, found all kinds of issues on the drive - which is a fairly new drive, fixed them, then re-booted.  got all the way to desktop, opened up a terminal, then froze again.  Repeated all previous steps and now it appears to be happy - finally.  Ironically, I have no issues with win XP.  Not convinced that Ubuntu is ready for the real-world, but keeping an open mind since I really like it when it works.

---

### Post by doobit on 2006-10-05
> **grahams said:**
> Looks like a fix is on the way, at least for setups like mine (ATI graphics and dual monitor). I installed 6.10 (edgy eft) nd I've been a happy little camper with 3 days of no freezing at all. 

6.10 seems to be very stable, even though it's using gnome 2.16 and everything seems to work fine :D 

I will report back if my freezing issue returns.

Anytime you have a lockup, the problem is most likely a hardware driver issue, so I'm not surprised that a newer kernel solved the problem for you. 
For those still having problems, you should look at hardware related issues. Try disabling/enabling ACPI, DMA, graphics drivers, etc. until you find the conflict. Use the OS's ananlytical tools and logs to help you find out.

---

### Post by eeefresh on 2006-10-05
> **doobit said:**
> Anytime you have a lockup, the problem is most likely a hardware driver issue, so I'm not surprised that a newer kernel solved the problem for you. 
For those still having problems, you should look at hardware related issues. Try disabling/enabling ACPI, DMA, graphics drivers, etc. until you find the conflict. Use the OS's ananlytical tools and logs to help you find out.

Thanks for the advice, Doobit, but if you read the whole thread you'll see that all of those suggestions have been covered and did not work for many of us.

---

### Post by thoffland on 2006-10-06
I was having the same problem after upgrading the kernel to 686.  I booted the 386 kernel and no more freezing. 

The keyboard became totally unresponsive, so ctrl+alt+backspace didn't work and I had to hold the power key to shutdown. 

I didn't notice a difference between the two on my thinkpad, so I'll stick with the 386.

---

### Post by jlh on 2006-10-06
Thoffland

I had good success fixing freezing on my T30 by following this fix:

"I resolved the lockup problem on my laptop (Thinkpad T30 w/ATI Radeon
Mobility 7500) by modifying my /etc/X11/xorg.conf file.

Around the lines that look like this:
============
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW
[Radeon Mobility 9000]"
Driver "ati"
============

Insert this before "EndSection":
============
Option "RenderAccel" "0"

---

### Post by towsonu2003 on 2006-10-06
obviously I didn't read the whole thread... 32 pages... ouch.

I just wanted to suggest using xrestop for those who suspect there is a memory issue with xorg. xrestop will show you what components of x (such as firefox, vmware) are using most of the resources (memory)

Here is a snapshot of a healthy machine (knock on wood please). notice that most resources are used by swiftfox in this case, without causing instability. 

```

res-base Wins  GCs Fnts Pxms Misc   Pxm mem  Other   Total   PID Identifier
2c00000   211   71    1 1272  108    49584K     10K  49594K   ?   Ubuntu Forums - Reply to Topic - Swiftfox
1e00000     0    0    0    1    0     4000K      0B   4000K   ?   <unknown>
0a00000    10   30    2    4  728      780K     20K    800K  5267 metacity
0c00000   225   51    0    6   50      782K      7K    789K  5272 Top Expanded Edge Panel
2000000    33   83    1    6   37      782K      4K    786K  5340 09/14/2006
2e00000   109   60    1   46   51      462K      6K    468K   ?   turk-linux for towsonu2003@gmail.com - Thunderbird
3400000    47   54    1    4   24      393K      3K    397K  5272 liferea
3600000    15   46    1    4   30      393K      3K    396K   ?   mehmet@portable: ~
2400000     5   35    0   14   13      391K      1K    392K  5272 battstat
1000000    10   45    1    5   16      386K      2K    389K  5274 Desktop
1a00000     7   36    0    2    8      384K      1K    385K  5272 trashapplet
2600000     8   33    0    2    8      384K      1K    385K  5272 mixer_applet2
0600000     2    2    0    2   10      384K    336B    384K  5049 gnome-session
2a00000     2    1    0    0  715        0B     16K     16K  5352 gnome-screensaver
0800000     4    1    0    0  406        0B      9K      9K  5248 gnome-settings-daemon
2800000     6   40    0    1    7        4B      1K      1K  5272 ClockApplet
3000000     1    2    1    0    7        0B      1K      1K   ?   <unknown>
1200000     1    2    1    0    4        0B      1K      1K   ?   portable - conky
0200000     0    1    1    0    0        0B      1K      1K   ?   <unknown>
1600000     4   28    0    1    5        4B    888B    892B  5289 update-notifier
0e00000     4   28    0    1    5        4B    888B    892B  5276 gnome-volume-manager
3200000     4   28    0    1    4        4B    864B    868B 10915 gksu
1c00000     3   28    0    1    3        4B    816B    820B  5300 gnome-cups-icon
1800000     3   28    0    1    3        4B    816B    820B  5295 gnome-power-manager
3800000     1    1    0    0    0        0B     48B     48B   ?   xrestop
2200000     0    1    0    0    1        0B     48B     48B   ?   <unknown>
1400000     0    1    0    0    0        0B     24B     24B   ?   <unknown>
0400000     0    1    0    0    0        0B     24B     24B   ?   <unknown>

```

PS: sudo apt-get install xrestop

---

### Post by saxin on 2006-10-06
I changed back to the 386-kernel, and now my computer never freezes anymore =)

---

### Post by llanitedave on 2006-10-06
I've had the same problem with Kubuntu on a homebuilt AMD-64 3000 with an Nvidia drive.  I was worried that it was my hardware selection.

However, I also have an Apple G4 iBook that dual boots with Dapper, and other than the Apple proprietary hardware issues(trackpad slow and no wifi) I've NEVER had a single problem with kubuntu on that machine.

---

### Post by Tyltyl on 2006-10-06
I have changed many kernels without succes. Now without a change I ran 2 days without a freeze.
I will try to upgrade to Edgy in the next days.

---

### Post by Tyltyl on 2006-10-09
I installed Edgy and the first thing I could do was...to freeze :(

---

### Post by towsonu2003 on 2006-10-09
> **Tyltyl said:**
> I installed Edgy and the first thing I could do was...to freeze :(

what happens when you change your x driver from <whatever> to vesa (under section "device")?

---

### Post by Tyltyl on 2006-10-09
> **towsonu2003 said:**
> what happens when you change your x driver from <whatever> to vesa (under section "device")?

Nothing changes, I still freezes.
Today I tried with Edgy and Dapper live CD and all 3 times I froze. By default they use the vesa drivers.

For some reason the Live version seems more prone to freeze than my present installation, which is more "worked" and it's almost 1 year old.

I guess that it has some changes than make it different to the Live CD so that it crashes less frequently. Maybe ACPI...

---

### Post by llanitedave on 2006-10-09
I left my desktop running overnight, and noticed in the morning it was noticeably slower.  I used the top command, and found that Xorg was using over 77% of available memory -- and I have 1 Gig!

Rebooted, and it gets back up to normal speed.  (However, Thunderbird does have to pause to refresh itself every few minutes.  Doesn't seem to be anything I can do about that.)

That's a pretty serious memory leak!  Again, the PPC version on my G4 iBook has no such issues.

---

### Post by Tyltyl on 2006-10-09
But the memory leak doesn't explain why it crashes soon after 2-5 minutes after logging in :(

---

### Post by llanitedave on 2006-10-09
I did have a similar issue a year ago with Suse 9.3 professional -- that's one of the reasons I decided to try Kubuntu.  Suse would often freeze soon after logging on.  Kubuntu hasn't done that, but it does get more sluggish over time.  And it started with Dapper.  Breezy always worked fine.

So the issue may not be unique to Ubuntu.  I'm still puzzled, and I'm looking forward to both Edgy and Fedora 6 coming out.  I expect to give both of them a try.

---

### Post by Tyltyl on 2006-10-11
I tried again with Dapper Live, it crashed in 3-4 minutes and this time I kept "top" open, but didn't notice any abnormal memory use during the crash.

---

### Post by elemental0125 on 2006-10-11
Have you tried running a memory test?

On my previous laptop I used to get random freezes which I couldn't explain. I ran a memory tester (If I recall correctly, there's one on the Live CD as startup option), which tracked it down to a bad stick of RAM. RAM left the laptop and the laptop ran fine.

---

### Post by eeefresh on 2006-10-11
I ran a memory test.  I can't remember how, either, but someone suggested it in this thread several pages ago.  It ran for hours and never actually finished, so I turned it off.  I think someone else reported the same problem.  Maybe the fact that the test never ended indicated a problem with the memory? 

However, I don't think its a memory issue, at least for me.  I switched back to 5.10 and its been working great for weeks.

---

### Post by towsonu2003 on 2006-10-11
> **eeefresh said:**
> It ran for hours and never actually finished, so I turned it off. 

it is supposed to not end with errors afaik -> so your memory is ok.

it's probably a hardware (driver) issue

---

### Post by Tyltyl on 2006-10-11
I ran a memory test several times, the last time yesterday for 5 cicles and several hours without errors :(
Anybody knows about problems or incompatibilities with a P4P800-x motherboard?

---

### Post by alan53 on 2006-10-11
Just as a slightly offside, how many people reporting these freezes have a Wacom stylus/tablet combination?  I know mine isn't perfect and causes all kinds of havoc if it's unplugged while the system is running.

---

### Post by llanitedave on 2006-10-11
OK, I had claimed I had no freezup issues on my G4 iBook -- I was wrong.

Apparently, my habit of simply closing the lid and letting it sleep when I'm done with it clears the memory enough to keep it from happening.  However, I just let it run all night and all day with the lid open, and several applications open, including OO.o, SPE, Bluefish, KCalc, and top.

When I activated it, the clock was stopped, and the screen was almost completely frozen.  The mouse cursor moved sporadically and with several-second delays.

When I *finally* got top to the front, it showed a surprising thing.  My swap space is completely used up:  120008k total, 12008k used, 0 free.  My main memory is 514844k available, 513264k used, and 1580k free.  That's 99.7% used!

And the biggest memory culprit isn't Xorg, as it is on my desktop, it's Python!!!  It's using 77.5% of available memory!  Xorg is down at 5.9%

This is indeed puzzling.

---

### Post by Tyltyl on 2006-10-12
So if I get it correctly there are many problems that cause these type of crash. It may be the wireless, the ACPI, ATI/nv drivers, corrupted RAM etc.
It's just a bad way for the system to manage the crash without output.

---

### Post by madchicken on 2006-10-12
I don't have any more crash since Edgy upgrade. 
To those have tryed with a live: I don't think a live version is good, because I don't think it uses all latest version of packages and drivers. 
My problem was related to the ATI radeon open source driver, and now it seems to be gone (touching wood...) with the latest driver upgrade. Maybe the kernel upgrade (2.6.17) is also contributing to the stability of my system.
I really don't know, but it's working here.
I say: if you can, upgrade to edgy now. Maybe it won't solve your problem...but it still a try.

bye

---

### Post by Tyltyl on 2006-10-12
I tried with a fresh Edgy install already and I had the same problem. If I try to upgrade I get several errors, so I won't try again for now.

I noticed an incongruence with the use of RAM
[http://snipurl.com/oxqy]("http://snipurl.com/oxqy")

Top shows almost the whole 1GB of physical RAM in use, while the desklet on the left only shows 305MB in use.
And also by summing the processes in use they don't seem to use the whole RAM.

---

### Post by saxin on 2006-10-21
So, what can this be? I upgraded to Edgy now and still my computer freezes like every 10second. I can't use my computer like this :(

---

### Post by wargames on 2006-10-21
I'm having strange freezing problems on a laptop. I keep trying to install Dapper on a Compaq 2190US and it seems to go ok. I can boot up normally and run the system as usual but at random times the system will freeze and I can't do anything but hit the power button. Almost every time it freezes the "Save Screenshot" application loads by itself anywhere around 4 to 50 times in a row and the whole system totally locks up. I've done several installs and it happens the same way each time. Also the filesystem seems to get corrupted as well. Weird. I did a 3 hour memtest and passed, and this can also happen on the LiveCD session as well so that rules out a hard drive problem. The system does not seem hot, just warm and the fan appears to be running normally. I've been trying to setup the winmodem but so far no go. Any idea what would cause the "Save Screenshot" application to load automatically and the system freeze? Using the "top" command, doesn't seem to show anything unusual and their are no error messages in kern.log. I've never seen this behavior before.

Any ideas?

---

### Post by viz_e on 2006-10-26
Solved the xorg memory leak. Solution: edgy eft!

To my experience the difference between edgy and dapper is much bigger than dapper to breezy. My system is now *much* faster, font and appearance much better and *no* memory leak.

Have fun with edgy.

---

### Post by two55309 on 2006-10-26
I've been using edgy for the last week or so and last night i had the freeze again.  I had upgraded from dapper because of this problem, but it still happens to me using edgy.

---

### Post by saxin on 2006-10-27
Yep, same here! Freezes even when I'm using Edgy..

---

### Post by viz_e on 2006-10-28
In my case the source of freeze was the xorg memory leak. After the edgy upgrade, xorg uses always a lot of memory (more than 100Mb) and processor (5%-10% constantly), but the system is now much faster and (wait for it...) xorg's memory is also freed from time to time!!!

For the guys reporting edgy's freeze, do you know the general cause?

---

### Post by towsonu2003 on 2006-10-28
I think Edgy enables composite by default. try disabling it in the xorg.conf...

---

### Post by viz_e on 2006-10-29
> I think Edgy enables composite by default. try disabling it in the xorg.conf...

Yes, right after the installation of the system, xorg was using a *huge* amount of memory and kubuntu was slow. After I discovered the composite option enabled, I disabled it and since then the system works flawlessy. I think this only applies to ati-guys, because of an incompatibility of ati drivers and DRI, right?

---

### Post by eeefresh on 2006-10-29
Well I never was able to fix the freezing problem in Dapper, but I have gone four days now in Edgy without a freeze.

*Keeping fingers crossed*

---

### Post by Bill Gatz on 2006-11-13
I have had a hell of a time with this.  I had quad booting system on my Asus mobo PIV, 2Ghz with 2 SATA drives and ATI 9700.  I believe it was Fedora 4, Mandriva, Mepis and SuSE.  (I'm not sure, I have another multi-boot machine and I have been doing so much landscaping work around my home this summer that I haven't been doing that intensive "no life, I'm in the computer room" thing for a change.)  

So I wiped the drives of the machine above, and for some reason, I couldn't install ANYTHING on it!  I couldn't remember doing anything special before, but I absolutely could not install (from Linux Format mag DVD's) Gentoo, PC Linux, Ubuntu and something else.  I was sure it was the SATA drives, and I would have given up, but I found a whole lot of help here, and I kept adjusting the BIOS.  Funny thing is, turning off the ACPI didn't help me at all.  I did try several combinations, and someone else mentioned turning off 2.0 support, and that worked for me, it finally loaded.   

So I was happy until the freezing...  I agree that some web pages seemed to make that happen instantly, but it also did so did using Thunar, when going to the menu bar.  And of course, I could not back up DVD's, which I wanted to try to do to get away from Winderz.  After 3 tries, it went to the hard disk, but would not finish a burn.  

Anyway, I went to ATI and got their install package, and so far, it has worked much better.  Got a DVD to the hard drive and then copied with no freeze, left the computer and worked more in the yard (for hours), came back and it was up and running!!  I was really surprised.  So it is still real early in the test, but even so, it seems like it is fixed.  I am going to be brave and try to burn another disk now.  

And yes, I remember reading that some people went days before they had a recurrence.  I will report (like everyone else) if that happens...

Meanwhile, I'll try to give it a good workout with as much of a stress test as I can think of.

I see that I mentioned above turning off ACPI didn't work, then I said I turned off ACPI 2.0.  I had 3 ACPI options, and I tried different combinations.  I left 2 of them on, so all I ended up turning off was the 2.0 part.  And now I see that I have a problem where an app might freeze, but I can still move the mouse, and I can call a terminal and run "TOP".  That is a huge improvement, as my only option previously was to hit the "OFF" button for 5 seconds.  And xorg didn't seem to be hogging too much processor time, so when my DVD copy to hard drive froze, instead of rebooting, I just killed that and am now trying again.  It is over half done, and whatever happens, I agree with the later opinions of this who say that there are variations of the problem, and different symptoms depending on what hardware you have.  I am sure I could use another 512 megs of RAM (I currently have 512 and left that out above), but you can usually get away with a lot less of everything on a modern Linux distribution, as opposed to Winderz specs.  I have noticed that my DVD playback is uneven, though not choppy, (that is, there is slight hesitation that is noticeable), more RAM seems as if it might fix that.

I have been wanting to install some software to WINE as I am anxious to get the hell off of the *other* OS, but I think I am going to hold here until this whole problem gets resolved.  I used to use Mepis as my main/favorite Linux (and I will dual boot with it if I can get it installed), but I made my dad a Linux box with Ubuntu and I need to make sure I have one running the same distro.  His is only a P III and it has no problems like this at all.  (And I forget what all else is on it, sorry!)

---

### Post by towsonu2003 on 2006-11-14
> **Bill Gatz said:**
> I made my dad a Linux box with Ubuntu and I need to make sure I have one running the same distro.  His is only a P III and it has no problems like this at all.  (And I forget what all else is on it, sorry!)

you could install a distro that works better for you and use vmware player to have the distro that your dad runs. just an idea :)

---

### Post by altaaa on 2006-11-14
I managed to narrow down my freezing problem.

Some pages back i stated that without beryl (compiz), i was running stable... well, i was wrong.... In the mean time i tried out fedora 6 and suse 10.1; only suse was running somewhat stable. but suse aint ubuntu :)

so, back to ubuntu. now i noticed that if ubuntu freezed, top would display a cpu usage of around a 100% on the 'wa'-counter. man top gave me this:

[FONT="Courier New"]wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.
[/FONT]
Furthermore, i was getting this message on my console:

[FONT="Courier New"]hdb: cdrom_pc_intr: the drive appears confused (ireason = 0x02)[/FONT]

I physically removed my cd rom drive, and ubuntu was stable for the entire night.

I added the rmmod ide_cd and rmmod cdrom commands to my /etc/rc.local, so my cd drive is now completely unusable in ubuntu. no modules loaded, and so far it has been stable. And now I'm gonna test it some more.

Update: it's been 5 days now, haven't had a single lockup....

---

### Post by Tyltyl on 2006-11-22
> **altaaa said:**
> 
so, back to ubuntu. now i noticed that if ubuntu freezed, top would display a cpu usage of around a 100% on the 'wa'-counter. man top gave me this:

[FONT="Courier New"]wa  --  iowait
          Amount of time the CPU has been waiting for I/O to complete.
[/FONT]


How did you discover that? To me when I get a freeze I can't do anything at all. How can I do the same for me?

---

### Post by altaaa on 2006-11-22
Before logging in to X, do a CTRL-ALT-F1 and log in to the terminal. Then log in to X with CTRL-ALT-F7, then go back to the terminal, open top and just wait...

That did it for me.

But my system didn't freeze, it just got a 100% cpu usage. It's quite possible that, if your system freezes completely, top won't give you any leads.

btw; still stable! :)

---

### Post by isitututu on 2006-12-15
> **towsonu2003 said:**
> I think Edgy enables composite by default. try disabling it in the xorg.conf...

I had similar problems. Xorg was using 50-90% processor resource. Once I disabled composite it seems to work fine. To disable I added the following to /etc/X11/xorg.conf

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

---

### Post by MkfIbK7a on 2007-02-23
> **eeefresh said:**
> I feel your pain, Tyltyl.  The Ubuntu community is typically very helpful, but I think everyone is stumped by this issue.  I haven't filed a bug report, but several others have.  Until someone finds a fix that actually works, I'm sticking with Breezy Badger.  It works flawlessly for me, though I can't use the latest version of AmaroK.


Hopefully this issue won't resurface in Edgy.

too late im having the same problem!

700Mhz AMD not 64bit

nVIDIA GeForce 2 Pro 

ubuntu edgy fresh install

gateway broadcom wifi card

western digital 40gb HD

my comp periodically locks up while i am using a web browser i find this extrememly :KS :KS :KS ANNOYING!!!!

---

### Post by jlh on 2007-02-23
This worked to stop my freezes.  I'm running Ubuntu 6.06 on a Thinkpad T30 w/ATI Radeon
Mobility 7500.

Modify /etc/X11/xorg.conf file.

Around the lines that look like this:
============
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M7 LW
[Radeon Mobility 9000]"
Driver "ati"
============

Insert this before "EndSection":
============
Option "RenderAccel" "0"
============

---

### Post by MkfIbK7a on 2007-02-24
ok this seems to have worked for me the reason i hadnt tried this before is that my nvidia geforce 2 pro didnt alow gl after removing renderacell however that seems to have been fixed ill keep this updated

---

### Post by MkfIbK7a on 2007-02-25
thx so much for the solution i havent had an issue in a while!


will keep you posted

---

### Post by MkfIbK7a on 2007-02-25
still crash free!!!

---


---
title: "Dell 1525 Crashing Randomly"
date: 2008-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ggerules on 2008-08-29
First of all I want to say it is *very* cool to have my new Dell 1525n laptop running ubuntu 8.04 pre-installed from the factory.  Now onto some problems that I am having.

I purchased this Dell 1525n directly a month ago from Dell's online site and it worked out of the box no problems.  A couple of weeks ago I started having random crashes.  I have done all of the software and security updates through the update manager.  Yesterday the laptop crashed three times in an hour.  So I used the feature where upon boot up you can reinstall the factory default Ubuntu OS that came with the laptop.  That reinstall wiped the disk and the system booted up fine with the factory default OS.  So the first thing I did was do an update to get the system up to the latest.  In the middle of that down load the system crashed again.  I rebooted the system logged in and the system crashed again.  By crash what I mean is that the screen goes blank and no key board action makes the system do anything.  The only thing that I can do is hold the power button down for 4 seconds to shut the system off and then turn it on again.

What am I doing wrong!?  I really want to make this work.  I really like Ubuntu and would love to get this going on this laptop.

Thanks in advance,
George

P.S. Here is some technical info on my laptop from when I purchased it.

Intel Core 2 Duo T7250 (2.0GHz/800Mhz FSB/2MB cache)
4GB Shared Dual Channel DDR2 at 667MHz
Glossy, widescreen 15.4 inch display (1280x800)
Intel Graphics Media Accelerator X3100
250GB SATA Hard Drive (5400RPM)
Ubuntu 8.04 with DVD Playback
Integrated 10/100 Network Card
CD / DVD Writer (DVD+/-RW Drive)
High Definition Audio 2.0
Wireless Intel 3945 802.11a/g Mini-card
Integrated 2.0M Pixel Webcam
85Whr Lithium Ion Battery (9 cell)
Dell Wireless 355 Bluetooth Internal (2.0 + Enhanced Data Rate)

---

### Post by ggerules on 2008-08-30
The system is still crashing.  I am begining to think I made a mistake buying this system.  

Is there some information that I need to post to get some help?  I would love to get this solved.

George

---

### Post by linux_tech on 2008-08-30
Random system crashes out of the box could indicate a hardware problem.
Memory, hard drive, systemboard, etc.  Try to clear some of the hardware   

Using the Dell Diagnostics- Run extended test
[http://www.cs.utexas.edu/users/deke/laptopsupport/manuals/d600/diag.htm](http://www.cs.utexas.edu/users/deke/laptopsupport/manuals/d600/diag.htm)
Dell diags can be launched either from the cd that came with the computer or by doing the following:
Turn on the computer. When the Dell logo appears, press <F12> immediately.
When the boot device list appears, highlight Diagnostics and press <Enter>.

Run a memory test 
[https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)

How to Run the Hard Drive Disk Self Test (DST) on a Dell Computer
(RESOURCE CD) support.dell.com
Run the Disk Self Test (DST) from the Resource CD

Assuming the hardware passes all the tests then run the following
from the terminal and post output.
```
dmesg
```
```
lsmod
```
```
lspci
```
```
sudo lshw | less
```
```
sudo dmidecode
 
```
More useful diag tools but you need to install them-
```
sudo apt-get install sysstat
 
```  then run iostat -ostat(1) - Linux man page for more info - [http://linux.die.net/man/1/iostat](http://linux.die.net/man/1/iostat)
```
sudo apt-get install x86info

``` then run x86info
```
sudo apt-get install ipmitool

``` then run ipmitool

Download the ultimate boot cd for more diag tools-
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by ggerules on 2008-08-30
Thanks!!!!!!

I am in the process, as we speak, of reinstalling 8.04 on the drive this time from the Dell re-install CD.  When that process is complete I will run the diags and post the output.

I have been running Debian on a server with no problems since 1999.  This is my first Linux laptop experience.  I am highly motivated to make it work, so thanks for helping out.

George

---

### Post by ggerules on 2008-08-31
Ok......  First, thanks linux_tech for your help!

Second, I ran MemTest and the Dell diagnostics, the ones that were embedded in the BIOS.  All tests came back with no errors.  So I am less convinced that it is a hardware problem.

Third, I performed a fresh re-install of 8.04 with what was offered through Grub.  

I have attached the following output as requested above in the archive file.

One interesting thing is that I can get the system to crash in fairly short order when I run the 'sudo lshw' command.  Once I type in the command it will output 'PCI (sysfs)' and hang in the terminal.  If I close the terminal and rerun it in another terminal, the screen will shortly go blank and I have to reboot the system.  I am not sure if it related or not.

Thanks in advance for your help!
George

---

### Post by ggerules on 2008-09-01
So I down loaded the dell 8.04.1 iso install and installed in on my 1525n with the idea that what was on the install partition was different from what was issued through the online iso.  I didn't work.

I installed the 8.04.1 iso dell install cd.  No problems.  I logged in with the pristine istall.  And I did the up date as suggested by the update manager.  360+ updates were installed.  I rebooted the machine.  Logged in and just let it sit for 6 hours.  When I can back.  The screen was blank.  The system was frozen.  

What am I doing wrong!?  Did I make a mistake in purchasing this 1525n laptop with linux?  Help!!!!!! I don't want to be remote testing for Ubuntu and Dell.  I want to do some work!  This is just sucking up way too much time! 

George

---

### Post by bigbrovar on 2008-09-01
i completely feel your pain .. i dont use dell and i can offer little help .. since u seem to be the only one having this problem .. my guess is that it might be a hardware problem ... i have used 5 different laptops with ubuntu and i haven not had problems with it .. perhaps u would not be soo much in a worry to update .. next time u reinstall your system .. or u could use the default ubuntu cd not the dell iso to do a clean install of the system .. sumtin times things like this happens even with windows or mac .. sorry i wasnt of much help :(

---

### Post by ggerules on 2008-09-01
Thanks BigBrovar.  I appreaciate the thoughts.

I just want this to work so I can work.

George

---

### Post by Dougie187 on 2008-09-01
I am not sure about this, but I think the dell version of 8.04 has specific hardware drivers built into it so you don't have to configure it. Where as the one that you download from the ubuntu site might not have this support by default and therefore might not work out of the box.

As for your issue, Did you issue return after a fresh install of the Dell version of 8.04?

I read through your output files and don't see any clear issues. If you can, next time that it randomly freezes and you go to turn it on, save the output of dmesg after you log in by doing something like this
```
dmesg > ~/DMESG.OUT
```
That way you will get a file in your home directory that has all the information.

It only really helps if it's after a freeze because then we can see the error. Because these logs get "refreshed" everytime you reboot your computer.

---

### Post by ggerules on 2008-09-01
Thanks Dougie187! 

My first re-install was with the ubuntu version, 8.04, that was part of the option, through grub, on the hard disk.  

The second re-install was with the re-install CD I created through an option on the desktop.

The third re-install was with the DVD iso image 8.04.1 that I downloaded from the Dell linux web site.

For all of these options the system would run for awhile and then the screen would go blank, the keyboard would go inactive and I would have to do a hard reboot.

I tried various permutations of the above both with with leaving the system standing no updates through the update manager and with all of the updates through the update manager.

So...... What I'll do, as part of your suggestion, is wait for the system to freeze again and then type the dmesg command and post the output.

Thanks again for your help!
George

---

### Post by Orphee on 2008-09-01
Hi there, I have a Dell Inspiron 1525 (bougt with vista)
I installed Ubuntu 8.04.1 and I have to say I randomly have the same problems as you have...
I noticed I have less problem since I disabled Compiz...
Randomly my computer hangs... but no blank screen... I have my screen locked, I can move the mouse... but keyboard doesn't respond, click doesn't too... I must 'hold the power button down for 4 seconds to shut the system off and then turn it on again'

My first thaugt was the system completly hangs... but it's not !

I discovered the system is still active ! because I can connect to it with SSH from another computer ! Daemon still run, like HellaNZB ! ...
My Computer didn't hang since a few days, but when it will (because it will happen) I will try to check errors, and try to remotly kill GDM and X...

Could you please try to check about SSH remote controle when you PC hangs ?
Thanks !

---

### Post by ggerules on 2008-09-01
Hi Orphee,

That's a great tip!  Thanks.  I have had an up time of something like 6 hours with no system hangs.   I am waiting.........

George

---

### Post by ggerules on 2008-09-01
Hi,

Here is the dmesg output. 

The system crashed I did a hard reboot logged back in and typed

dmesg > dmesg1.txt

The attached files are from actually two freezing instances tonight.  So, there is dmesg1.txt and dmesg2.txt in the archive file.  

If there is any other output that would help in diagnosing this problem, I would love to know.

Thanks in advance,
George

---

### Post by ggerules on 2008-09-02
How do I go about finding errors with either PCI timing or with GDM video problems?

Thanks 
George

---

### Post by Orfintain on 2008-09-03
I have a Dell 1525 N it came with 7.04 , Now it's running on a hardy disk I downloaded and burned I haven't had any trouble..

(well i'm trying to fix the media keys and the secondary audio out at the moment, but those are fairly minor)

Though since yours came with 8.04 preinstalled it may have different firmware, (there is a dell ubuntu wiki...){you might try alternate firmwares... from said wiki)

Good luck

---

### Post by ggerules on 2008-09-03
Hi Orfintain,

Thanks for the reply.  The Dell bios version is A13.  I checked Dell's web site and it is the newest version.

Thanks again for replying! 

Any help no matter how little is *much* appreaciated.

Thanks,
George

---

### Post by ggerules on 2008-09-03
Hi Orphee,

I installed ssh on the laptop so I could ssh into the laptop from another computer.  I could ssh into the laptop until it froze.  The message I got was that destination was unreachable after it crashed, where it was reachable before it crashed.  Hummm...... Any thoughts on what I might try next?  This is frustrating......

George

---

### Post by Orphee on 2008-09-03
Hum, if SSH doesn't work after the crash for you, we don't have the same problem :(
Don't know how to help you, and me, sorry

---

### Post by ggerules on 2008-09-03
Thanks Orphee,  I will continue on in my search for a solution.
George

---

### Post by nwilliam3 on 2008-09-04
I've been having the same problem for the last few weeks. I can't prove it, but it seems to be linked to the 2.6.24 kernel. I just started to use the 2.6.24 series a few weeks ago. A newbie mistake had me using an old kernel and I didn't even know it. If I use that older kernel I have (2.4.22) I have no issues at all. 

I have also noticed with the 2.6.24 series that there are some webcam issues too. I was actually out here looking for a solution to that to see if it fixed my freeze issues. If I figure anything out, I'll post back here. I was going to do a fresh install to see if that fixed the issue, but based on your experience I'm going to hold off so that I don't lose my old kernel.

---

### Post by mark on 2008-09-04
Hi - my original 1505n was replaced by Dell with a 1525n (a video problem they couldn't find/fix).  I noticed random lockups occurring and I started playing with stupid stuff - and found that, when I changed the screensaver from "Random" to "Blank screen" - it didn't lock up anymore.

This was so bizarre I haven't filed a bug report - but give it a try and let me know if it works for you, too.

Thanks,

Mark

---

### Post by ggerules on 2008-09-04
Thanks nwilliam3! 

Are you having the same problem where you can't ssh into your box from another computer?  What window manager are you using?

George

---

### Post by ggerules on 2008-09-04
Thanks Mark!

Early on I too was checking out the screen saver stuff too.  I was getting crashes whether the screen saver was on or off.  Right now it is set to blank so I could eliminate the possibility that there might be a bug some random screen saver.

Thanks, George

---

### Post by linux5uper on 2008-09-04
Sorry I can't offer any help. I don't know what your support with Dell includes, but if I were having this problem, I would try to return/exchange it or deal with them directly instead of troubleshooting for hours/days. Isn't the whole point of buying Dell Ubuntu that it should 'just work'? My HP laptop came with Vista and there were no guarantees about linux, yet it works perfectly.

---

### Post by Zakhafr on 2008-09-04
How long did you run the memory test?

I'd suggest, if you see your PC crashing every 6~12 hours of continuous usage, to let the memory test run for 24h.

I had a laptop (LW) were the memory was upgraded and it did sort of the same thing with Linux with that memory chips.
Xp seems to be less demanding on memory, it crashed only now and then (but anyway, it's so obvious that Xp crashes some times :), it could have been "normal" XP crahes).
Vista is worse !.. If you do not have the exact correct memory timers it goes crazy. One of my colleagues had that, and when he changed the memory chips everything ran perfectly. Don't ask me why :confused:

---

### Post by bigbrovar on 2008-09-05
i dont know if this would help much but i can try installing ubuntu-studio packages in synaptics .. just open synaptics search **ubuntu studio** and install everything u see from the result .. one of the stuff that would be installed is a unique rf kernel (tweaked for audio and video production performance) which some pple have reported to be more stable and stops some random freezing often experienced with the generic kernel that ships with Ubuntu .. if it works u can then use it and uninstall the extra packages u didnt want ..

---

### Post by ggerules on 2008-09-05
Thanks!  

These are all are excellent suggestions.  

Zakhafr, The first time I ran memtest I did it for two iterations.  I think I am going to run it for 24+ hours.  Thanks!  I should have let it run for more time.  

bigbrovar, I don't know much about the ubuntu studio, but I am going to give it a try after the memtest. 

linux5uper, I kinda feel like I need some "hard" data, like an error code or something like "If I do X task, then it crashes".  But I may be to hopefull.  There are a lot of variables at play.

Thanks everybody!!!!! 

George

---

### Post by bigbrovar on 2008-09-08
Any luck?

---

### Post by ggerules on 2008-09-08
Still working at it.  I had to go away for the weekend and I left MemTest running on the laptop.  It is now 72+ hours with 85 passes and there are no errors.  I am going to shut it down and look at possibilities as to why it is locking up.  I guess I am going to try and find other possibilities.  Hummmm..... there is a solution out there somewhere.

Thanks,
George

---

### Post by ggerules on 2008-09-08
Ok, So I left MemTest on a little longer than I said in the last post.  Just to see if something would pop up.  The good news is finally I got some hard evidence that something is up with the hardware.  The bad news is that I have to send the laptop in to get it fixed.  Yuck!

Thanks to all that lent their support and help!  

I have attached a picture of the error.

Thanks again!
George

---

### Post by bigbrovar on 2008-09-08
Am glad that if seem to have tracked down the cuase of the problem .. hoep u get your laptop back in no time so that u can get to use it for what u bought it for .. cheers

---

### Post by ggerules on 2008-09-08
Hi,

I have just spent 2 hours in a Dell support chat dialog.  He was courteous but seemed to me stuck in a help support script.  This stuff is taking up a lot of time.  The gist of it is that even though I have a memory error with the Dell supplied MemTest 1.70.  They need to reproduce the error with a "Dell" utility to find out which memory bank has the error in it. Hummm ... couldn't they find out that from the error address and map it to the chip dimm in question?  

Does anybody know of a Dell "Ubuntu" hardware support group, or is it just a Dell "Windows" hardware support group trying to support Ubuntu users on hardware issues.

Any thoughts out there or experiences that could help me with my situation?

I have attached a conversation.  I have a few misspellings in my chat conversation.  Sorry. 

George

---

### Post by bigbrovar on 2008-09-08
this sucks mehn .. i would have thought that dell would have a support term dedicated to their Ubuntu laptop  .. i plan on getting a dell Ubuntu but this scares the hell out of me .. 

i think your best bet would be to send the system back to dell for repairs .. where did u get it from .. maybe you should take it to the local dell repair outlet near u .. or better still u might want to wait for his call lets see what he has to say .. did some search and i found this [http://www.dellcommunity.com/supportforums/board?board.id=sw_linux](http://www.dellcommunity.com/supportforums/board?board.id=sw_linux)  hope it helps ...

---

### Post by ggerules on 2008-09-08
Hi,

It took a while, but they are sending me new memory for the laptop.

I learned many things out of this process.  1) Be persistent.  2) Don't think that Dell Tech Support guys know errors that come from a Ubuntu laptop.  3) There are differences between the Windows Dell Diag disk and the Ubuntu Dell Diag disk for the 1525 series computers.

The Dell tech support guys that I dealt with were courteous but most everybody that I dealt with came from a Windows background and there are subtle differences is how diagnostics get done between Windows and Ubuntu.  

On Windows machines the memory test portion seems to be embedded inside their diagnostic disk.  On that disk you can run memtest like features within that environment.  On Ubuntu machines the Dell diagnostic disk, the one that I downloaded from the 1525n Linux support page doesn't have memory testing on it.  I guess memory testing is done through MemTest86+ as a load option through GRUB.  

The first couple of Tech support guys that I talked to didn't know what to do with the memory error address location as seen from above.  In fact they didn't even want to see the photo of error that I posted earlier today.  They wanted to know which memory module bank had failed.  And that error would be displayed through a Dell Diagnostic Disk or through the Pre-Assessment Boot test.  This led to endless rounds of Pre-Boot System Assessment memory tests which all passed.  All of this led to conversations like, "We don't think it is a hardware problem".  

At one point I was sent to General Ubuntu phone support at which after I explained the error message and they said it was a hardware problem.

I was given a number by Dell Tech support guy named Chris, who was pretty helpful, to the Dell Ubuntu Hardware Support, 866-622-1947.  I explained the error message and he said I needed entirely new RAM.  So off I go back to the regular tech support guys who wanted me re-seat the memory chips and to re-run memory tests, they said it would only take 15-20 minutes.  I had to re-educate this guy that this was a random memory problem and it might not turn up in this test and that it took 72 HOURS to have this memory error to turn up.  He wouldn't let it go.  So I said, so what you are telling me, is that I might have to run more memory tests and ones that might take up to 3 days to run?  I explained to him that I am completely done in trying to to resolve this.  I have an error on the memory installed in the computer, I am through running memory tests, I need to have the memory replaced.  What a frustrating experience!

George

---

### Post by Orfintain on 2008-09-08
congrats , yeah they don't really have their support together right for Ubuntu yet gotta buy conical or these forums. I tried to get lin dvd (comes with the pre installed linux set up but you can't get through the repo's and didn't come with a back up disk.. i eventually gave up after talking to 6 different people who said the next one would be able to help me , ubuntu windows tech and back and forth again

---

### Post by bad luck on 2008-09-08
hi ,
i registered in this forum in the name of bad luck just because  i had a bad luck buying this Dell inspiron 1525 n series and i am living in the bottom of the earth with no support,,,
i am having the same problem of ggerules???????
damn ubunto

---

### Post by bad luck on 2008-09-08
help me with blue error screen that made me sad, depressed, fool, suffering, >>>>>>>>>

---

### Post by bad luck on 2008-09-08
i formatted the system , installed windows XP , and the same problem , blue error screen

---

### Post by nwilliam3 on 2008-09-09
George,

Sorry I haven't gotten back to you, I kind of forgot this was out here. It sounds like you've made some progress, despite your frustrations.

As for your original question to me. I don't use ssh and frankly I'm not even sure how to use it. If you want to send me some instructions I'll give it a try.

I have noticed that I don't seem to have the crash issues when I'm in KDE 4.1. I playing in there a couple of weeks ago and everything was fine. When I went back to Gnome, I had the crash issues again. 

I'm pretty sure my issues is with the 2.6.24 kernel. I don't have any issues with the 2.6.22 kernel. The 2.6.24 kernel starts slow, I don't get the normal Ubuntu Load screen, and my volume is noticeable lower for some reason. Since I don't need to be in the 2.6.24 kernel unless I'm running VirtualBox I'm probably just going to wait and see if the new kernel with 8.10 will fix some of these issues.

---

### Post by ggerules on 2008-09-09
Hi,

Dell send the 4GB of ram next day.  I got it this morning.  Ran the Pre-Assesement Boot test for memory.  It passed.  Then I booted up Ubuntu 8.04 with the 2.6.24-19.41 generic kernel.  It hasn't crashed all day!  And usually it would crash at least once a day.  

Thanks to all that helped!
George

PS I post back later this week with a progress report.

---

### Post by ggerules on 2008-09-29
Hi,

Here is a report on how my laptop is working after the replacement memory from Dell.

The laptop still crashes on average about once a day.  The interesting thing is that it will crash only once, usually withing the first hour of use, then works pretty well for the rest of the day.  I am getting use to this behaviour but I would love for it to not crash at all.  

I did install KDE3 and that seemed to help, but right now I am lacking hard evidence.  

It feels like some kernel issue. Has anybody loaded some of the newer kernel?  What have been your experiences?

George

---

### Post by ggerules on 2008-12-05
Hi everybody,

It has been a number of months since I have posted on this topic.  Thanks to everybody who has helped me.  This particular post is a status update to help people that have had problems similar to mine.

So over the past few months since the last post, my system even with the new RAM, was still crashing about 2-3 times a day.  In other words, I would be working and the screen would go blank, the keyboard would go unresponsive and I would have to do a hard reboot. 

Well about 3 weeks ago the system took a turn for the worse.  It started crashing multiple times in an hour.  I have kept up with all of the updates I could.  So I thought it was a bad update or something.  I decided to reinstall ubuntu (again!).  During the install, the system crashed.  I ran the diagnostics in the POST test and that crashed too!  No error message or error code.  

I called the dell tech ubuntu support help number and while on the phone describing the problem the system crashed again.  The dell tech support guy said the laptop should be sent in to have it checked out. 

Two weeks pass and I get the system back and it is working like a charm.  It hasn't crashed once!  It turns out that the mother board was bad in the system.  

Now here is the kicker.  I decided to install emerald windowing decortor that runs on top of the compositing windowing manager compiz.  That has been working great with all of the cool desktop effects even though compiz has blacklisted the intel 965 graphics chip set.  

I hope this helps in some small way,
George

---

### Post by openprivacy on 2009-02-03
Last April I bought my wife my wife a Dell 1525 via the Dell online storewith factory installed Ubuntu 8.04.  As her personal sysadmin ;-) I've kept it up-to-date via the update manager.  She's not made any major configuration changes, and uses Firefox, Thunderbird and OpenOffice for her writing.  She doesn't travel with it - it stays on her desk.

Since we bought it, it would very occasionally (a couple times a month) lock up to the point that I can't SSH into it.  That's happening more frequently now - today happening four times.

Upon reboot, there are no messages left in dmesg, system, messages, kern.log, debug, daemon.log or Xorg.0.log which leads me to believe that this is a hardware problem.

I'll try running some of the diagnostics suggested by linux_tech on 30 August but there are a lot of them and my wife and I both work about the same hours, so finding time to run them will be tough.  Suggestions as to which to run first?

How do I "prove" that it's a hardware problem and deserving of a replacement under warranty?  Sending the system in means my wife won't have a machine during the time that it's in the mail and being repaired.

We bought her a Dell as we wanted a solid machine.  Her previous machine - a Thinkpad that she had for 7 years - was a rock, especially after I wiped Windows and installed Xubuntu on it.

(Oh - just noticed my profile: my personal home-built desktop runs Ubuntu 8.10, but I've never updated her Dell 1525 from 8.04 as I wanted to keep her system vanilla.  And while typing this message, I was ssh'd in to her machine when it locked up - and the ssh session was also frozen.)

---

### Post by abn91c on 2009-02-03
> **ggerules said:**
> So I down loaded the dell 8.04.1 iso install and installed in on my 1525n with the idea that what was on the install partition was different from what was issued through the online iso.  I didn't work.

I installed the 8.04.1 iso dell install cd.  No problems.  I logged in with the pristine istall.  And I did the up date as suggested by the update manager.  360+ updates were installed.  I rebooted the machine.  Logged in and just let it sit for 6 hours.  When I can back.  The screen was blank.  The system was frozen.  

What am I doing wrong!?  Did I make a mistake in purchasing this 1525n laptop with linux?  Help!!!!!! I don't want to be remote testing for Ubuntu and Dell.  I want to do some work!  This is just sucking up way too much time! 

George
I have a friend at work that just went thru the same problem with hers, she had extende service so they came replaced her RAM and mother board, still no joy. She sent it back to dell and it was what I suspected the problem was, it was the MLB-mother load board( the hole where the AC adapter goes in).You need to send it to dell

---

### Post by openprivacy on 2009-02-04
Just rebooted, hit F12 and started the Diagnostics.  It ran through the first set fine, then a dialog came on the screen that said:

[INDENT]No problems have been found with this system so fr.  Do you want to run the remaining memory tests?  This will take about 30 minutes or more.  Do you want to continue? (Recommended) **Y**es or **N**o[/INDENT]

Anyway, at this point I think the machine froze again.  It won't take a 'y' nor a 'Y' nor does TAB or arrow button make anything happen.

The top of the machine says:
[LIST]
[*]Pre-boot System Assessment Build 4108
[*]Device: Hard Drive
[*]Test: DST Short Test
[*]Status:
[*]Percent Complete: 0
[/LIST]

but this test may have passed, just not recorde at the top, since at the bottom of the screen (behind the dialog) I see
[LIST]
[*]** Hard Drive - DST Short Test **
[*]Test Results : Pass
[/LIST]

I'm going to let it be for a while longer (it's been in this frozen state for 20 minutes now) but if nothing changes, I'm going to call DELL Support in the morning.

[SIZE="1"][LIST]
[*]Machine: Dell Inspiron 1525
[*]OS: Ubuntu 8.04 factory installed; fully up-to-date
[/LIST][/SIZE]

---

### Post by openprivacy on 2009-02-04
Let it sit frozen in the diagnostics (above post) for an hour.

ENTER and even ESCape dit not pull it out.

Ran the memory tests (MemTest86+ v1.70) overnight - 7hrs 10 minutes, 15 passes and they're still running.

As people have suggested above, this is looking like a motherboard problem.  I'll be calling Dell soon and finding out how long it takes to navigate their phone menu tree.  I'll report back with my experience.

---

### Post by openprivacy on 2009-02-04
Called Dell support, they re-routed me to Dell Ubuntu support - direct number: 866-622-1947

Talked to Mankiran (a woman; kinda funny as I talked to Kiran, a man, at (Windoze) tech support) for 15 minutes.  Despite the fact that the diagnostics froze indicating a hardware - probably a motherboard - problem, she wanted me to re-load the OS.

As the system froze during diagnostics (see a few posts back) I don't want to do this busy work as if the system freezes during an install it could become 100% unusable.

Mankiran said she's call me back in 2 hours - I'll post what happens then.

---

### Post by ggerules on 2009-02-04
I fee your frustration.  I dealt with my laptop crashing multiple times a day.  

Unfortunatly the diagnostics that came with the laptop didn't find the problem with my laptop which was a bad mother board and memory.  But, below there are some tips in dealing with Dell tech support. 

The key for me was to find out if I was talking to a Windows support guy or a Ubuntu support guy. Be forcefull and get the phone number to the Ubuntu support guy.  You will be wasting your time talking to the Windows guys. 

Here are some additional tips that I had to find out the hard way.
- If you call in with the phone, be prepared to sit in a phone queue for 20+ minutes.  Once you are talking with them they will want you to run any test possible and get off the phone as fast as possible.  It took 2 and a half months to get my laptop fixed.
- Get a case number and use that when talking to the support guys.
- Use the online chat feature, you will get faster response.
- Get the Dell Ubuntu support number and call that direct. Don't call the regular support number. It will be a bunch of windows guys.  If you call canonical support they will also have the Dell Ununtu support number.  
- Get the Dell "bin" file that has the latest memtest on it. They should give you a link to down load it. The one installed that came installed on my extra hard drive partition was pretty out of date.
- Make sure the RAM is seated properly. They will ask you to do that at some point in your fix-it journey.
- If your laptop is like mine, the graphics chip that is on the mother board was black listed by the compiz compositing window manager people. So you might want to change from compiz to metacity.  In my case it didn't make a difference, the laptop crashed.  On a side note, once the mother board was changed out, the laptop has been solid as a rock. I have been running compiz with emerald and most of the goodies turned on. 
- Make sure your BIOS is up to date.
- Make sure you have all of the updates installed.
- If you suspect it is a hardware issue even if you have run all of the tests they have suggested, be forcefull, but nice, and get the laptop in for warantee hardware check up.  They will send you a box for shipment. It took around 2 weeks for the mother board to be replaced and sent back.  What finally got me the ok to send the laptop back in for repair was that while I was on the phone with the Dell Ubuntu support guy, the laptop crashed on reinstall of the OS while he was on the phone.
- It may be very frustrating to deal with the support guys but be nice. They have a job where they deal with negative frustrated people all day long.

In summary, run as many of the test on you own before talking with them. It will save time.  Talk to the Dell Ubuntu support guys.  If it is a potential hardware issue, get the laptop looked at!

I hope this helps.
George

---

### Post by captinkid on 2009-02-05
I feel your pain, I am working on a friends 1525 and it freezes constantly. This one appears to have a hard drive problem, and I think it also has a virus. Is the home basic edition considered a virus? 

I am starting to think that the entire 1525 line needs better QA.

Matt

---

### Post by heapy on 2009-02-06
hi there people..
i have had a read threw all these posts, and i too feel the pain lads. my dell 1530xps locks up all the time running ubuntu hardy, and vista ultimate 32bit.

using linux, it just seems to randomly hang the mouse kinda lags and 10 secs later completely locks up. only a hard shutdown as an option to turn off. 

in windows, instead of just locking up, it BSOD with a stop: 0x00000101. 

Dell replaced the motherboard, twice! and still the same results. not fixed yet, im absolutely gutted. 
Have ran memtest86+ for 12hrs with no errors, it can only be a cpu fault ???

much love x

---

### Post by openprivacy on 2009-02-10
Update: Dell replaced the motherboard and now, instead of crashing (freezing up) every couple hours, it's doing it every couple days.

Progress, but not good enough, of course.

The Dell guy left me a replacement drive - I have to return one of them within 10 days - so next I'm going to back up everything and re-install - probably with the new Dell 8.10 disk I just downloaded from [http://linux.dell.com/files/ubuntu/intrepid/iso-images/ubuntu-8.10-dell-reinstall.iso](http://linux.dell.com/files/ubuntu/intrepid/iso-images/ubuntu-8.10-dell-reinstall.iso)

What a pain.

Hopefully that will fix things.  I also ran memtest one night for 8 hours with no failures.

If after the drive replacement (and upgrade from 8.04 to 8.10) I'm still getting the crashes, I guess I'll try returning it to the depot for a complete going over (even more of a pain as I'll be without the machine for 10 days or so).

Good luck to all - I'll keep you all informed as to how things go with my machine.

---

### Post by banyan.peepal on 2009-02-19
I have Inspiron 1525 which originally came with Vista. I dualbooted it with Ubuntu 8.10 through grub. Almost everything is working right except that the system hangs sometimes and I am left with keyboard and touchpad frozen and two leds for capslock and scrolllock blinking simultaneously.
As a result I havve to shut it forcefully by pressing the power button.

Any help in this direction would be highly appreciated. :(

---

### Post by ggerules on 2009-02-19
Are you having these problems on Vista or Ubuntu 8.10?

---

### Post by theozzlives on 2009-02-19
> **banyan.peepal said:**
> I have Inspiron 1525 which originally came with Vista. I dualbooted it with Ubuntu 8.10 through grub. Almost everything is working right except that the system hangs sometimes and I am left with keyboard and touchpad frozen and two leds for capslock and scrolllock blinking simultaneously.
As a result I havve to shut it forcefully by pressing the power button.

Any help in this direction would be highly appreciated. :(

My caps lock, scroll lock, and num lock leds don't work. Didn't realize I had them until you said something. Outta get that looked at.

---

### Post by banyan.peepal on 2009-02-20
these problems occur only with ubuntu. Vista does not crash randomly.
;)

---

### Post by gusanto on 2009-02-20
Hi all,
I have a randomly freeze problem on my Ubuntu 8.10 running on Sony Vaio VGN-NR120E.  I never had this experience before when running Ubuntu ealier version. The symptom before the system completely freeze is usually by slowing down the performance.  Memory and CPU usage looks normal. (Note: I disable Compiz, I'am afraid if it's the culprit). 
I attached the dmesg file in case it's helpful to identify the cause (and hopefully fix the problem). I split up the file into 4 to make them possible to upload.
Any help is much appreciated.

---

### Post by Orfintain on 2009-02-20
I take you guys have tried hitting the hot key open up a terminal(alt-f2 by defaul maybe) and then 


killall gnome-panel

---

### Post by Stebalien on 2009-04-01
banyan.peepal:
The flashing scrolllock and capslock leds means that you have a kernel panic. This could be caused by the kernel itself or some of your modules (drivers). This happened on my dell and it turned out that it was my wireless drivers (you could try blacklisting yours). You should also try using a non-dell ubuntu (i.e. downloaded from the ubuntu website without the custom dell packages and modules).

---

### Post by ggerules on 2009-04-02
Previous post a wrong thread?

---

### Post by abn91c on 2009-04-09
A friend at work has a 1525 with vista with the same problems, it was  under warranty and they replace the MB and the RAM. the problem persisted, she sent it to Dell and it turned out to be the** MLB**(mother load board), or the hole where the power cord connect to the AC adapter

---

### Post by blurpo on 2009-07-31
I was having this problem (locks up, CapsLock and NumLock blinking) regularly also- normally if I left the laptop on overnight, but it has also happened a few minutes after booting up.

I have run the Dell Diagnostics disk and it tells me to have the disk replaced, but I'm not sure if that is because the disk is for Windows (I don't know which disk I downloaded). I was trying to decide if the problem was serious enough to go through the nuisance of returning it, having to use my girlfriend's Vista for a few weeks and so on (without any guarantees that it will be fixed, of course).

In the meantime I've upgraded to 9.04, run fsck a couple of times (which reports and marks some bad blocks, but nothing serious). And now, knock on wood, the problem seems to have disappeared...

---


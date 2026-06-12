---
title: "Ubuntu is unstable (video)"
date: 2010-09-19
forum: Desktop Environments
---

### Post by tim042849 on 2010-09-19
Using ubuntu 10.04 currently. Workstation is a Gateway GT5422E with
3 gigs of RAM. I have been using ubuntu and slackware since 2007 on
this workstation. All versions of ubuntu that I have used have been
distinctly less stable than slackware. It is not unusual for firefox
to crash, less commonly, ubuntu will drop out of X to the login screen
and less frequently, but disturbly all too often the system becomes
unresponsive and a hard reboot (power-off) is required.

I stress that slackware on the same machine never acts this way. I will
also stress that I have another machine here with ubuntu 10.04 that does
not exhibit this problem. 

I presume that this has to do with the interaction of ubuntu's video
drivers with the particular hardware on this machine. 

I am using the **NVIDIA accelerated graphics driver (version 173)**

I would welcome any and all suggestions, including thoughts on other
forums or MLs that might be better sources to trouble-shoot this problem.
So, if you don't have a solution but may have another source in mind,
please let me know.

:( I get so envious when my wife, friends and colleagues have such great
stability from Lucid.

FYI: Long-time linux user (10+ years). Comfortable with the command line.
Main desktop is gnome, have tried awesome, same problems.
TIA
tim

---

### Post by coffee412 on 2010-09-19
Good Morning, 

I have to say that I have been installing Ubuntu on all kinds of computers from the very cheap (emachines) to some high end HP boxes. I have found the following in dealing with crashes:

1. I have learned that before you decide to install linux on a box that you should clean it out - Especially the processor heatsink, fan and memory. Its amazing that dust in the wrong spots can cause alot of problems. 

2. I also run a memory test. Just to make sure. 

3. I will often swap out the video card when having xcrashes. To be sure I learned to run Ubuntu in safe mode for a while to confirm a possible video card / driver problem.

I recommend those things to check first. However, I have had some problems with 10.4 and above. But its on selected machines and probably has to do with chipset problems or incompatibilities.

What invidia video card do you have?

---

### Post by tim042849 on 2010-09-19
Good Morning to you coffee412:
Below is my entire lspci dump. (see VGO controller)```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

```
and FYI: I clean the heat sink frequently. Memory tests look good.
I would not be adverse to trying another video card.
Let me know what you think.
thanks
tim

---

### Post by mikewhatever on 2010-09-19
Sometimes, compiz may be the cause of such crashes. Have you tried switching off desktop effects.

---

### Post by tim042849 on 2010-09-19
> **mikewhatever said:**
> Sometimes, compiz may be the cause of such crashes. Have you tried switching off desktop effects.
I don't use compiz. Can you tell us where to switch off those effects?
thanks
tim

---

### Post by mikewhatever on 2010-09-19
Compiz is installed and used by default if the hardware supports it, which is the case with nvidia. System->Preferences->Visual-Effects.

---

### Post by tim042849 on 2010-09-19
> **mikewhatever said:**
> Compiz is installed and used by default if the hardware supports it, which is the case with nvidia. System->Preferences->Visual-Effects.
On my desktop that is ```

System->Preferences->Appearance->Visual-Effects

```
and **Visual Effects** has been set to **none** for quite
some time, as I now recall.

BTW: Things are even more unstable when I have firefox running...
thanks
tim

---

### Post by mikewhatever on 2010-09-19
I don't know. Without something more definitive, like 'it crashes if this and that is done' or 'it freezes when something else happens', etc, it's really hard to tell.
PS: Are you running the 64 bit system, and if so, have you tried the 32 bit and vice verse?

---

### Post by coffee412 on 2010-09-19
> **tim042849 said:**
> Good Morning to you coffee412:
Below is my entire lspci dump. (see VGO controller)```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

```and FYI: I clean the heat sink frequently. Memory tests look good.
I would not be adverse to trying another video card.
Let me know what you think.
thanks
tim


Hi Tim,

Lets do a test. See about getting a different video card. Not some top of the line thing. Just a used card would be good. Borrow one from another box if you can. This is just to test the system with. See if your problem disappears. 

My thought is that using a different card no matter what it is - is going to help you figure out the problem quicker than anything else.

---

### Post by tim042849 on 2010-09-19
> **mikewhatever said:**
> I don't know. Without something more definitive, like 'it crashes if this and that is done' or 'it freezes when something else happens', etc, it's really hard to tell.
PS: Are you running the 64 bit system, and if so, have you tried the 32 bit and vice verse?
I use 32-bit. 64-bit is not an option at this time for reasons which if
were discussed would muddy this thread. I can get semi-specific about
crashes, but look at my reply to coffee412 ...
thanks

---

### Post by tim042849 on 2010-09-19
> **coffee412 said:**
> Hi Tim,

Lets do a test. See about getting a different video card. Not some top of the line thing. Just a used card would be good. Borrow one from another box if you can. This is just to test the system with. See if your problem disappears. 

My thought is that using a different card no matter what it is - is going to help you figure out the problem quicker than anything else.
Great minds run in the same gutter!
That is the suggestion that has occurred to me in the past, 
but I was hoping that I might come across a more software - based solution.
It will be a few days before I can make that happen and perhaps a few
more before I have anything to report. 
thanks
tim

---

### Post by anezch on 2010-09-19
> **tim042849 said:**
> Using ubuntu 10.04 currently. Workstation is a Gateway GT5422E with
3 gigs of RAM. I have been using ubuntu and slackware since 2007 on
this workstation. All versions of ubuntu that I have used have been
distinctly less stable than slackware. It is not unusual for firefox
to crash, less commonly, ubuntu will drop out of X to the login screen
and less frequently, but disturbly all too often the system becomes
unresponsive and a hard reboot (power-off) is required.

I stress that slackware on the same machine never acts this way. I will
also stress that I have another machine here with ubuntu 10.04 that does
not exhibit this problem. 

I presume that this has to do with the interaction of ubuntu's video
drivers with the particular hardware on this machine. 

I am using the **NVIDIA accelerated graphics driver (version 173)**

I would welcome any and all suggestions, including thoughts on other
forums or MLs that might be better sources to trouble-shoot this problem.
So, if you don't have a solution but may have another source in mind,
please let me know.

:( I get so envious when my wife, friends and colleagues have such great
stability from Lucid.

FYI: Long-time linux user (10+ years). Comfortable with the command line.
Main desktop is gnome, have tried awesome, same problems.
TIA
tim

Since you are using Slackware and found no problem when using it. I think it's caused by the software (apps, kernel and drivers). I'm using Lucid now and experienced the same problem with firefox and chrome that restart the desktop when streaming videos from the net.

Looks like the desktop is less stable here in Ubuntu. I suspected it's because of the nvidia driver but personally I have not tried to upgrade it. IMHO the nvidia driver in ubuntu is more problematic than in Slackware.

---

### Post by mc4man on 2010-09-19
i'm not sure why you're using the 173 (legacy)  drivers with a 6000 series card
The 'nvidia-current' would be better suited (195.XX in lucid

---

### Post by wilee-nilee on 2010-09-19
OP just for reference you can do soft shutdowns it is a better alternative.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

---

### Post by tim042849 on 2010-09-19
> **mc4man said:**
> i'm not sure why you're using the 173 (legacy)  drivers with a 6000 series card
The 'nvidia-current' would be better suited (195.XX in lucid
I installed the **nvidia graphics drivers** shortly after installing lucid. All the
previous (k)ubuntus had similiar problems and I had only used the default driver.
Thus I wished to try something different.

How do I uninstall the drivers and go back to nvidia-current?

thanks
tim

---

### Post by tim042849 on 2010-09-19
> **wilee-nilee said:**
> OP just for reference you can do soft shutdowns it is a better alternative.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)
Never tried it. Why should I expect that to work when ubuntu is not
responding to any keypress? Worth a try if I might expect that particular
key combination to be scanned when none others are.
:( But that is just a pill for the sickness and the sickness continues...

---

### Post by tim042849 on 2010-09-20
> **anezch said:**
> Since you are using Slackware and found no problem when using it. I think it's caused by the software (apps, kernel and drivers). I'm using Lucid now and experienced the same problem with firefox and chrome that restart the desktop when streaming videos from the net.

Looks like the desktop is less stable here in Ubuntu. I suspected it's because of the nvidia driver but personally I have not tried to upgrade it. IMHO the nvidia driver in ubuntu is more problematic than in Slackware.
Amen! Yet there is still **so** much to recommend ubuntu!

---

### Post by coffee412 on 2010-09-20
> **tim042849 said:**
> Great minds run in the same gutter!
That is the suggestion that has occurred to me in the past, 
but I was hoping that I might come across a more software - based solution.
It will be a few days before I can make that happen and perhaps a few
more before I have anything to report. 
thanks
tim

Tim, I just ran across something interesting and I dont know if this will shed some light on your problem. But here goes. Sorry if this is a bit winded.

I installed Ubuntu on a customers system. His system was a dreaded emachine / seprom processor and 1 gig of memory. Of course the install went fine and after getting installed like we wanted we experienced major lockups. I tried alot. I replaced memory, Replaced power supply and did all kinds of memory testing and system testing. 

Finally found this in the logs:
Sep 20 12:39:30 glenn-desktop kernel: [ 6294.157690] plugin-containe[3030] general protection ip:50a35f sp:f1c87a98 error:0 in libc-2.10.1.so[4e0000+13e000]

After monitoring the system with TOP while he used it I noticed that flash (plugin-containe(r) in TOP) was sucking up the memory to the point that the system would hard lock. Apparently adobe is aware of the problems with flash but have not done much about it yet. 

So, After alot of cleaning and replacing parts for troubleshooting it appears that when he uses firefox and watches Utube videos the system will eventually lockup. If he doesnt use his browser then the system is quite stable.

On my Fedora box that I dualboot ubuntu with I have no lockups with flash but then again I have 4 gigs of ram in it. I think it just doesnt get to a point of using up all available memory to crash system.

So, I say login to your system from another and run top and then wait for your computer to crash and see what top says.

Just a long winded thought here. :confused:

---

### Post by tim042849 on 2010-09-20
Thanks coffee412. I had thought of the flash sucking up memory angle, 
since I have had those experiences you have described. 
However, I have problems when not using flash also.
 Example: I've been moving a website and doing
frequent FTP from my desktop using midnight commander. (My FTP client of
choice). MC is running inside of gnome-terminal.
At the same time, I was running firefox so that I could use the 
**View Source Chart** plugin to track content rendered via DHTML.
I had to shut down the MC tab and restart several times. I would not
have had this problem if I were using Opera or Koqueror. 
So firefox is an aggravating factor in subtler ways - or so it seems to me.
thanks
tim

---

### Post by wilee-nilee on 2010-09-20
> **tim042849 said:**
> Never tried it. Why should I expect that to work when ubuntu is not
responding to any keypress? Worth a try if I might expect that particular
key combination to be scanned when none others are.
:( But that is just a pill for the sickness and the sickness continues...

I know it seems that it wouldn't work, if from what sounds like no key responses, but this method is a built in safety method it will work. You have to think a little out of the box here.;)

---

### Post by tim042849 on 2010-09-20
> **wilee-nilee said:**
> I know it seems that it wouldn't work, if from what sounds like no key responses, but this method is a built in safety method it will work. You have to think a little out of the box here.;)
I'm trying it after reading [http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub) and so
far I can't make anything happen.

Example: tried alt-shift-prtSc/sysRq-h nothing
   ctrl-PrtSc/sysRq-h nothing. Perhaps I am not reading it correctly.
   according to that page I should get "a terse help document to the console"
Probably not configured in the kernel? I looked thru
/usr/src/linux-headers-2.6.32-21/arch/frv
and searched for CONFIG_MAGIC_SYSRQ
found nothing

---

### Post by wilee-nilee on 2010-09-20
> **tim042849 said:**
> I'm trying it after reading [http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub) and so
far I can't make anything happen.

Example: tried alt-shift-prtSc/sysRq-h nothing
   ctrl-PrtSc/sysRq-h nothing. Perhaps I am not reading it correctly.
   according to that page I should get "a terse help document to the console"
Probably not configured in the kernel? I looked thru
/usr/src/linux-headers-2.6.32-21/arch/frv
and searched for CONFIG_MAGIC_SYSRQ
found nothing

Not sure how your using it but it is just a soft reboot or shutdown;when things freeze up. It will not work in rare occasions where you just have to hit the power button.

So the intructs are hold down these three keys I start in this order cttl-alt-prtsc/sysq, then slowly hit reisub will reboot, if you instead use reisuo the o=off it powers down. 

Here is another link that is easier to understand, I had to look at that wiki for a second to remember it when it is actually second nature now I have to actually think now what am I doing.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

If your getting Kernel panic though I'm not sure this works, you will only know by trying, or if somebody knows this.

Your computer will do this if you ever get totally set up just run the reboot command as I explained from a regular set up or from a live cd it is there, and watch the magic.;)

---

### Post by tim042849 on 2010-09-20
I got you now. Understood. Thank you.

---

### Post by coffee412 on 2010-09-20
> **tim042849 said:**
> Using ubuntu 10.04 currently. Workstation is a Gateway GT5422E with
3 gigs of RAM. I have been using ubuntu and slackware since 2007 on
this workstation. All versions of ubuntu that I have used have been
distinctly less stable than slackware. It is not unusual for firefox
to crash, less commonly, ubuntu will drop out of X to the login screen
and less frequently, but disturbly all too often the system becomes
unresponsive and a hard reboot (power-off) is required.

I stress that slackware on the same machine never acts this way. I will
also stress that I have another machine here with ubuntu 10.04 that does
not exhibit this problem. 

I presume that this has to do with the interaction of ubuntu's video
drivers with the particular hardware on this machine. 

I am using the **NVIDIA accelerated graphics driver (version 173)**

I would welcome any and all suggestions, including thoughts on other
forums or MLs that might be better sources to trouble-shoot this problem.
So, if you don't have a solution but may have another source in mind,
please let me know.

:( I get so envious when my wife, friends and colleagues have such great
stability from Lucid.

FYI: Long-time linux user (10+ years). Comfortable with the command line.
Main desktop is gnome, have tried awesome, same problems.
TIA
tim



Tim,

Are you getting this in your logs:

> Clocksource tsc unstable (delta = -122159006 ns)I added "acpi=off" as my theory of flash didnt pan out. Was just typing in the address field of FF and it locked up!

Just curious if you are getting this and I read a post that if you are there are some things to try and solved it for a poster.

---

### Post by tim042849 on 2010-09-21
> **coffee412 said:**
> Tim,

Are you getting this in your logs:
"Clocksource tsc unstable (delta = -122159006 ns) "?
I added "acpi=off" as my theory of flash didnt pan out. Was just typing in the address field of FF and it locked up!

Just curious if you are getting this and I read a post that if you are there are some things to try and solved it for a poster.
You bet I am:
/var/log/messages
/var/log/kern.log
/var/log/syslog
/var/log/installer/syslog
And I am seeing
```
Clocksource tsc unstable (delta = -122159006 ns)
```
**preceded** by ```

Switching to clocksource hpet
```....
And going back to retained backup logs of same.
It seems we are on to something but :oops: I'm not sure **what**!

---

### Post by coffee412 on 2010-09-21
This is what I have done so far:

Added "apci=off" to the /etc/default/grub file.
Ran grub-update
Rebooted.

Just checked system and its still up now for 10 hours. Have to see if this might be the fix for me/you.

:confused:

---

### Post by tim042849 on 2010-09-21
> **coffee412 said:**
> This is what I have done so far:

Added "apci=off" to the /etc/default/grub file.
Ran grub-update
Rebooted.

Just checked system and its still up now for 10 hours. Have to see if this might be the fix for me/you.

:confused:
OK. Keep me posted.:cool:
thanks
tim

---


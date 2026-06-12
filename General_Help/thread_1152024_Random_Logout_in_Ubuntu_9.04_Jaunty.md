---
title: "Random Logout in Ubuntu 9.04 Jaunty"
date: 2009-05-07
forum: General Help
---

### Post by Snyper450 on 2009-05-07
Every so often i log out and need to log back in what up? another bug or have i got problem with my XServer?
Can anyone shed some light?:confused:

---

### Post by lexe-cc on 2009-05-10
i have the same problem.
every now and then, the screen turns black and the system loads gdm login screen again. after logging in everything seems fine again (for a while)

---

### Post by reis.tiago on 2009-05-12
I also have the same problem. Random logouts, doesn't seam triggered by any specific action.

My system is a Pentium 4 with a old ATI card.

The only information that I found in log files that looked related to the problem was this:

```

kernel: [205484.516078] [drm] Num pipes: 1
gdm[30882]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
acpid: client 30949[0:0] has disconnected 

```

Can anyone share some light in this?

---

### Post by lexe-cc on 2009-05-19
I also have an ATI card. Radeon x700 mobility.

However, since the recent mesa packages updates i think the problem seized to exist. I've had no more random logouts. Let's hope it stays this way.
I sure hope your problems dissapeared as well.

Kind regards,
Lexe

---

### Post by blastus on 2009-05-22
This is the most annoying thing ever. I've noticed it may happen when playing a video; anything really. It has occurred on both my laptops; one has an integrated Intel video card and the other an NVIDIA card. I don't recall if it has happened on my desktops yet. I have never seen this happen before Jaunty on any machine.

I first saw it happen with Jaunty beta on my integrated Intel-based laptop. It was embarrassing because I was showing Ubuntu to a coworker and we were just browsing a simple web site then poof--the screen went black, it puked then restarted (it didn't even logout.)

---

### Post by DeMus on 2009-05-22
> **Snyper450 said:**
> Every so often i log out and need to log back in what up? another bug or have i got problem with my XServer?
Can anyone shed some light?:confused:

As can be seen there are more people having the same kind of problems. It would be good to find out what is the common factor in this, something you all share. Things like:
Hardware
which OS
do you use compiz (since this seems to be a source for many problems)

Just write the things you have and let's see from there.

---

### Post by blastus on 2009-05-22
> **DeMus said:**
> As can be seen there are more people having the same kind of problems. It would be good to find out what is the common factor in this, something you all share. Things like:
Hardware
which OS
do you use compiz (since this seems to be a source for many problems)

Just write the things you have and let's see from there.

It seems to happen on my integrated Intel-video laptop every time I use xine to play a video and try to show the OSD (On Screen Display.) As soon as I try to show the OSD the screen goes black and it dumps me back to the login screen. This is not a clean logout. It has happened other times also on both my laptops, but in the above case it happens every time.

---

### Post by carignan.boy on 2009-05-22
This happens to me too often for comfort.

OS : Jaunty 9.04
I use compiz with emerald as a window decorator.
my graphics card : ATI Radeon Mobility X1400

Someone said something about updates? When is that gonna happen?

---

### Post by Leonivek on 2009-05-28
This happened for the first time for me about 15 minutes ago.  I'm using Jaunty with all the latest updates.  Compiz is not enabled. It's not an ATI issue since I have an NVidia card.  I was simply watching [this idiot]("http://www.youtube.com/watch?v=pzrUt9CHtpY") on YouTube in Firefox and BAM, black screen and then GDM.  I've been using Ubuntu since 6.04 and I've never seen this happen.  (I'll blame it on Creationists.)  :rolleyes:

This is what the logs say at that time:

```
May 28 18:41:22 zoe-r kernel: [271132.048520] **Xorg**[16627] general protection ip:7f306e04c186 sp:7fff7b862c50 error:0 in **nvidia_drv.so**[7f306dfe9000+39a000]
May 28 18:41:23 zoe-r kernel: [271132.336024] **npviewer.bin**[19782]: segfault at ec67e3b4 ip 00000000f78fa9e0 sp 00000000ea518f74 error 4 in libpthread-2.9.so[f78f3000+15000]
May 28 18:41:25 zoe-r gdm[3546]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 28 18:41:25 zoe-r kernel: [271135.166566] pidgin[16907]: segfault at 2206000 ip 00007f2ae1a4095d sp 00007fffea635550 error 6 in libX11.so.6.2.0[7f2ae1a09000+102000]
May 28 18:41:29 zoe-r acpid: client 16627[0:0] has disconnected 
```So it's probably either a problem with Xorg or Nvidia, or Firefox's Adobe *Flash* Player plugin (npviewer.bin), or a combination.

If it happens again, I'll be sure to post here again.

---

### Post by AmsiNZ on 2009-05-29
I'm having the same problem with Jaunty, and the pattern I am noticing is it happens when I am browsing pages with flash content.  I originally thought Compiz might be the culprit, so I disabled it earlier this week, but it is still happening.  I might remove Adobe Flash and install Gnash to see it stops the problem. 

OS:  Ubuntu 9.04 (Fresh Install)
Compiz:  Not enabled 
Flash Plugin:  Adobe Flash plugin for Firefox.
Motherboard: ASUSTek P5VDC-MX
Graphics:  ATI Radeon 9600XT

I found similar entries in my logs:
```
May 29 22:05:24 Gulgothir kernel: [ 2886.725930] [drm] Num pipes: 1
May 29 22:05:25 Gulgothir gdm[2932]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
May 29 22:05:25 Gulgothir kernel: [ 2887.116103] pidgin[3524]: segfault at 961d000 ip b7e96253 sp bfb77fe0 error 6 in libX11.so.6.2.0[b7e67000+ea000]
May 29 22:05:26 Gulgothir acpid: client 2936[0:0] has disconnected
```

It'll be interesting to eventually see what is causing it. ;)

---

### Post by Irish J on 2009-06-02
Just had this as well.  Been happening for the last couple of days.  How do i post that loggy thing? :D

---

### Post by carignan.boy on 2009-06-05
It seems to me that this has a lot to do with the Flash plugin. I'm going to try and disable it, see how things run and come up with news about that.

Oh noess! No youtube!!!!

---

### Post by GhostCard on 2009-06-10
I'm been trying to even log in since upgrading to 9.04. Every time I log in i am dumped back at the login screen after about 5 to 10 sec. I have tried all the brands of graphics cards i have, same result. What else can i try before going back to 8.10?

P4 2.0GHz
Savage (on-board) and Nvidia MX440 and ATi 9200 and Voodoo FX3
Only have stock 9.04 software due to the fact i can't login.

---

### Post by fathi shaman on 2009-06-11
> **carignan.boy said:**
> It seems to me that this has a lot to do with the Flash plugin. 

I have the same Problem and I don't even have a flash-plugin installed.

But I use a KVM-Switch. Sometimes when I switch back to the Jaunty-Machine where i've been logged in, I'm logged out and see the gdm-Loginscreen.

Is there any Bugreport at launchpad?

Is everybody having this problem using encryptfs for their Home Directory?

---

### Post by 7tisix on 2009-06-13
Happened to me also.

Ubuntu 9.04
ATI Radeon 9000, P4-2800, 2GB Ram, Root on EXT4    All updates for Ubuntu 9.04, fresh install.

Was running Firefox, SSHFS, Truecrypt.  Active SSH connection.  Very large USB Flash drive connected and transferring files through SSH.  Wireless LAN... Linksys.

---

### Post by mrkiss on 2009-06-14
It Happened me also too

and the wallpaper is zoomed in broken image of some window now showing so I think it seems like video card problem.

It is just fresh installed ubuntu 9.04. I didn't do anything
First time I logged in it didn't log out immediately but after several minutes it started to log out just after login.
I set it up auto login. so the Ubuntu logs in and out automatically and eternally~


My computer is
Dell Dimension 5100 I bought it in 2005 
Ubuntu 9.04 Fresh install.
Pentium 4 3GHz, 2GB Memory, ATI Radeon X300 SE video card


And I saw lexx-cc says recent mesa packaged update has stopped the problem. But it seems nobody listen to the success..
How can I update mesa package? 
I am new to linux. Could anybody tell me the details?

---

### Post by nikolayo on 2009-06-14
For me the logout is not really random. It happens every time I try to play video with Movie Player or VLC (but does NOT happen when I play video in the browser with Flash Player). My machine is Thinkpad T500. Here is the configuration:

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
```

---

### Post by carignan.boy on 2009-06-15
for sure this has nothing to do with flash. I confirm. After a week of Flash turned off, I was still being logged out. So you guys think it might have something to do with playing video?

How do I revert to the proprietary ATI driver? I do like my sofware being free, but I like it functional also.

---

### Post by mrkiss on 2009-06-16
For my case. It was display driver problem. 

When I turn off display effect, the logout problem disappeared

My old Radeon x300 video adapter maybe not good for the display effect

But you have to click fast to reach the Appearance - Effect menu before logout  :D

And I failed to install ATI's recent  linux driver. It didn't worked but spitted errors. I gave up.

I don't want anymore for this old video card

---

### Post by VastOne on 2009-06-16
Just as I was trying to reply to this, it happened again and I also get a reboot automatically back to login.

Using a nVidia 9500 GT and the 185.18 drivers.

Have been using this machine for several months with no issues and in the last week I have had this every 45 minutes to 2 hours.

Have almost identical machine (955 AMD Phenom where this is the 940 phenom) and a slightly newer MOBO on the other machine and have never seen this on the other machine.

Reading about this all over the web, hardware cannot be the issue as there are hundreds of variations with the same issues. 

The fact that this was a stable machine leads me to believe an update is the culprit.

I am getting the generic gdm_slave_xioerror_handler error on every reboot

---

### Post by nikolayo on 2009-06-20
> **nikolayo said:**
> For me the logout is not really random. It happens every time I try to play video with Movie Player or VLC (but does NOT happen when I play video in the browser with Flash Player). My machine is Thinkpad T500. 

FYI: At the end of the day it turned out that my logout problems are caused by 9.04 problems with Intel video driver. I found and applied successfully a fix here: 
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Seanman on 2009-07-08
Not sure if anyone is still paying attention to this thread, but I've been having the same sort of thing happen to me and I've tried multiple solutions and nothing works.

Periodically, my Jaunty install completely locks up.  After ten minutes or so, I get control back and the only thing I see in the logs that's relevant is:

Jul  8 12:29:35 mymachine acpid: client 3642[0:0] has disconnected
Jul  8 12:29:35 mymachine acpid: client 3642[0:0] has disconnected
Jul  8 12:29:35 mymachine acpid: client connected from 10309[0:0]
Jul  8 12:29:36 mymachine acpid: client connected from 10309[0:0]

While the motherboard has the Intel chip on it, I've disabled it and I'm using an NVidia card.

This problem is MUCH more egregious -- as often as once an hour -- if I do anything with Flash.  Only a restart will fix it.  But it still happens, albeit less frequently, if I avoid flash and anything having to do with video.

I'd very much appreciate any suggestions as to how to deal with this.  I've tried the nolapic, noapic, and acpi=off kernel parameters in all permeations with no success.  The usual logs tell me pretty much nothing and I'm not sure where to look next.

Thanks

Sean

---

### Post by tuberculo on 2009-08-06
Any solutions?

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/244737](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/244737)

---

### Post by jdforsythe on 2009-08-11
This happens to me about 50% of the time I play Farm Town, a flash game on Facebook.

I can't recall it happening when I wasn't using flash.

Other people have disabled flash and it happens when they play videos.

All different motherboards, all different video cards. What is the common thread? Pulseaudio, maybe? I've had problems with pulseaudio since Hardy.

I have also had a lot of trouble with VLC since I installed Jaunty. VLC will randomly stop playing and close. Anyone think it may be related?

Another thing I've noticed, sometimes when it logs out, if I try and open firefox after I log back in, it will either just close firefox out or sometimes it logs out again (especially if I restore the previous session with the flash page).

Anyway, right before it shows me the login screen, it shows tty8. Not sure if that helps or means anything.

Couple more symptoms I forgot:

Once when it logged out and I logged back in, all window decoration was gone (I don't use any desktop effects but I just mean the Human theme was completely disabled and it was like looking at win 98 compared to xp, very boxy and ugly looking, and the red, on/off button for shutdown had turned into an icon of a person).

Once after logging back in, my desktop icons appeared, so nautilus started, but none of the panels showed and none of the keyboard shortcuts (ctrl-alt-f2, etc) would work. It was like I was running nautilus with no gnome around it. Weird.

A couple times it logged out and back in in a loop (I have it set to auto-login) and after a few times it stopped.

I thought it may be related to adding some 3rd party repositories to keep updated on packages like vlc, openoffice, and the like, but others seem to be having this trouble on fresh installs.

I hope any of this could be of some help. Anyone want to see output from certain logs or anything of the sort, just let me know. I scanned the logs and couldn't find anything I thought to be pertinent, but I could be looking in the wrong place.

---


---
title: "Graphic card crash while playing games."
date: 2016-04-09
forum: Gaming &amp; Leisure
---

### Post by grzegorz7 on 2016-04-09
Hello.
Few days ago i installed ubuntu and downloaded league of legends (play on linux), left 4 dead 2 and team fortress 2 (steam). I tried to play them (mostly league of legends) but my graphic card seems to be crashing every time.
Here's what's happening from user point of view: I start playing and at random time my monitor kinda turns off (screen goes black and after that "no signal" appears). I cant use keyboard, mouse or see anything. Sound is working just fine. Only holding power button for 5 seconds to force shutdown works. When i hit reset button my pc boots but there are 3 beeps instead of one (graphic card or ram error).
I've got gts 250, i5 @750
Drivers that i'm using are NVIDIA binary driver - version 340.96 from nvidia-340 (proprietary, tested). I've tried others but this doesnt help.
Beside nvidia drivers in my software & updates -> additional drivers i've also checked "using processor microcode firmware for Intal CPUs from intel-microcode (proprietary). Checking or unchecking it seems no difference for me.
Worst thing is that i dont know where i can find any logs or error informations. I dont know what's happening and what can i do.
I'm counting on Your help :)

---

### Post by grzegorz7 on 2016-05-04
I'll allow myself to refresh this question.
Here's update. I installed half life 1 from steam and it's just working. No crashes, i can play all day long without any trouble. But any other game (no matter if it's on steam or wine/play on linux) always ends crashing my pc. Nothing changed from my point of view - crash looks same as i described it above.
Could You please give me some advices?

---

### Post by howefield on 2016-05-05
Hello grzegorz7,

Welcome to the forums, I have moved your thread to the "*Gaming & Leisure*" forum, who better to talk about graphics cards than fellow gamers.

Also feel free to give your thread a daily bump if no response is recieved.

---

### Post by David_Farkas on 2016-05-05
If the game keeps running after the issue, the error is definitely with the graphic card. It seems to me, that it is a hardware problem (because the BIOS can detect it). You could try a GPU stress test with GpuTest. Maybe Half Life 1 has lower system requirements than the other games and therefore it doesn't uses the damaged part of the video memory.
I'm not a professional, it is just an idea.

---

### Post by mastablasta on 2016-05-05
does half life run in software acceleration maybe?

beeps on boot indicate hardware failure of some sort.

1. Test your ram using memtest (i think it's on live CD if not use "Ultimate boot CD")
2. check the temperature of the system. for example using** psensor**: [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/) (a version should be in the software center)
3. check if the system is actually using hardware 3D acceleration 
    - run ```
glxinfo | grep "direct rendering"
``` 
- it should say "direct rendering: Yes"
glxinfo is part of mesa-utils and you might need to install those (software center)
4. if you can try to borrow and replace the card and see if the problem persist (it's the easiest way to see if card is bad)

recently i was searching for an app that would do VRAM test, but i haven't found any. so i had to use elimination process and screenshots&photos from other people to see where the issue is. perhaps someone here know of a VRAM test that works in linux?

5. check system logs specifically dmesg for any errors (dmesg command will display the log, but there are many GUI log viewers available if not preinstalled). you should se eif drivers are loaded propperly.
6. finally - nvidia has a troubleshooting script or should i say more a reporting script that when run will give out important information. if we can pinpoint the erorr to the graphics card, the files from report will be needed to get official nvidia support (nvidia forums or support form)

---

### Post by grzegorz7 on 2016-07-24
> **David_Farkas said:**
> Maybe Half Life 1 has lower system requirements than the other games and therefore it doesn't uses the damaged part of the video memory.
I checked one more old game. It's called metin2 - it's old mmo game. Sys requirements are:
Minimum system requirements:
**CPU:**
Pentium3 1000 MHz
**RAM:**
512 Mb
**GPU:**
32MB RAM
**DX:**
DirectX 9.0
**OS:**
Win XP, Win 2000, Win Vista, Win 7
**Store:**
1000 Mb

So my pc should handle it (and it did about 7 years ago when i got windows. Basically problem occurred when i switched to ubuntu. On windows i never had such a problem).

> **David_Farkas said:**
> You could try a GPU stress test with GpuTest.
I downloaded linux version and launched few tests. None of them made my pc crash. But i've got theory that it's because all of tests were runing on opengl.

> **mastablasta said:**
> does half life run in software acceleration maybe?
Dont know, how can i check it?

> **mastablasta said:**
> 1. Test your ram using memtest (i think it's on live CD if not use "Ultimate boot CD")
Tested, passed.

> **mastablasta said:**
> 2. check the temperature of the system. for example using** psensor**: [http://wpitchoune.net/blog/psensor/](http://wpitchoune.net/blog/psensor/) (a version should be in the software center)
I found case when it's 100% sure that crash will happen. At that moment it's always about 60 celcius degree so it's not a problem (my card can handle 80 degrees - seen it many times)
> **mastablasta said:**
> 3. check if the system is actually using hardware 3D acceleration 
    - run ```
glxinfo | grep "direct rendering"
``` 
- it should say "direct rendering: Yes"
It is saying "direct rendering: Yes" so the answer is yes.
> **mastablasta said:**
> 4. if you can try to borrow and replace the card and see if the problem persist (it's the easiest way to see if card is bad)
Unfortunately i dont have anyone who could borrow me gpu for short time.
> **mastablasta said:**
> 5. check system logs specifically dmesg for any errors (dmesg command  will display the log, but there are many GUI log viewers available if  not preinstalled). you should se eif drivers are loaded propperly.
I opened preinstalled "System Log" and under "syslog" i found that when crash occur no logs are written. There is blank line:
```

Jul 24 18:36:33 gkocik-desktop systemd[1]: Started CUPS Scheduler. // previous log
// 18:41 crash occured but no log about that
Jul 24 18:42:06 gkocik-desktop rsyslogd-2222: command 'KLogPermitNonKernelFacility' is currently not permitted - did you already set it via a RainerScript command (v6+ config)? [v8.16.0 try http://www.rsyslog.com/e/2222 ] //next log (after pressing power button)

```
"dmesg" tab in System Log says "(Nothing has been logged yet.)" but when i type this command in terminal many logs appears. Unfortunately there is no timing in them (or i cant understand it) so it's hard for me to search for crash error.

I mentioned before in this post that i have some theory. Looks like half life is runing under opengl and any other game i tried to run runs on directx. I think this is the problem. Watching videos, opengl bencharks and any other activity wont cause crash but playing games on directx do.
Any suggestions?

---

### Post by uNoubu8a on 2016-07-24
I don't have anything to add that is a solution, but can say that none of the games you have played on Linux has been using DirectX as it doesn't work on Linux.  Games like League and other Windows games that use DirectX is played via [Wine]("https://www.winehq.org/") that translates the DirectX calls into something that Linux can handle (like openGL).  So if your games are always locking your PC when using Wine it may be something related to this.

When you play games in Steam, are you using the native linux version or Windows binary via Steam?  Left for Dead 2 has a native linux client, if it doesn't lock up your system then we don't have to worry about hardware being an issue (which it doesn't sound to me to be).  If it is only under Wine we have to start troubleshooting there.

Also, just for clarity what version of Ubuntu are you using (judging from the graphics driver I would think 14.04?).

---

### Post by grzegorz7 on 2016-07-24
Ok so games I play:
- half life 1 downloaded from steam - works perfectly fine
- left 4 dead 2 downloaded from steam (so i assume it's native linux version) - always crashes after < ~5 minutes
- team fortress 2 downloaded from steam (so i assume it's native linux version) - always crashes after < ~5 minutes
- metin2 through wine  - always crashes after < ~15 minutes
- league of legends through play on linux - always crashes after < ~15 minutes

What i meant in my theory about directx and opengl was that half life 1 has no directx in minimal requirements so i assume it does not use it. But as You said left 4 dead 2 and Team fortress 2 downloaded from steam has native linux versions so they should work just fine. But they dont. Basically i assumed that theory after seeing none of downloaded benchmarks that i runned have cause this crash.

Right now (installed today) i'm using 16.04. But before (since topic creation as for yesterday) it was 15.10. I did not say before but it's probably worth of mention that both of instalations required to use nomodeset. Mayby it has something to do?

Right now i have installed NVIDIA binary driver - version 340.96 from nvidia 340 (proprietary, tested)

By the way i dont think it's hardware problem. Main reason is because i played on this computer for past 7 years with windows on it. Problems starded after installation of ubuntu. Additionally why benchmarks do not cause crash? Only games (and as You already know not all of them - half life 1)

---

### Post by mastablasta on 2016-07-25
> **grzegorz7 said:**
> Ok so games I play:
- half life 1 downloaded from steam - works perfectly fine
- left 4 dead 2 downloaded from steam (so i assume it's native linux version) - always crashes after < ~5 minutes
- team fortress 2 downloaded from steam (so i assume it's native linux version) - always crashes after < ~5 minutes
- metin2 through wine  - always crashes after < ~15 minutes
- league of legends through play on linux - always crashes after < ~15 minutes

If you are running steam under wine then you are downloading the windows version. you could check the game settings if you can enable openGL. if you installed via wine then we would need ot knwo what stuff you have installed in wine. e.g. do you have driectx installed, do you have winetricks installed, are all necessary things installed...?
> 
What i meant in my theory about directx and opengl was that half life 1 has no directx in minimal requirements so i assume it does not use it. But as You said left 4 dead 2 and Team fortress 2 downloaded from steam has native linux versions so they should work just fine. But they dont. Basically i assumed that theory after seeing none of downloaded benchmarks that i runned have cause this crash.


check if the versions you downloaded are really linux versions.

it doesn't not seem to be a hardware error but a software one - either wine settings or drivers settings/drivers issues.

---

### Post by grzegorz7 on 2016-07-25
I installed steam through apt-get (sudo apt-get install steam) so i assume it's linux version. One thing i know for sure: when i'm lunching steam or Left 4 Dead 2/Team Fortress 2 I dont use wine to do it (at least not manually). I just click on desktop icon which was created by steam.

---

### Post by uNoubu8a on 2016-07-25
I am reading through the following to see how one would troubleshoot this:

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)
[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)
[https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Pretty epic.

---

### Post by grzegorz7 on 2016-07-26
Thank You! I read these and i was able to catch some error logs.
I provoked crash two times while connected by ssh.
At the first time i only checked sudo cat /proc/kmsg. Here is a result:
```
gkocik@gkocik-desktop:~$ sudo cat /proc/kmsg
<6>[16450.003910] pcieport 0000:00:03.0: AER: Multiple Corrected error received: id=0018
<4>[16450.076098] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
<4>[16450.076106] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
<4>[16456.432118] show_signal_msg: 33 callbacks suppressed
<6>[16456.432122] compiz[3255]: segfault at 7fb71f76efff ip 00007fb60ab9d966 sp 00007ffe3f819030 error 6 in libnvidia-glcore.so.340.96[7fb6093ec000+19c2000]
```

At second time i logged three things:
sudo cat /proc/kmsg [http://wklej.to/I2OFA](http://wklej.to/I2OFA)
tail -f /var/log/syslog [http://wklej.to/pSGkm](http://wklej.to/pSGkm)
sudo nvidia-bug-report.sh (it's probably not complete because of script hang but it's said to paste it anyway) [http://wklej.to/SZHJw](http://wklej.to/SZHJw)

I tried to google a bit by myself but to be honest i'm not good at this stuff so once more i'd like to ask you for help.

Edit:
I did one more try in Left 4 Dead 2. Crash occured so I've got another log files:
sudo cat /proc/kmsg [http://wklej.to/G4ARQ](http://wklej.to/G4ARQ)
tail -f /var/log/syslog [http://wklej.to/i4jiu](http://wklej.to/i4jiu)
sudo nvidia-bug-report.sh (this time script did not crashed so raport is complete) [http://wklej.to/hEyQC](http://wklej.to/hEyQC)

---


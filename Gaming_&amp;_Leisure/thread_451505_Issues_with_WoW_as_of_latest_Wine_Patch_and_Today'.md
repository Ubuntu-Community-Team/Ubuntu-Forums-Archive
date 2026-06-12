---
title: "Issues with WoW as of latest Wine Patch and Today's WoW Patch."
date: 2007-05-22
forum: Gaming &amp; Leisure
---

### Post by Stormweaver on 2007-05-22
I'm running WoW on Edgy - The Wine update a week or so ago caused the launcher to have an error before it ran, though the box has got no writing in it.  Then the launcher comes up - No pictures or writing.  Click launch and it goes to the WoW Login Screen and all seems good.

Now today, the Patch 2.1.0 comes down, and the same errors happen, but now when I exit (Was checking to see if the servers were back up), it hangs.  And as a result of some part of this, its causing my Teamspeak server to not be available to log in to as well.  Its says its running, but any client trying to log into it "No Reply from Server"


Help!?!?!?

Stormweaver

---

### Post by Sammi on 2007-05-22
system specs please

wine and graphics driver version...

---

### Post by warewolf55 on 2007-05-22
It's not an isolated incident. After installing the patch I can start and use the program, the problem only occurs when I try to exit the program. It will hang, seemingly forever, until I do a "wineserver -k" to kill it.

The wine version is:  wine-0.9.35
Ubuntu version is :  Ubuntu 7.04 - the Feisty Fawn
System : P4 3.20Ghz, 1Gb ram
Video Card : Nvidia GeForce 7800 GS/OC
Video Drivers : Nvidia v1.0-9755
Wine Config : NT4/2000/XP (I tried all three)

---

### Post by hikaricore on 2007-05-22
Hang on close happening on my girl's system as well.

Could this be opengl related?

/me goes to check the mac forums.

---

### Post by graigsmith on 2007-05-22
k, I'm having the same problem. crash on exit.  it also occasionally HARDLOCKS my whole system. I'm using an ati 9200 with the open source drivers, and despite somewhat poor framerates, i haven't had any problems running it with the last patch.  This patch is messed up i think.

also, i am getting wierd texture problems when i zoom away from my character, gonna try disabling Level of detail. if i can log in. wont even let me.

edit, im gonna see if i can get rid of my hardlock problem by upgrading to the newest wine version.  ugraded to newest version, STILL hardlocks. seems to hardlock, after this sequence of events. run wow, exit wow, kill wow because it crashes.  try to run again, system hardlocks.

---

### Post by hikaricore on 2007-05-22
there were rolling restarts going on.  might be awhile before you can >.<

---

### Post by Tellisk on 2007-05-22
Okay Authentication servers seem to be down now, but that aside, when I was able to log in, the game was rather slow and even on the login screen it is quite choppy. It was working much better yesterday, so I assume it's patch related. Switching to NT4 didn't seem to have any effect whatsoever.

Ubuntu 6.10, Nvidia GeForce 6800, 1.0-9755, latest Wine.


Edit: Also having the program freeze on exit, though it lets me logout fine.

---

### Post by graigsmith on 2007-05-22
hmm, was reading the blizzard forums, and they recommended running repair.exe for a similar problem.  I'm going to try it and i'll let you know how it goes.

---

### Post by graigsmith on 2007-05-22
hmm. the repair tool had no effect.  wow still crashes when you try to exit the program.

---

### Post by Drezliok on 2007-05-22
I have the same problems. It's not saving any settings now either, I'm going to manually change them.

---

### Post by graigsmith on 2007-05-22
apparently you can get the game to save settings ingame, by typing
/console reloadui

i diddn't know that caused it to save settings, but some guy on the cedega forum said that will save settings.
also they noticed that everyone that was having problems with this has an athlon xp. 

i have an athlon xp. is anyone using intel that is experiencing this problem?

---

### Post by Drezliok on 2007-05-22
I am, P4 2.66 no HT

My launcher is still busted... Maybe I need to redo my wine. I like getting my news.

---

### Post by shnastybiznastic on 2007-05-22
I had the same problem under Edgy today.  After the patch everything worked fine for a little while, but then my latency spiked to over a minute and I got disconnected and WoW crashed.  Since it didn't get **** down properly, every time I try to log back in, it locks up my system.  When I tried to log in after getting disconnected, I had to re-agree to the EULA and TOS, but it froze and locked my computer up after I accepted the TOS.  The second time, my realm was down, and it wouldn't let me log in, but didn't freeze.  I was going to try logging in to another realm, but mine came up after that, so I tried to get back into it only to be confronted by the exact same crash.

I'm running the ATI drivers on a 9800 pro.

---

### Post by Drezliok on 2007-05-22
I believe is this is more of an issue with Wine rather with Blizzards patch. Latest wine update broke my launcher. So I guess all there really is to do is wait for a work around.

---

### Post by Tellisk on 2007-05-22
Okay, my game is extremely choppy. Completely unplayable. I can get past the fact that it freezes on exit with Ctrl-C, so I'm not even worried about that problem right now. Here is what my terminal says as the game is running (copied everything after the command wine WoW.exe:


```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7d0c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d0c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5cc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5c0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f024,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x37400f40) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7c844554) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33d1d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d22c,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:ntdll:RtlpWaitForCriticalSection section 0x4f9f88c "?" wait timed out in thread 0011, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x4f9f88c "?" wait timed out in thread 0011, blocked by 0009, retrying (60 sec)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x33ce8c,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
```

---

### Post by Drezliok on 2007-05-22
Anyone here a maintainer for the game on the WineHQ AppDB?

---

### Post by lckeeper1 on 2007-05-22
I'm getting the same issues as well with hanging upon exit. I'm running on Fiesty with wine 9.37. Prior to the patch everything was peachy, but now it's a bit of an inconvenience.

In-game is still running well, just freezing on exit.

---

### Post by WINEHQ-GOT-HAXORED on 2007-05-22
gg all

---

### Post by laffys on 2007-05-22
same here before the blizzard patch everything was great. now after the patch it freezes on the exit part. :(

---

### Post by Skylara on 2007-05-23
Same problem here, but I don't think it's an OS thing.  A person posted on a thread that their Vista was having the same problem.  I linked to THAT thread from this thread below.  Both are worth reading just to see what issues people are having.

[World of Warcraft Tech Forum Thread]("http://forums.worldofwarcraft.com/thread.html?topicId=105970623&postId=1056811154&sid=1#3")

So I guess we're SOL until Blizz fixes it... or until a Ubuntu god finds a workaround.

---

### Post by hikaricore on 2007-05-23
> **WINEHQ-GOT-HAXORED said:**
> gg all


idiot

---

### Post by Falcorian on 2007-05-23
> **graigsmith said:**
> k, I'm having the same problem. crash on exit.  it also occasionally HARDLOCKS my whole system. I'm using an ati 9200 with the open source drivers, and despite somewhat poor framerates, i haven't had any problems running it with the last patch.  This patch is messed up i think.

also, i am getting wierd texture problems when i zoom away from my character, gonna try disabling Level of detail. if i can log in. wont even let me.

edit, im gonna see if i can get rid of my hardlock problem by upgrading to the newest wine version.  ugraded to newest version, STILL hardlocks. seems to hardlock, after this sequence of events. run wow, exit wow, kill wow because it crashes.  try to run again, system hardlocks.

This is the exact problem I'm having! Runs fine for awhile, textures glitch if too far away, and then hard locks after about 15 minutes.

Haven't been able to fix it at all, if you come up with a solution, I'd be glad to here it.


Oh yeah, I'm running a ATI 9700 Mobility with proprietary, and everyone else I've seen with the problem is on ATI. :(

---

### Post by justin whitaker on 2007-05-23
I run WoW using Crossover...patch installs fine, game is fine (a little choppy on Thunderhorn and Blackhand, both of which are high volume servers, less so on Earthen Ring)...on exit, need to force kill WoW because it locks on exit. Running the game windowed so I can make that part easy.

---

### Post by infamous on 2007-05-23
after 2.1 patch game crash on exit ( i have to kill wow.exe )  before patch everything goes perfectly..

intel core duo, nvidia driver 1.0-9631, ubuntu feisty, wine 0.9.37

---

### Post by marcozs on 2007-05-23
It was running fine on my Feisty desktop yesterday, I am not yet at home so I haven't got the latest patch... is there a way to skip installing it since it seems that it's causing problems to everyone? :)

---

### Post by infamous on 2007-05-23
>  It was running fine on my Feisty desktop yesterday, I am not yet at home so I haven't got the latest patch... is there a way to skip installing it since it seems that it's causing problems to everyone? 

i don't think so

---

### Post by BetaguyGZT on 2007-05-23
Same problems here. Settings won't save, game runs like crap, and locks up on exit (must kill it to shut it down), occasional hardlocks. Worked fine before.

And same problem with the launcher also. Worked fine until updating Wine a few days ago.

---

### Post by slayerboy on 2007-05-23
to confirm, this is happening on my system too after the patch....

AMD Sempron 2.0GHz
1GB RAM
Nvidia Geforce 6200 256MB
running xubuntu fiesty

last time they had problems like this was when 2.0.5 for BC came out....I had to buy a new graphics card then!  I'm NOT buying a new computer this time! LOL.

It can't possibly be a problem with wine.  It's gotta be an issue with the patch, which I think, and would hope, they're working on.

Until then, as long as my server stays online, I'll just make sure I have no programs running and exit Wow and wait a few minutes then restart x with the good 'ol CTRL-ALT-BACKSPACE lol

---

### Post by Falcorian on 2007-05-23
> **infamous said:**
> i don't think so

Install it in Windows, and then copy the entire WoW folder over to Linux. You can use a friend's install from a Window's Box, should work too.

---

### Post by Pikestaff on 2007-05-23
Has anyone stumbled across a fix for this yet?  Things seem to be okay for me in-game (at least so far, I haven't spent a lot of time with it yet) but the lockup on exit has a tendency to mess up my system sound.

---

### Post by z0phi3l on 2007-05-23
> **Falcorian said:**
> Install it in Windows, and then copy the entire WoW folder over to Linux. You can use a friend's install from a Window's Box, should work too.

THAT caused my WoW.exe to get corrupted, had to delete the patch.mpq, reset to 2.0 and manually install all the updates, then used the Blizz downloader to install 2.1

---

### Post by Sammi on 2007-05-23
> **z0phi3l said:**
> THAT caused my WoW.exe to get corrupted, had to delete the patch.mpq, reset to 2.0 and manually install all the updates, then used the Blizz downloader to install 2.1Never seen that before.

Anyway I've been looking in other forums and there doesn't seem to be a fix yet. But hey, the game still starts and you can play it. Who cares what happens after you close it ;)

---

### Post by Falcorian on 2007-05-23
> **z0phi3l said:**
> THAT caused my WoW.exe to get corrupted, had to delete the patch.mpq, reset to 2.0 and manually install all the updates, then used the Blizz downloader to install 2.1

Will it worked for me and others. Sorry to hear didn't work for you.

> **Sammi said:**
> But hey, the game still starts and you can play it. Who cares what happens after you close it ;)

For some people... :( Other people crash while playing. *sigh*

---

### Post by iriemon on 2007-05-23
Same problem here.  The game ran well up until yesterday's 2.1.0 patch.  Now it hangs on exit.

Just a reminder, '/console reloadui' in-game will save your setting for the time being.

---

### Post by shnastybiznastic on 2007-05-23
> **Falcorian said:**
> For some people... :( Other people crash while playing. *sigh*
I still can't get to the login screen.  Every time I start it I have to re-accept the eula, then it frezes my machine up.  The only time I was able to get past this problem was when my server was down, in which case I tried to log in and it told me that Sisters was down.

---

### Post by Falcorian on 2007-05-23
For the EULA at least, you can delete your WTF/RunOnce.WTF.

That probably won't fix your real problems though, but it's one problem down.

---

### Post by Stormweaver on 2007-05-23
Hey gang, I started this thread so I will at least update from my end.

My issues started when Wine Updated a few days prior to patch, that made my Launcher have some sort of error where it couldn't connect to display info.  Also I noted this stopped the patch from coming down over a few days prior to patch day.  So I hate wait longer on patch day to get it all in, thats when the freeze on shut down occured.

I forgot to post my specs here, maybe this will help maybe it won't... But if we all raise enough noise with this, we may even be able to get Blizz to re release the Linux Version

AMD Ath XP 64 -- Running 32 bit Ubuntu Edgy 6.10 - Plus updates.
GeForce 6600GT PCIe Vid Card.

If you need more info feel free to ask.

I hope this gets fixed soon.

---

### Post by shnastybiznastic on 2007-05-23
> **Falcorian said:**
> For the EULA at least, you can delete your WTF/RunOnce.WTF.

That probably won't fix your real problems though, but it's one problem down.

Hey, one problem at a time is the only way to debug.  Thanks for the advice about my .WTFs.  If nothing else, this issue will familiarize me with the WoW innards.

edit:  After deleting my RunOnce.WTF, my problems are more in line with those experienced by people here.  I can't quit properly.  But I can play now, so that's nice.  Thanks for your help.  I didn't expect that file to have such a major impact.  Perhaps it calls whatever function locks WoW up when I try to quit after you accept the EULA and TOS?

---

### Post by slayerboy on 2007-05-23
I think I found a possible solution to our WoW exiting woes.

Now I tested the /console reloadui thing, and it doesn't work for EULA issue.

But...if you run the game from a console window, when you exit from the game and it's still freezing, ALT-TAB to the console window and press CTRL+C and it will end the game.

Now in XFCE, I set a launcher on my panel and ticked the box to run in terminal.  That makes it less messy because when I hit CTRL+C, the terminal exits as well.

Still an issue with saving the settings though.  You could try manually changing Config.wtf so that it won't display that, but I've tried that in times past and it did nothing.  

At least, for those of us that have a playable game, we can now exit with this strategy.:p

---

### Post by justin whitaker on 2007-05-23
> **slayerboy said:**
> I think I found a possible solution to our WoW exiting woes.

Now I tested the /console reloadui thing, and it doesn't work for EULA issue.

But...if you run the game from a console window, when you exit from the game and it's still freezing, ALT-TAB to the console window and press CTRL+C and it will end the game.

Now in XFCE, I set a launcher on my panel and ticked the box to run in terminal.  That makes it less messy because when I hit CTRL+C, the terminal exits as well.

Still an issue with saving the settings though.  You could try manually changing Config.wtf so that it won't display that, but I've tried that in times past and it did nothing.  

At least, for those of us that have a playable game, we can now exit with this strategy.:p

Yeah, my workaround is similar: load the game windowed, an alt-tab out to system monitor where I can kill the game manually. I haven't noticed any settings differences between logins, but then I'm hearthing and exiting...

---

### Post by Skylara on 2007-05-23
This is how I dealt with the problems...

1) I logged into a character and did a /console reloadui to save my settings.
2) I went into World of Warcraft/WTF and delete the RunOnce.wtf (I believe it was called)

Now my settings are saved AND I don't have to read the EULA every login.

3) When exiting, I exit as normal, then  CTRL ALT arrow to another workspace, bring up a terminal and kill the wineserver with *winserver -k*.

Annoying, but it works.  Other than that I have NO other problems with WoW.  I have Ubuntu 6.10 and Wine 0.9.37.

---

### Post by hikaricore on 2007-05-23
Threw together a little script for my gf thought it might be useful to someone.

This will kill every threaded process of WoW.exe, leaving winesever untouched.

Useful if you are running more than one app in wine and just want to kill WoW.

```

#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done

```

---

### Post by Falcorian on 2007-05-23
> **hikaricore said:**
> Threw together a little script for my gf thought it might be useful to someone.

This will kill every threaded process of WoW.exe, leaving winesever untouched.

Useful if you are running more than one app in wine and just want to kill WoW.

```

#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done

```

Ok, not on a WoW topic at all, but a bash question:

What is the advantage of using kill -9 instead of killall -9, which seems to do what your script does already? (That is, kill by name instead of PID)

---

### Post by hikaricore on 2007-05-23
Alot of times:

> killall WoW.exe

Fails. As does the killall command on many resource heavy threaded applications.

You can seriously spam: killall WoW.exe 
Over and over for up to 20 seconds if you've had it running for awhile.  ^_^

The "i" loop grabs the pidof WoW.exe in every occurance it is found, kills the number returned and does it again.  I've found this to be the most effective way of dealing with trouble applications such as this.

---

### Post by Falcorian on 2007-05-23
> **hikaricore said:**
> Alot of times:



Fails. As does the killall command on many resource heavy threaded applications.

You can seriously spam: killall WoW.exe 
Over and over for up to 20 seconds if you've had it running for awhile.  ^_^

The "i" loop grabs the pidof WoW.exe in every occurance it is found, kills the number returned and does it again.  I've found this to be the most effective way of dealing with trouble applications such as this.

Ah good to know.

---

### Post by AndrewRiedi on 2007-05-23
Also useful is, ```
wine taskmgr
```

This will basically behave like the Windows task manager does.  Ie. you can use it to kill programs.  ;)

---

### Post by hikaricore on 2007-05-23
> **AndrewRiedi said:**
> This will basically behave like the Windows task manager does. 

So wait are you saying that it will throw up errors about killing a process and fail to do so?  ^_^

I don't know if I could handle it if this didn't exactly mimic it's windows counterpart.  Blasphemy.

---

### Post by z0phi3l on 2007-05-23
> **hikaricore said:**
> Threw together a little script for my gf thought it might be useful to someone.

This will kill every threaded process of WoW.exe, leaving winesever untouched.

Useful if you are running more than one app in wine and just want to kill WoW.

```

#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done

```

I must be doing something wrong, made it ,called it ByeWoW.sh but it does nothing, it looks like a shell script to me :/

---

### Post by Pikestaff on 2007-05-23
> **hikaricore said:**
> Threw together a little script for my gf thought it might be useful to someone.

This will kill every threaded process of WoW.exe, leaving winesever untouched.

Useful if you are running more than one app in wine and just want to kill WoW.

```

#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done

```

Awesome, I pasted that into a terminal a few minutes ago upon exiting WoW (and having it hang) and not only did it completely end the program, but it also restored my sound without making me restart X :D Thanks!

---

### Post by hikaricore on 2007-05-23
> **z0phi3l said:**
> I must be doing something wrong, made it ,called it ByeWoW.sh but it does nothing, it looks like a shell script to me :/

```
chmod +x ByeWoW.sh
./ByeWoW.sh
```


Anything now?  :)

---

### Post by DonPeppe on 2007-05-23
Another one with the same problem

Ubunty 7.04 / Wine 0.9.37  Running on an Intel P4 3GHz with 1GB RAM, and nVidia 7500 AGP 512MB.  Using nVidia latest Graphic Driver.

WoW works fine (haven't tested extensively, though I noticed an increase in latency over time), but on clicking exit, I get a freeze, while the sound loops on the background back to the log-in/character selection default.
Wine was also giving the error described by some above before the patch, but it's gone now.  Waiting for a fix from Blizz or the gurus in here...

---

### Post by schnarkle on 2007-05-23
All I get is "Downloading new patch (16KB)..."  and it never downloads anymore.

---

### Post by slayerboy on 2007-05-23
> **hikaricore said:**
> Threw together a little script for my gf thought it might be useful to someone.

This will kill every threaded process of WoW.exe, leaving winesever untouched.

Useful if you are running more than one app in wine and just want to kill WoW.

```

#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done

```

You are a genious!  This is even better!  I just created a launcher on my panel (since I can always alt-tab to firefox since i have that open all the time for thottbot) and just click the button to Kill WoW and it's gone!  w00t!

And the RunOnce.wtf removal worked.  I actually just renamed it just in case.  Seems to work fine now


.:popcorn:

---

### Post by warewolf55 on 2007-05-23
Just as an aside, my in-game performance went down the tubes on patch day. I was getting between 50-70 FPS, after the patch I was lucky to get 20 FPS. I suspected the addons, disabled them all, and viola things picked up. Since I'm on a dual-boot machine, I bit the bullet and rebooted into winblows, performed the 50 or so patches and updates because I haven't used it in 6 months, rebooted twice more to finish the patches and finally went out to:

WorldofWar.net --> [http://ui.worldofwar.net/ui.php?id=2106](http://ui.worldofwar.net/ui.php?id=2106)
WowAce.com --> [http://www.wowace.com/wiki/WinAceUpdater](http://www.wowace.com/wiki/WinAceUpdater)

There are 2 utilities there that I used to upgrade all of my addons. It took about 30 minutes or so to update everything, I rebooted to Ubuntu, copied the addons folder from winblows to my wine directory, and now my performance is back up around the 50 FPS mark.

While this helped me tremendously in-game, it did not fix anything with the hanging exit. I still CTRL+ALT+LArrow, open a console, and run 'wineserver -k'. It kills everything nice and easy.

Moral of this story: Update your addons if you are having a lot of in-game issues. It may just fix it all for you.

---

### Post by shnastybiznastic on 2007-05-23
> **hikaricore said:**
> Threw together a little script for my gf thought it might be useful to someone.

This will kill every threaded process of WoW.exe, leaving winesever untouched.

Useful if you are running more than one app in wine and just want to kill WoW.

```

#!/bin/bash

for i in $(pidof WoW.exe); do
    kill -9 $i && sleep 1
done

```

High five and a half!  Now if only there was some way to send /console updateui to wow through a script we wouldn't even need a fix.

---

### Post by thom_raindog on 2007-05-24
Have you guys read the thread at the WoW-website that was linked here? The guy there seemed to have solved his problem... unfortunately he didn't really share how he did it...

And thanks to those genious monkeys at blizz messing something up I can't log into the forum right now.. since I can still log into WoW fine it beats me why....

Can anyone log into the forums there and ask the guy to share his wisdom?

Just for the record:
I have the same problem here. I use the script provided here to kill WoW and it works marvels.. great job, also on the RunOnce.wtf thing..

---

### Post by hikaricore on 2007-05-24
Glad everyone's found use for the script ^_^

thom: did you mean this page on the WoW forum?  [http://forums.worldofwarcraft.com/thread.html?topicId=105970623&postId=1056811154&sid=1#3](http://forums.worldofwarcraft.com/thread.html?topicId=105970623&postId=1056811154&sid=1#3)
because I don't see even a vague mention of a solution there.

---

### Post by beeldings on 2007-05-24
This problem is affecting me, too. I am playing WoW through CrossOver Office Standard 6.1 on Ubuntu Feisty Fawn and I experience the lock-up issue when closing the program. Like someone else posted earlier, I also had issues with the patch not downloading through the Launcher (the download would freeze 16kb). I solved this problem by downloading the patch from [FileFront]("http://files.filefront.com/WoW+The+Black+Temple+2012+to+210+US+Patch/;7576118;;/fileinfo.html"). If it helps diagnose the problem, running WoW on AMD Athlon 64 3200+ 2.2 Ghz, 2 GB DDR RAM, NVIDIA GeForce 7800 GS AGP.

---

### Post by Tellisk on 2007-05-24
Okay, my problem (choppiness) still isn't resolved and in my search, I discovered I do not have the latest version of Wine. My version (according to winecfg) is 0.9.30. This is the only version I see in Synaptic and nothing appears in the Update manager. Is 0.9.37 only for Feisty? Or is there a terminal command to upgrade wine to the latest version on Edgy?

---

### Post by Pikestaff on 2007-05-24
> **Tellisk said:**
> Okay, my problem (choppiness) still isn't resolved and in my search, I discovered I do not have the latest version of Wine. My version (according to winecfg) is 0.9.30. This is the only version I see in Synaptic and nothing appears in the Update manager. Is 0.9.37 only for Feisty? Or is there a terminal command to upgrade wine to the latest version on Edgy?

I have the latest version (0.9.37) and I'm on Dapper... I installed it via the [instructions on Wine's website]("http://www.winehq.org/site/download-deb"), so you might try that.  (perhaps adding Wine's official repository will allow you to get updates?  I get Wine updates myself pretty regularly.)

---

### Post by Tellisk on 2007-05-24
Oo thanks. I wasn't sure about the instructions on Wine's site because they don't say anything about updating, so I kind of assumed they were for fresh install and didn't want to risk further messing up of things.

Thanks again, I'll try it.

Edit: Ok I followed the instructions but still only see 0.9.30 in Synaptic. The sudo apt-get command seems to be working to install .37 though so all seems good.

---

### Post by The Squig on 2007-05-24
hmm the latest patch works fine for me on fiesty. guess im lucky :/

---

### Post by Tellisk on 2007-05-24
Yep, just as I expected. No difference in performance at all. Oh well, I'm glad to have the latest versions of everything now =P

---

### Post by warelf on 2007-05-24
> **The Squig said:**
> hmm the latest patch works fine for me on fiesty. guess im lucky :/

Have you done a fresh install after the patch, or you just patched up as normal and everything works fine? 
No freezez on exit?

Yeah, lucky you, probably the only person that have it working :D

---

### Post by Flump5000 on 2007-05-24
why would you want to play WoW anyway? i had it for three months and i never went back. it is so incredibly boring. i honestly cant see what makes people like it so much. even if i didnt have to pay $100 or whatever it is to play for a year i wouldnt play it.

---

### Post by Pikestaff on 2007-05-24
> **Flump5000 said:**
> why would you want to play WoW anyway? i had it for three months and i never went back. it is so incredibly boring. i honestly cant see what makes people like it so much. even if i didnt have to pay $100 or whatever it is to play for a year i wouldnt play it.

I just started playing about a month ago, my boyfriend suggested we use it to roleplay together and I have to admit it's kind of fun to do that :p (Yes, I know we're huge geeks)

---

### Post by hikaricore on 2007-05-24
> **Pikestaff said:**
> I just started playing about a month ago, my boyfriend suggested we use it to roleplay together and I have to admit it's kind of fun to do that :p (Yes, I know we're huge geeks)

Lol the opposite effect it has on most people's lives.  Usually WoW destroys them.  ^_^

---

### Post by drlabel on 2007-05-24
I have the same prob since last patch freze on exit but the rest is fine ....

> **Pikestaff said:**
> I just started playing about a month ago, my boyfriend suggested we use it to roleplay together and I have to admit it's kind of fun to do that :p (Yes, I know we're huge geeks)


lol i have done the same to my girl this way i can play and don't have to go shoping :p ( this is my way to save money...)

---

### Post by lightfly on 2007-05-25
> **graigsmith said:**
> k, I'm having the same problem. crash on exit.  it also occasionally HARDLOCKS my whole system. I'm using an ati 9200 with the open source drivers, and despite somewhat poor framerates, i haven't had any problems running it with the last patch.  This patch is messed up i think.

also, i am getting wierd texture problems when i zoom away from my character, gonna try disabling Level of detail. if i can log in. wont even let me.

edit, im gonna see if i can get rid of my hardlock problem by upgrading to the newest wine version.  ugraded to newest version, STILL hardlocks. seems to hardlock, after this sequence of events. run wow, exit wow, kill wow because it crashes.  try to run again, system hardlocks.

Hi

I have a very similar Problem. everytime wow freezes, the whole system freezes. Either CTRL + ALT + Backspace or ctrl + alt + f1 will work -> i have to hit the reset button :(

the funny thing is, skype still works even when system freezes.

also funny, wow is still able to write the logfile in the wow error directory, but the error report is not complete, it breaks at Line

--------------------------------------------
Stack Trace (Using DBGHELP.DLL)

i renamed the file, to see if it causes the freeze ->  hole system still freezes when wow crashes


is it possible that the memory dump / blizz error reporting tool causes the system freeze?


btw. i use feisty fawn, had never bevor problems with wow....

---

### Post by sams2100 on 2007-05-25
Lightfly:  That is a very good comment about the blizzard debugger causing the freeze.  Since it has been such a long time between WoW patches, they may have snuck in some new code for that part and opened up a new problem with Wine.  And then the problem with Wine causes problems with video drivers that cannot handle a killed 3d process (ATI drivers dont like for the 3d input to abruptly stop, they prefer things to stop gracefully)

Another problem I have not seen people mention yet, but is happening to me, so I'm assuming it will probably happen to someone else if they try it, is that my WoW will lock up whenever I adjust the volume using the keyboard volume controls.  This only freezes WoW when I have ALSA selected in winecfg... if I set it to use OSS instead, it works fine, but of course then Wine holds onto my sound card and I cannot play mp3's.

---

### Post by Migs on 2007-05-25
> **sams2100 said:**
> Lightfly: That is a very good comment about the blizzard debugger causing the freeze. Since it has been such a long time between WoW patches, they may have snuck in some new code for that part and opened up a new problem with Wine. And then the problem with Wine causes problems with video drivers that cannot handle a killed 3d process (ATI drivers dont like for the 3d input to abruptly stop, they prefer things to stop gracefully)
 
Another problem I have not seen people mention yet, but is happening to me, so I'm assuming it will probably happen to someone else if they try it, is that my WoW will lock up whenever I adjust the volume using the keyboard volume controls. This only freezes WoW when I have ALSA selected in winecfg... if I set it to use OSS instead, it works fine, but of course then Wine holds onto my sound card and I cannot play mp3's.
 
Did you ever tried ALSO-OSS? Look at te WoW wiki section [COLOR=red]voicechat[/COLOR]. 
 
link: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by yeti.man on 2007-05-25
Has anyone submitted this as a bug for wine?  (Submitting it as a bug to Blizz won't go anywhere.  They don't officially support linux.)

---

### Post by yeti.man on 2007-05-25
Can someone else try this to verify it is what was wrong:

I was using OSS as the sound system, but getting bad lag and interrupts.  I switched to ALSA and the lockup on exit has gone for me.

run 'winecfg' from the command prompt, and change sound system from OSS to ALSA and try it.

---

### Post by rjwboys on 2007-05-25
humm i was haveing the exit freezing bug but then i got 42 updates with the ubuntu package manager and i no longer have the exit freezing :popcorn::p
one of the updates was to nvidia if that helps lol

---

### Post by laffys on 2007-05-26
well yuppers it worked for me to. I went into winecfg and audio then changed a to o. then the freeze on exit not there any more. all normal.

---

### Post by kano on 2007-05-26
The exit bug also has disappeared for me. I'm not running Ubuntu on this box, and the only updates I've gotten today that could in anyway be related are alsa-utils and alsa-libs.

Perhaps it's just a coincidence and blizzard hotfixed the problem without us knowing?

---

### Post by ImNeat on 2007-05-26
O -> A confirmed.  Much thanks!

---

### Post by thom_raindog on 2007-05-26
> **hikaricore said:**
> 
thom: did you mean this page on the WoW forum?  [http://forums.worldofwarcraft.com/thread.html?topicId=105970623&postId=1056811154&sid=1#3](http://forums.worldofwarcraft.com/thread.html?topicId=105970623&postId=1056811154&sid=1#3)
because I don't see even a vague mention of a solution there.

No, my mistake. But in that thread there is a link to [**this** ](http://forums.worldofwarcraft.com/thread.html?topicId=104597655&sid=1) thread and there the guy Zorak claims he solved his own problem...

As did I by the way. for me, deleting the Config.wft did it. with the fresh one, WoW runs smooth and shuts down like it should... go and try it.

---

### Post by stefan.pasat on 2007-05-26
i have an issue too.

I had the problem of wow crashing alter the eula and tos ... but i deleted the ReadOnce.wtf and now i can login but i have a terible loss in performance.

if i have the DisabledExtensions set in the wine registry then  i get a system freeze imidiatly after I enter the game world.

i tryed ALSA and OSS and with bouth the soud is terrible(lots of breaks in the sound).

so any1 has any ideea on how can i get wow running smoothly again ??

my system:
celeron: 2G
ram: 1G
video: ati radeon 9600
wine: 0.9.37
ubuntu 7.04
fglrx OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by Pikestaff on 2007-05-26
> **yeti.man said:**
> Can someone else try this to verify it is what was wrong:

I was using OSS as the sound system, but getting bad lag and interrupts.  I switched to ALSA and the lockup on exit has gone for me.

run 'winecfg' from the command prompt, and change sound system from OSS to ALSA and try it.

Awesome, that worked for me as well.  Thanks!

---

### Post by lightfly on 2007-05-26
i've tried Alsa, system still freezes....

---

### Post by cmon on 2007-05-26
> **yeti.man said:**
> Can someone else try this to verify it is what was wrong:

I was using OSS as the sound system, but getting bad lag and interrupts.  I switched to ALSA and the lockup on exit has gone for me.

run 'winecfg' from the command prompt, and change sound system from OSS to ALSA and try it.


Oyeah!! This fixed my lockup problems upon exit. Many thanks :D

---

### Post by infamous on 2007-05-26
also here with alsa the game doesn't hang on exit anymore!

thanks

---

### Post by drlabel on 2007-05-26
Done notting but today the problem was gone .... I think that the problem was server side ....

---

### Post by slayerboy on 2007-05-27
> **drlabel said:**
> Done notting but today the problem was gone .... I think that the problem was server side ....

exactly my experience...I think it was server side and was fixed without any need for a patch.  The game exits perfect for me now without having to do anything.

---

### Post by ShadowFlar3 on 2007-05-27
Same here allthough I did fiddle with some settings, but I didn't change from OSS to ALSA, so be sure to use the one that works better for you, should not affect the crash-on-exit bug.

---

### Post by cmon on 2007-05-27
> **slayerboy said:**
> exactly my experience...I think it was server side and was fixed without any need for a patch.  The game exits perfect for me now without having to do anything.

I think you're right. I changed back to the OSS driver and my WoW is still running fine.

---

### Post by thom_raindog on 2007-05-28
> i have an issue too.

I had the problem of wow crashing alter the eula and tos ... but i deleted the ReadOnce.wtf and now i can login but i have a terible loss in performance.

if i have the DisabledExtensions set in the wine registry then i get a system freeze imidiatly after I enter the game world.

i tryed ALSA and OSS and with bouth the soud is terrible(lots of breaks in the sound).

so any1 has any ideea on how can i get wow running smoothly again ??

my system:
celeron: 2G
ram: 1G
video: ati radeon 9600
wine: 0.9.37
ubuntu 7.04
fglrx OpenGL version string: 2.0.6334 (8.34.


Did you try 
```
mv Config.wtf Config.wtf.backup
```
and starting the game then? It certainly helped me...

---

### Post by ShadowFlar3 on 2007-05-28
Resetting config makes your wow start in d3d mode instead of opengl which is definetly not good for performance. You should make a new config.wtf and only include the following lines:

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxRefresh "60"
SET gxApi "OpenGL"
SET gxResolution "1280x1024"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"

Set resolution, color and refresh rate settings to the same you have on desktop and you should be fine. Last 2 should fix your sound issues. (Set wine to OSS with those) For more tweaks check [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

And BTW I think you have mispelled something in the registry if the fix makes your game crash, that shouldn't happen. Note that everything in the registry is CaSe SenSiTiVe.

---

### Post by drlabel on 2007-05-30
after today mini patch is crashing again ...
grrr 
In D3D mode is fine no crash ... but we need to play in OpenGL mode :(

---

### Post by drlabel on 2007-05-30
I was wrong we exit afther 1 minute or 2 :(

---

### Post by ShadowFlar3 on 2007-05-31
You mean crash on exit? Worked fine for me when I did it 30 mins ago both in-game and on the login screen.

---

### Post by crocodin on 2007-06-06
> **schnarkle said:**
> All I get is "Downloading new patch (16KB)..."  and it never downloads anymore.

I had the same problem. I fixed it simply by downloading the patch from another source and installing it by myself.

You can find the latests patches here: [http://www.filesforplayers.com/wow/](http://www.filesforplayers.com/wow/)

---


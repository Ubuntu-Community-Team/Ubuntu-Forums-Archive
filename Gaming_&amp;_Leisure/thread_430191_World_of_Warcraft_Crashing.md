---
title: "World of Warcraft Crashing"
date: 2007-05-01
forum: Gaming &amp; Leisure
---

### Post by Torrgan on 2007-05-01
Hey Everybody,

I have feisty fawn installed on my laptop (Inspiron 5150) and i am trying to get World of Warcraft working on my laptop.

I followed the howto at the wiki:  [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

What happens right now is that I can start the game fine, i log into the servers and i can select to play my character.  at the loading screen (before you log onto the game server) the status bar at the bottom goes about halfway across and then stops.  Once this happens my mouse freezes as well.  Once this happens i am forced to restart my computer by holding down the power button.

Any ideas?

Thanks

---

### Post by willskills on 2007-05-02
A similar thing is happening to me, and I think it might have been an nvidia update of some kind the other day..... will need to investigate !

---

### Post by Ferrat on 2007-05-02
Have you tried logging on to another char and tried creating a new one? see if you get in the, if you do it's most likely a corrupt MPQ file

---

### Post by willskills on 2007-05-02
> **Ferrat said:**
> Have you tried logging on to another char and tried creating a new one? see if you get in the, if you do it's most likely a corrupt MPQ file

I think this might be the case actually, I shut down the other night fine, and I didn't think I'd installed any updates; it's kind of annoying though, this is the second time that's happened in about 2 months. (corrupt .MPQ files, I mean)

The first time I loaded from a cold boot, my character actually loaded (i.e. I was in game) - but the char model wasn't rendering, just the shadows, and then WoW hung. Now when I start WoW, it hangs at the loading screen.

One thing I'd like to ask as a side note, if WoW hangs, I am trying to kill it using killall, like so; (otherwise I just restart X, but this often leaves WoW in it's hanging state and I have to reboot)

sudo killall <process ID> /home/will/games/WoW/WoW.exe - (process ID from "ps aux") - and it always returns "no process killed"!

What am I doing wrong? :)

---

### Post by willskills on 2007-05-02
Ok, so I don't think my install was corrupt. I copied over a clean client from my flatmate's pc, and ran it again, and, it hung again ;'[

So I fired up regedit, and WoW had created a load of entries and something in there obviously broke.

Anyway - I just deleted the WoW entries in HKEY_CURRENT_USER\Software\Blizzard Entertainment

When I started WoW, it ran - hooray :)

---

### Post by AndrewRiedi on 2007-05-02
Generally use ```
wineserver -k
``` to kill all your Wine programs.  If you use the system ones, it could potentially cause some damage to the registry, cause ghost processes, etc.  It is also a bit more tedious as you have to look up the PIDs.

---

### Post by Torrgan on 2007-05-02
ok so i tried removing those reg entries that you said helped and i also tried creating a new character from scratch, the loading screen got all the way accross this time so it looks it at 100%, but then the Music stopped and the mouse stopped moving again.

Any other ideas?  I guess its not a corrupt MPQ because i tried creating a new character.  

But once the computer gets in this non-responsive state, aka the mouse not moving is there anyway i can get to a command promt and kill the process? i haven't been able to figure out how

---

### Post by Torrgan on 2007-05-02
also... I just tried to run it again and my mouse crashed before i even got into WoW here's what i see in the terminal from wine:

i ran wow with this command: wine WoW.exe

fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4, 0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c, 0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc, 0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544, 0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530, 0x00000000), stub!
fixme:system:SystemParameteresInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)

it seems random when the crash happens, but once it happens i can't seem to recover the computer... any ideas?

Also, when i installed i installed using CD's, not copying an existing install.

---

### Post by willskills on 2007-05-03
Well, you should be able to do this to kill WoW; Press Alt + Ctrl + D - this will minimize everything to desktop, open a terminal.

sudo killall WoW.exe

As to your crashes, I'm not really sure, like I said in my last reply, I waited while WoW hung (for about ~30mins) - and the WoW client eventually crashed and gave me an error report.

See if you can get that, then pastebin it, and post it here, and we'll try and help you out :D

---

### Post by Torrgan on 2007-05-03
WoW crashed again when i tried to log in at the end of the loading screen, and my computer went unresponsive.

I tried to do Alt + Ctrl + D as you suggested but that did nothing.  It seems that wow crashing locks my entire computer so i must hold down the power button.

I also left the computer for about 5 hours to see if wow would come back eventually with an error report, no dice.

---

### Post by cesium062 on 2007-06-03
It sounds like maybe you need to use 'alt-tab' to switch out of the warcraft screen and back to the non-wine desktop.  I'm also having this problem.  When a crash occurs, warcraft will write 2GB of data out to disk via Wine.  

To kill a process or processes, you would normally use either "kill -9 <pid>", or "killall processname".  But don't try to mix the syntaxes.  ('killall processname' is a relatively new syntax, so google "man killall" to figure out what I'm lying about.)

Cs

---

### Post by Pianospider on 2007-06-06
hi Torrgan, i am having a simlar problem while trying to log onto the world.
i have followed steps for every HOW-TO , adressed every problem , tried every single fix mentiond.
been at this for days. i can log on, select my character and then about 50-70 percent loading it freezes, the mouse locks, the sound stutters, i basically hit cntrl alt esc, alt tab, until i can hit log-off. sometimes when logging off i can still here the sound stuttering at the screen where it prompts you to choose beteween KDE and GNOME etc. i am fairly new to Ubuntu and Linux and i must say that i enjoy it. i admire the community here and not really looking forward to going back to windows. so its either not play wow or go back to windows. 
just dropping by here to let you guys know that i am having the same problem with trying to log in to the world.
i have never been able to log onto the world yet. i tried deleting registrys as suggested, after that i ran wow and the opening movie was white, i could hear sound perfectly but see no video. so i hit esacape and stll couldnt log on. i appreciate alll these people trying to fix this. keep us posted

---

### Post by Nkari on 2007-07-15
I have a  problem somewhat like your having with the not being able to get in to the actual world, however in my case the progress bar does not move at all before it freezes up

Did the movies work properly before the registry entrys were deleted?

My movies work really well, but I just can't get into the world, was thinking I might give that a go since that seemed to allow you to get in where you previously couldn't. 

But i'm not sure I want to do something that might not help if it might also make things way worse.

Also did you find that when you were crashing trying to get into the world that if you went to character creation and changed race or class that it would freeze up too?

---

### Post by acconrad on 2007-07-15
This just happened to me as well - I think this is a problem with the new patch...my console is reporting the following log, which keeps repeating in the console:

fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 191


So new patch + WOW = problems?

---

### Post by Nkari on 2007-07-16
I don't know if it is the new patch or not, I only installed it on the weekend, and that is since the latest patch, I have no idea of what it was like prior to this patch.

Interesting

---

### Post by Sandlst on 2007-07-16
Hey guys, sorry to hear you are all having so much trouble.  Wow is currently working for me fine, latest patch included, so I doubt thats the main problem.  Errors while in the loading screen are the worst, since in my experience atl-tabbing, console, and workspace switching all do not work until the loading bar is complete. 

 It might help us to know what kind of graphics card you all have (on my computer's nvidia card, wow works flawlessly, but on my friend's card (intel) it refuses to work at all).  

Besides that, it might be good to try to run it without editing the registry (at first) just to see if thats the problem.  The easiest way to do this is to copy your wow directory (unless you want to reinstall!) to your home folder, then delete the entire .wine folder, then open a terminal and run ```
winecfg
```in order to get a fresh new one (note you can run wow from anywhere, it does not have to be in ~/.wine/drive_c/Program Files/).

---

### Post by acconrad on 2007-07-17
hmmm well WoW worked fine until the new patch...so...

---


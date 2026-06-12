---
title: "Compiz, PulseAudio and Latency; why Linux gaming sucks"
date: 2008-10-27
forum: Gaming &amp; Leisure
---

### Post by Wertigon on 2008-10-27
Hi.

Writing this here, in the vain hope of getting someone's attention to this. I have a couple of pet peeves to bring up, with regards to gaming. This might very well just be me having bad luck/bad setup, if so I apologize. However, I see two things very much broken;

1. Compiz. Compiz in and of itself is wonderful. However, it still doesn't play nice with OpenGL-apps. Trying to fullscreen a game while having multiple workspaces leads to strange results - for instance, trying to run the game bzFlag while having Compiz on leads to both applications fighting for dominance over the desktop and lots of flickering. I can run windowed games, but it's far from an ideal situation, and what's worse - should the game happen to have GTK or QT menus, they will flicker, as well. This might very well just be a driver issue though, I'm running an Intel card and any suggestions to fixing it would be welcome.

2. PulseAudio. It makes sound in games lag. No problems when it comes to music - for sound effects though, I get atleast 100-200 ms lag, and it SUCKS. Try hitting something with a sword and hear the hit effect appear around 0.2s later than it should, and you'll understand why this is a gripe. It also means less reaction time if you, say, play an FPS and hear a rocket explode right behind you. The only suggestions to solutions I've seen is to either use pasuspend (which sorta sucks, since I can't play background music or hear when an IM contact is trying to reach me) or to use SDL, which sorta suffers from the same problem.

These two things make the Linux Gaming Experience a very much crippled one and need to be fixed as soon as possible. The Compiz issue is the most grave one. Any ideas on fixes?

---

### Post by Perfect Storm on 2008-10-27
> 1. Compiz. Compiz in and of itself is wonderful. However, it still doesn't play nice with OpenGL-apps. Trying to fullscreen a game while having multiple workspaces leads to strange results - for instance, trying to run the game bzFlag while having Compiz on leads to both applications fighting for dominance over the desktop and lots of flickering. I can run windowed games, but it's far from an ideal situation, and what's worse - should the game happen to have GTK or QT menus, they will flicker, as well. This might very well just be a driver issue though, I'm running an Intel card and any suggestions to fixing it would be welcome.

Use fusion-icon or make a launching script will do the trick.

> 2. PulseAudio. It makes sound in games lag. No problems when it comes to music - for sound effects though, I get atleast 100-200 ms lag, and it SUCKS. Try hitting something with a sword and hear the hit effect appear around 0.2s later than it should, and you'll understand why this is a gripe. It also means less reaction time if you, say, play an FPS and hear a rocket explode right behind you. The only suggestions to solutions I've seen is to either use pasuspend (which sorta sucks, since I can't play background music or hear when an IM contact is trying to reach me) or to use SDL, which sorta suffers from the same problem.

Pulseaudio is so much better in 8.10 just wait some days (31 oct.) or switch to another audio. 

> These two things make the Linux Gaming Experience a very much crippled one and need to be fixed as soon as possible.

No problem at all and a play **alot** of games on Linux.

But ranting here would not get you far, as those people behind the diffrent stuff rarely or never reads this board.

---

### Post by Wertigon on 2008-10-27
I do run 8.10. Still get 200ms lag in games, but yes, PA is lots better now atleast. Now, if only I could increase the master volume somehow...

As for Compiz, the only workaround is to disable it then? No plans on fixing the broken-ness of it?

---

### Post by Azure.Rise on 2008-10-27
Not hard to disable and re-enable.

metacity --replace (disable)
compiz --replace (enable)

Just type that in the command line. I'm getting a bit of sound lag in Doom 3 although it has significantly improved, probably due to updates to Ubuntu. Also had sound lag in Quake Wars, but I fixed that. I'll try fixing the sound lag in Doom 3 today. All my other games work fine.

---

### Post by eragon100 on 2008-10-27
Compiz is going to be fixed in the next xserver version with DRI 2, which is due out coming janaury, and will be included in ubuntu 9.04.

I don't have any pulseaudio problems at all myself, 5.1 surround sound works (with bass effects) and there is no lag at all :)

---

### Post by Yfrwlf on 2008-11-07
> **eragon100 said:**
> Compiz is going to be fixed in the next xserver version with DRI 2, which is due out coming janaury, and will be included in ubuntu 9.04.

I don't have any pulseaudio problems at all myself, 5.1 surround sound works (with bass effects) and there is no lag at all :)

Too bad the only way they offer to install it is through source packages, and otherwise you have to wait around to do an entire distro upgrade.  I'm glad the newer X server addresses performance issues though, will be cool to see.

About sound lag though, Pulse Audio still has a pretty crazy lag at times.  Neverball has a slight lag.  Freedoom and Secret Maryo Cronicles have fairly significant lags.  Open Arena does too...so, basically anything that uses Pulse Audio.

Now, I'm definitely no PA expert, so maybe these programs are using the "old ALSA way" or SDL or whatnot and perhaps PA has features available to really decrease lag times but these programs just aren't using those features, no clue.

I remember when PA was first starting to take off though, how one of the big features being touted was the great, nearly lag-less performance.

---

### Post by 3rdalbum on 2008-11-07
I never used to get pulseaudio lag with Ubuntu 8.04 32-bit. Now I get it with 8.10 64-bit. This bites. I just removed Pulseaudio and installed Esound.

---

### Post by xanas3712 on 2008-11-10
I get pulseaudio lag, but using oss4 there is no lag at all.  Only one issue I have had with oss4, and that's that the sound in wine on starcraft kicks out after 1/2 sec or so.  Other games (warcraft 3/wow/etc. ) have sound that works just fine, so not sure what the deal is with starcraft.

---

### Post by epitaph on 2008-11-11
In my foray into gaming on Ubuntu in the past week or so I have kind of made similar conclusions.

Using scripts to launch games that disable and re-enable compiz is necessary. I found that there were multitudes of zombie compiz.real processes lurking, though, so I have the scripts make sure compiz is gone before it's launched again when the game closes.

I do not like Pulseaudio at all. I was having a plethora of issues with crackling sound, lagging sound, no sound... I'm sure there's someone out there yelling "yeah, you just forgot to set that up right". After I completely removed Pulseaudio and stuck with alsa I've had no problems. Most issues can be solved by using the OSS wrapper or executables that use SDL, I've found.

A huge issue for gaming that I am still fighting is the mouse. Using "xset m 0 0" and disabling dgamouse has helped quite a bit, but I still have mouselag when I swipe the mouse quickly to make a reaction shot. It's like the buffer fills and then it has to "catch up". At least with dgamouse disabled it simply skips instead of buffering then lagging for 3 seconds to catch its breath. I'd like to see an option in the Mouse menu under preferences to just "Kill all acceleration".

Over all, I wouldn't say Linux gaming sucks. Expectations from experiences on Windows are hard to meet, but with patience and compromise I've found it to be nearly equal for the games that matter most to me.

---

### Post by Riqz on 2008-11-11
> **3rdalbum said:**
> I never used to get pulseaudio lag with Ubuntu 8.04 32-bit. Now I get it with 8.10 64-bit. This bites. I just removed Pulseaudio and installed Esound.



i did the same and it's the best thing i've ever done tbh..

Although i'm not very impressed with ubuntu's sound overall... It's the only negative point i have with it... Very poor.
I had problems with flash 10 on firefox... no sound...
I still have problems with skype, sometimes accepting the sound output sometimes not letting me answer calls because there's something wrong with the output...
It's very random... And installing esound solved the Flash10 problems... now i'm scared that with any update in ubuntu the pulse audio will be reinstalled or something will be changed and i'll have to make a total reinstall to restore the system sound settings.

---

### Post by Yfrwlf on 2008-11-16
So far, I've had to kill Pulse Audio in order to play Wine games correctly.  Each time, Pulse Audio would cause sound cracks in both Spore and Wizardry 8 and probably other Wine games as well of course.  After killing either Pulse Audio or choosing OSS for the Wine sound option, things would work great.

---

### Post by Vadi on 2008-11-16
Eh, I disagree with Linux gaming sucking, after seeing the horrid effects of alt+tabbing in Windows.

---

### Post by doorknob60 on 2008-11-16
> **Vadi said:**
> Eh, I disagree with Linux gaming sucking, after seeing the horrid effects of alt+tabbing in Windows.

Or unintentionally pressing the Windows key...I hate that :-P

---

### Post by Vadi on 2008-11-16
I don't know what does that do, but I heard people curse at it. Also outlook...

---

### Post by Yfrwlf on 2008-11-16
> **doorknob60 said:**
> Or unintentionally pressing the Windows key...I hate that :-P

Erm, the ability to minimize or escape out of a full screen game is a really nice feature, one that I wish X.org or the window manager or whatnot would implement or implement better.  One of the most frustrating things about Linux gaming is trying to explain to someone who doesn't know how to use the command line what to do when a game freezes right after you've explained to them how Linux is so stable that it doesn't crash your whole machine usually (except in graphics driver cases, which is really annoying).  Linux still needs an easy/graphical way of escaping from messed up programs.  Sometimes Control + Alt + Arrow keys or even Alt Tab or other things will allow you to switch out of it but most of the time those keys are locked out and you're stuck except for switching to a terminal.

So, don't complain about nice features. :P  Yes, I agree the super key should be protected and can be annoying, as long as you can configure the hot keys that'll be fine.  Control + Alt + Arrow or some complex combination like that should be allowed to function all the time even in games as a rescue system.  There needs to be **some** kind of bail out key command that cannot be silenced by an application.

P.S., alt-tabbing or getting out of a full screen game could easily be cursed in Linux too also if it ever makes the screen so small after a crashed game that they have trouble trying to change the resolution back to what it used to be.  Sometimes you have to alt-click on the windows just to see the apply/OK button, something that shouldn't be required to know.  Maybe the new versions of GTK+ have fixed this problem and now have dynamic windows or now have scrolly bars on their windows if you can't see everything or something, I'm not sure.

---

### Post by Vadi on 2008-11-16
It's not about gtk, it's about the games not quitting properly

Try playing a game that has good linux support like savage 2. you'll be amazed at what a good implementation does

---

### Post by Yfrwlf on 2008-11-17
> **Vadi said:**
> It's not about gtk, it's about the games not quitting properly

Try playing a game that has good linux support like savage 2. you'll be amazed at what a good implementation does

Programs can freeze, bugs will always exist and can happen.  Many games aren't "implemented correctly" apparently, but even if they were, bugs still exist and will always.  So, yes, there is a big reason to have a bailout system so that Linux users aren't forced to reboot their desktops when something bad happens.  Windows has it, Linux needs one too.

Telling someone that they don't need the "kill" command and to uninstall it because all programs, if "implemented correctly", should work flawlessly so they should never need it, would be the stupidest thing ever.  Of course desktop Linux needs graphical kill tools, I can't tell you how many times I've used the force quit icon and so have others who use Linux, and right now unless you can get back to your desktop, you can't use them, so there needs to be some kind(s) of override function(s) to escape a frozen full screen app.

If you disagree, because you've never run a program that froze on you like that, you're a one-off, trust me.

I mean, that's the kind of logic Microsoft might use to justify their lack of features, but not Linux.  Linux should be intelligently designed from the ground up to account for things like programs freezing, and it has been for console users, but not for graphical users, not yet any way.

---

### Post by Dedoimedo on 2008-11-17
Hello,

You can use the simple compiz configuration settings manager to quickly enable/disable compiz when needed.

Install simple-ccsm (via synaptic).

Launch it when needed (menu > system > simple ...) and then enable/disable compiz...

Maybe this is satisfactory for you?

Dedoimedo

---

### Post by falkTX on 2008-11-17
About the compiz fullscreen bug, I noticed something weird.
When I run gnome (normal ubuntu installation) I have that bug (really annoying), but If I install kubuntu (KDE variant), even with real compiz enabled (not the KDE effects), I don't get that bug anymore.

I used Intrepid for this (Beta), so I don't know if it was been fixed when used gnome or not

---

### Post by Vadi on 2008-11-17
That's impossible because that is the ATI driver problem.

ATI driver doesn't care if you run one DE or another. It's simply incapable of handling two overlapping openGL applications properly, resulting in flickering.

---

### Post by QuickBrownFox on 2008-11-21
I agree with the original post that these problems should be fixed, and it looks like things are moving in that direction, but for now trying using compiz-switch (google for the .deb) for a gnome panel one-click toggle for compiz, and you can kill the pulseaudio process before starting a game. A quick way to do this would be to have the System Monitor gnome applet enabled and then click on that to open the system monitor window to do it. If alsa is configured properly then the game's sound should work. Of course you will have to enable pulseaudio (Alt+F2: pulseaudio) again in order to experience its benefits after quitting the game. Hope that helps.


> **Vadi said:**
> It's not about gtk, it's about the games not quitting properly

Try playing a game that has good linux support like savage 2. you'll be amazed at what a good implementation does

The quality of linux support is irrelevant in my opinion. Firstly, games running on Wine cannot be expected to provide linux support. More importantly, Gnome should not be relying on another application to set the correct resolution for using Gnome. What if the application crashes? The OS needs to be a bit more intelligent and aware. Here's an idea: if any non-full screen app is in focus then the resolution should be set to default.

[QUOTE=Vadi]That's impossible because that is the ATI driver problem.

ATI driver doesn't care if you run one DE or another. It's simply incapable of handling two overlapping openGL applications properly, resulting in flickering.
[/QUOTE]

But why is the driver being told to overlap two applications when in full screen mode you want it to draw one thing and one thing only. Is that not where the fault originates? If you run a fullscreen app that changes resolution, why is Gnome being drawn at the new resolution at all? Setting the permanent desktop resolution and temporarily changing the resolution for a full screen application should be considered two distinct processes. There may be some fundamental technical reason why this is difficult or impossible with Linux in its current state but even then improvements like this should be considered for the future.

I appreciate that shoddy drivers and applications are often to blame but if the OS can fool-proof (from both developer and user foolishness) these kind of actions, things would be much better.

---

### Post by &amp;co on 2008-11-21
This might help you,

```

X :3 -ac & nvidia-settings --load-config-only
sleep 2
DISPLAY=:3 wine "C:\Program Files\Starcraft\Starcraft.exe"

```

take out the "& nvidia...." bit if you don't have nvidia. You may need to chown some file (I think it was ~/.Xauth something) to do this when you are not root. This way you don't need to switch off compiz at all. Save it under /usr/local/bin/name to get a terminal launch.

Good luck.

---

### Post by Endolith on 2009-01-04
> **epitaph said:**
> A huge issue for gaming that I am still fighting is the mouse. Using "xset m 0 0" and disabling dgamouse has helped quite a bit, but I still have mouselag when I swipe the mouse quickly to make a reaction shot. It's like the buffer fills and then it has to "catch up". At least with dgamouse disabled it simply skips instead of buffering then lagging for 3 seconds to catch its breath. I'd like to see an option in the Mouse menu under preferences to just "Kill all acceleration".

Any luck with the mouse acceleration?  I remember reading years ago about how X mouse acceleration was very simple, with just two speeds that it switches between based on a very simple threshold, which is why the movement is so incredibly jerky.  In a good design, it would be a smooth function that allowed you to jump across the screen quickly but point precisely at small objects.  I wish there were a package you could install to fix this.

I can't say I'm surprised that this hasn't been fixed yet.  In the Linux world, it seems that the typical time to fix a bug like this is 10+ years.

> **Yfrwlf said:**
> when a game freezes right after you've explained to them how Linux is so stable that it doesn't crash your whole machine

Maybe you should stop lying to your friends.  :)  Linux crashes and locks up my machine much more than Windows ever did.  Don't give people false expectations or they'll just give up in frustration and move on.  Linux is only rock-solid stable when used as a server, not as a desktop OS.

---

### Post by Frem on 2009-01-05
> **Endolith said:**
> Any luck with the mouse acceleration?  I remember reading years ago about how X mouse acceleration was very simple, with just two speeds that it switches between based on a very simple threshold, which is why the movement is so incredibly jerky.  In a good design, it would be a smooth function that allowed you to jump across the screen quickly but point precisely at small objects.  I wish there were a package you could install to fix this.

I can't say I'm surprised that this hasn't been fixed yet.  In the Linux world, it seems that the typical time to fix a bug like this is 10+ years.

Wow, you sound ungrateful. Look, if you have a bug and can give enough information to project developers so that they can reproduce it, they can fix it. If your bug report is good enough, fixing it is (usually) a rapid process.


> **Endolith said:**
> Maybe you should stop lying to your friends.  :)  Linux crashes and locks up my machine much more than Windows ever did.  Don't give people false expectations or they'll just give up in frustration and move on.  Linux is only rock-solid stable when used as a server, not as a desktop OS.
Linux is a kernel; ascribe blame to the correct component of your system. As a desktop operating system not running games, Ubuntu's stability is at least on par with Windows Vista is for me. 

Once we start gaming, Vista does crash a lot less frequently than Ubuntu. This is partially because the Intel OpenGL drivers required for my card are incomplete, partially because DirectX covers stuff OpenGL does not, and partially because we're waiting on DRI2.

If you start a fullscreen DirectX app in Vista, it will disable the Aero desktop temporarily; it's basically automatically doing what we currently do when we switch from Compiz to Metacity. From my understanding of DRI2, we're going one better.

---

### Post by jrusso2 on 2009-01-05
> **Endolith said:**
> Any luck with the mouse acceleration?  I remember reading years ago about how X mouse acceleration was very simple, with just two speeds that it switches between based on a very simple threshold, which is why the movement is so incredibly jerky.  In a good design, it would be a smooth function that allowed you to jump across the screen quickly but point precisely at small objects.  I wish there were a package you could install to fix this.

I can't say I'm surprised that this hasn't been fixed yet.  In the Linux world, it seems that the typical time to fix a bug like this is 10+ years.



Maybe you should stop lying to your friends.  :)  Linux crashes and locks up my machine much more than Windows ever did.  Don't give people false expectations or they'll just give up in frustration and move on.  Linux is only rock-solid stable when used as a server, not as a desktop OS.

I can't speak for anyone but myself but I have not had any lockups with Linux.  I use KDE 3.5 and Nvidia and its been rock solid and I use it daily.  Only thing that can lock it up is WINE and that does not seem to happen for  years.

---

### Post by Endolith on 2009-01-05
I found out there's actually a "hidden" mouse acceleration setting in xset.  If you do "xset m 11/8 0", for instance, it will use a smooth acceleration instead of the jerky two-step that it does by default.

see [http://ubuntuforums.org/showthread.php?t=748412#4](http://ubuntuforums.org/showthread.php?t=748412#4)

---

### Post by Growbag on 2009-01-05
This is more of a distro or desktop environment problem than a "Linux" problem though.

Try running your game under a different distro.

I use openSUSE 11.0 with the latest KDE 4.2 beta (all desktop effects supplied by the built in Kwin, as nice as Compiz but less resource hungry and stable for openGL apps), I automatically remove the lousy cancer ridden pulseaudio and my games run perfectly (ET, Wolfenstein, ETQW).

You should be able to remove pulseaudio under ubuntu too, and also remove any "file indexing" software like Beagle, they will slow your system to a crawl.

Also the more desktop gadgets you have will add to pause times, like weather applets etc'.

Of course if you want to go for a "hard core gamer" setup, start with a "server" install and just use xfce!

Spartacus would be proud ;).

---


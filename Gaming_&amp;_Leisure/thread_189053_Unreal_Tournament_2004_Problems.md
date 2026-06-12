---
title: "Unreal Tournament 2004 Problems"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by michaeljb2005 on 2006-06-04
Hi there are a couple of problems with unreal tournament 2004.  I'm running an Inspiron 9300 with an nvidia go 6800 video card.  There are three things that I notice happen.  First when I open the game it only wants to see the size 800x600 using opengl.  It should be seeing 1920x1200 because that is what my monitor defaults to.  In order to solve it I have to switch it to software, switch the resolution and then switch back to Opengl.  Second the graphics are a little choppy ingame whether online or offline.  Third, after a short time my ping goes insanely high to around 200 after having a pretty decent ping for a few minutes.  I'm not sure what's going on here.  I have a pretty high end laptop so it should easily be able to handle the highest quality graphics for this game.  My internet connection also runs at 6 Megabits per second.  So my internet connection also shouldn't be the problem.  I've tested many different servers and the same thing happens.  I've played it in windows and this is not the kind of behavior I get there.  The driver i'm using was installed by automatix, it's the 8762 driver.  Any help would be greatly appreciated.  edit: Also sometimes sound doesn't work when I start the game.

---

### Post by IceAxe18 on 2006-06-04
Go under System, Prefrences, Screen Resolution what does it say? Does it say that you have a screen resolution of 800x600 or do you have it at 1920 X 1200? If you don't see at least that high of a Resolution Selection in your Screen Resolution selection then your Unreal Tournement 2004 won't see it either.

---

### Post by frying_fish on 2006-06-04
Choppy graphics are likely to be due to it not actually being able to render everything well.  try stepping up in stages, and make sure you have the correct xorg setup, using nvidia, rather than nv, as if automatix installed the driver, it probably didn't set it up.

---

### Post by michaeljb2005 on 2006-06-04
[QUOTE=IceAxe18]Go under System, Prefrences, Screen Resolution what does it say? Does it say that you have a screen resolution of 800x600 or do you have it at 1920 X 1200? If you don't see at least that high of a Resolution Selection in your Screen Resolution selection then your Unreal Tournement 2004 won't see it either.[/QUOTE]

Resolution is correct

---

### Post by michaeljb2005 on 2006-06-04
[QUOTE=frying_fish]Choppy graphics are likely to be due to it not actually being able to render everything well.  try stepping up in stages, and make sure you have the correct xorg setup, using nvidia, rather than nv, as if automatix installed the driver, it probably didn't set it up.[/QUOTE]

I tried it with the default less complicated settings and I still get the same problems, 3d nvidia is enabled.  

edit: I just found out that one of the problems was my monitor defaulted to 16bit and so I set that to 24.  But I still get very sluggish performance in game.  I don't know why.  It's not the internet connection.  I can almost guarantee that.

---

### Post by IceAxe18 on 2006-06-04
I don't have anymore ideas then.  I'm sure someone will have the answer.

---

### Post by _simon_ on 2006-06-05
Maybe try patching UT 2004 to the latest version? Mine kept crashing randomly until I patched.

[http://www.unrealtournament.com/ut2004/downloads.html](http://www.unrealtournament.com/ut2004/downloads.html)

Scroll down to patches and click the linux one.

I had to manually copy the files across.

Also, what are your OpenGL settings on?

---

### Post by handy on 2006-06-05
Just feed back to let you know that the **nVidia drivers** via Automatix, or installed manually for Dapper, are not the problem.

I have UT2k4 running VERY fast at 1600x1200 24bit, with everything set to the highest in the games System Settings.  I have had the same excellent result with the Automatix install, & with a manual install of the same nVidia (closed source) drivers.

Someone will crack it for you. :KS

---

### Post by michaeljb2005 on 2006-06-08
i thought I might start up this thread again because I'm still having major problems.  The problems aren't due to lack to my video card, I think I've narrowed it down to sound or network.  But I'm still not sure.  I mean I guess it could just be very choppy due to bad connections to the servers, but i've tried quite a few and I still get the same problem.  It's just very choppy, unbearably so.  Might I refresh that the reason I know it's not my video card is because when I first enter a game it runs very smoothly.  After about 5-10 minutes it slows down tremendously.  Becomes unplayable for about a minute or two and then goes to being just very choppy.

edit:  I'm going to try opening ports that apply to the game and see if firewalling the servers might be doing something.

edit:  That did it!  My ports were firewalling exterior packets and all I had to do was open them!  Woohoo!  It works!  Better than in windows in fact!

---

### Post by pantropik on 2006-06-09
I also have an i9300 and found that a couple of quick changes to xorg.conf *hugely* improve performance.  First of all, make sure you are using 24-bit color and not 16 (this cleared up the stuttering for me).  Secondly, by default your xorg.conf will have ONLY "1920x1200" listed in xorg.conf.  I'm not in front of my Ubuntu system at the moment (playing with Vista, actually), but you should find the appropriate section of your xorg.conf and add something like the following:

In the [Screen] section make sure **DefaultDepth** is set to **24**.  Mine defaulted to 16, so I'm sure yours is, too.

Then, also under [Screen] look for **SubSection "Display"** for Depth **24** and you should see:

**Modes "1920x1200"**

To make sure whatever programs you have installed can switch resolutions freely, change that to something like:

**Modes "1920x1200" "1920x1080" "1600x1200" "1600x1024" "1600x900" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x768" "1280x720" "1152x864" "1088x612" "1024x768" "960x600" "848x480" "800x600" "720x576" "640x480"**

All of that would be one line, of course, and I actually have no idea if all of those resolutions will work with Ubuntu, just that those are the resolutions the 6800 in this laptop will support on the built-in LCD.  Once you make this change and restart X or reboot, the game should run MUCH more smoothly (I play at 1280x800 since it's widescreen and it's very smooth even on a full server).  You'll also be able to choose any resolution you want.

Good luck.

---

### Post by michaeljb2005 on 2006-06-09
[QUOTE=pantropik]I also have an i9300 and found that a couple of quick changes to xorg.conf *hugely* improve performance.  First of all, make sure you are using 24-bit color and not 16 (this cleared up the stuttering for me).  Secondly, by default your xorg.conf will have ONLY "1920x1200" listed in xorg.conf.  I'm not in front of my Ubuntu system at the moment (playing with Vista, actually), but you should find the appropriate section of your xorg.conf and add something like the following:

In the [Screen] section make sure **DefaultDepth** is set to **24**.  Mine defaulted to 16, so I'm sure yours is, too.

Then, also under [Screen] look for **SubSection "Display"** for Depth **24** and you should see:

**Modes "1920x1200"**

To make sure whatever programs you have installed can switch resolutions freely, change that to something like:

**Modes "1920x1200" "1920x1080" "1600x1200" "1600x1024" "1600x900" "1360x768" "1280x1024" "1280x960" "1280x800" "1280x768" "1280x720" "1152x864" "1088x612" "1024x768" "960x600" "848x480" "800x600" "720x576" "640x480"**

All of that would be one line, of course, and I actually have no idea if all of those resolutions will work with Ubuntu, just that those are the resolutions the 6800 in this laptop will support on the built-in LCD.  Once you make this change and restart X or reboot, the game should run MUCH more smoothly (I play at 1280x800 since it's widescreen and it's very smooth even on a full server).  You'll also be able to choose any resolution you want.

Good luck.[/QUOTE]

The problem isn't with the video card.  The game runs very smoothly in the first 5-10 minutes.  I realized I ran the game after letting down the firewall and that when I did there was no sound.  It worked great.  However when I added sound the same old problems came back.  I think the problem is the sound.  I'm not sure how or why but I've pretty much diagnosed everything else as being ok.  For now I'll play the game without sound.  Hopefully I can find a fix eventually.

---


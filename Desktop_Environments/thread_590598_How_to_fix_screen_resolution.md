---
title: "How to fix screen resolution?"
date: 2007-10-24
forum: Desktop Environments
---

### Post by explainer on 2007-10-24
I have a ViewSonic VA1912wb monitor, which has a rather odd 1440 by 900 resolution.  I have an nVidia graphics card, so I use the nVidia restricted driver.

When my machine boots up, it will select 1024 by 768 resolution.  If I use Preferences>Screen Resolution, I don't see a 1440 by 900 choice.  However, if I use the nvidia-settings tool, I can get it to recognize the ViewSonic monitor and can then select the 1440x900 resolution.

I would like to configure the system so that this selection is the default selection at boot time.

Any good ideas?  Can I just put something into xorg.conf?:)

---

### Post by taurus on 2007-10-24
Yes, just add 1440x900 (that is not an odd resolution; it's a wide screen resolution) to the beginning of the resolution section near the end of /etc/X11/xorg.conf.

```
gksudo gedit /etc/X11/xorg.conf
```
Save it and restart X again with <Ctrl><Alt>Backspace.

---

### Post by TeaSwigger on 2007-10-25
> **explainer said:**
> I have a ViewSonic VA1912wb monitor, which has a rather odd 1440 by 900 resolution.  I have an nVidia graphics card, so I use the nVidia restricted driver.

When my machine boots up, it will select 1024 by 768 resolution.  If I use Preferences>Screen Resolution, I don't see a 1440 by 900 choice.  However, if I use the nvidia-settings tool, I can get it to recognize the ViewSonic monitor and can then select the 1440x900 resolution.

I would like to configure the system so that this selection is the default selection at boot time.

Any good ideas?  Can I just put something into xorg.conf?:)

Any luck? 

If not, first things first, is the right nvidia driver actually specified in use in the xorg.conf?

---

### Post by orange2k on 2007-10-25
Much easier than editing the xorg.conf file is choosing the right monitor in graphichs & screens menu...
Worked for me, at least, so in Gutsy I didn`t even view my xorg.conf file...:)

---

### Post by SunnyRabbiera on 2007-10-25
yeh but it didnt have my monitor though... depends on what you have I guess.

---

### Post by explainer on 2007-10-28
Adding "1440x900"  to all the subsections in the "Screens" section of xorg.conf results in the correct resolution for the Viewsonic.  So that much is solved.

However, I use this system on a KVM switch, and the above works ONLY if the KVM is selected during OS boot.  If it is, I see A Viewsonic selection in nvidia-settings at 1440x900.  If the KVM is not selected, then I get at 1024x768 generic monitor, and no option for selection to 1440x900.

Is there any way for me to override the dynamic monitor selection logic and simply tell X that I have a fixed monitor configuration: ViewSonic VA1912wb at 1440x900?

---

### Post by keyboardashtray on 2007-10-28
Man, I'm not a hater, but I'm having a crap day with Ubuntu I gotta say. I thought all this resolution $#!^ was supposed to be wrapped up with Gutsy. I just stumbled upon "screens and graphics" and remembered to try to get the 1280x1024 that I never bothered with in Feisty (i915 headache).

Well, I couldn't do anything driver side, but then tried selecting my monitor (Mag 786) instead of generic - and was psyched to see the blessed 1280x1024. Well, after adjusting all my fonts, panels, etc., it looked like a dream. 

Restarting there was a weird scramble, and the login screen looked kind of funny (password size a little big for the field). Well, dammit anyway - the changes don't stick, I gotta pick the stupid resolution from the stupid screens and graphics option and enter my stupid password a second time every boot? :mad: :confused::rolleyes:](*,):evil::sad::frown: So it remembers enough of the change that the login screen is all funny, but not enough to carry over my resolution? 

An added bonus is my panel gets to get all screwed up.

Sigh - this was the first post I ran across so I had to vent. Gonna go look now and see if there is anything that solves it, and I don't doubt it will be just as complex and annoying as the whole i915 thing I never bothered with.

---

### Post by rykel on 2007-10-28
Gutsy is really getting quite bad... my resolution is NOT correctly detected by nvidia-glx-new and thus defaulted into LOW-RES mode... and even deleting my /etc/X11/xorg.conf and running sudo dpkg-reconfigure xserver-xorg did NOT do the trick.

On top of that (not related to this thread), my laptop gets locked up real bad (ie. only unplugging it from the power supply turns it off) whenever I run bittorrent. ANY bt client (Azureus, Deluge, KTorrent so far), so it is NOT a Java issue.

Lastly, GNOME and X seems to disagree on the keyboard type I have and constantly ask me to choose either one of their settings after logging in.

Sigh... I thought I would love Gutsy, but I am beginning to be disappointed with it.    :confused:

---

### Post by keyboardashtray on 2007-10-28
Well -** knock on wood** - but for me, the problem *might* have been solved quite simply. I went into Preferences>Screen Resolution which I also didn't notice or think to look for, and there, wo and behold, was a simple checkbox, a simple, GUI checkbox, to make the resolution default. And it held on a restart. Well, I'll be. I say knock on wood, because I still don't like the way it has a scrambly - look on boot. Makes me think it might up and revert just to spite me. Or how the log-in screen looks..  Don't get me wrong, I can live with a couple choppy looking screens easily, I'm just saying knowing my luck on ever getting my resolution right I'm not taking anything for granted.

Preferences>Screen Resolution> make default. Yeah, I know I probably deserve a "duh" for that, but, and maybe it's cuz I'm still in annoyed-mode, but judging from the number of Gutsy screen resolution posts, I'd still say there is at least confusion, and while I'm certain some of these peoples problem isn't just that they missed the separate Screen Resolution option in preferences, I'm sure there are a couple folks who just missed it too.. 

I mean, hey, wasn't one of the big changes in GNOME consolidating the whole appearance section (themes, wallpaper and other assorted hoo-has)? I mean why couldn't that theme of consolidation carry across to the resolution/screen and graphics? Wouldn't most people use one default resolution? I'm just saying, I think most people would think that when they select their resolution they do it from one menu, and I wouldn't think there would be a need for users to have separate resolutions. Most applications that need a separate res switch on their own. And if you want bigger print that can be handled from Appearance as well. I don't know, maybe some people like it. I guess it doesn't kill GNOME to have a redundant option for a change. :lolflag:

---

### Post by circuitsurfer on 2007-11-21
> **keyboardashtray said:**
> Well -** knock on wood** - but for me, the problem *might* have been solved quite simply. I went into Preferences>Screen Resolution which I also didn't notice or think to look for, and there, wo and behold, was a simple checkbox, a simple, GUI checkbox, to make the resolution default. And it held on a restart. Well, I'll be. I say knock on wood, because I still don't like the way it has a scrambly - look on boot. Makes me think it might up and revert just to spite me. Or how the log-in screen looks..  Don't get me wrong, I can live with a couple choppy looking screens easily, I'm just saying knowing my luck on ever getting my resolution right I'm not taking anything for granted.

Preferences>Screen Resolution> make default. Yeah, I know I probably deserve a "duh" for that, but, and maybe it's cuz I'm still in annoyed-mode, but judging from the number of Gutsy screen resolution posts, I'd still say there is at least confusion, and while I'm certain some of these peoples problem isn't just that they missed the separate Screen Resolution option in preferences, I'm sure there are a couple folks who just missed it too.. 

I mean, hey, wasn't one of the big changes in GNOME consolidating the whole appearance section (themes, wallpaper and other assorted hoo-has)? I mean why couldn't that theme of consolidation carry across to the resolution/screen and graphics? Wouldn't most people use one default resolution? I'm just saying, I think most people would think that when they select their resolution they do it from one menu, and I wouldn't think there would be a need for users to have separate resolutions. Most applications that need a separate res switch on their own. And if you want bigger print that can be handled from Appearance as well. I don't know, maybe some people like it. I guess it doesn't kill GNOME to have a redundant option for a change. :lolflag:
Thank you keyboardashtray....

Wow I have been trying to figure out why this resolution was being reset. You are the man, but you are right WHY THE HELL DID THEY NOT JUST INCLUDE THIS CHECKBOX IN Screens and Graphics.

Thank you, Thank you.

I am putting a bunck of keywords in hope that this helps others

Screen resolution keeps resetting, Screen resolution set default Ubuntu 7.10

Please read prior post.

---

### Post by keyboardashtray on 2007-11-21
> **circuitsurfer said:**
> Thank you keyboardashtray....

Wow I have been trying to figure out why this resolution was being reset. You are the man, but you are right WHY THE HELL DID THEY NOT JUST INCLUDE THIS CHECKBOX IN Screens and Graphics.

Thank you, Thank you.

I am putting a bunck of keywords in hope that this helps others

Screen resolution keeps resetting, Screen resolution set default Ubuntu 7.10

Please read prior post.

Crazy, huh? :) I'm glad you got it working too. I really think what happens is a person gets so involved with the problem, they get a sort of tunnel-vision. 

But really, you're right, why does there need to be an extra external checkbox? :confused: It seems like a loose end - there should be a tooltip or a *"to set as default, you must access..."* or like you said, just have the bloody thing there in the first place.

I had made a few posts after my ordeal, a [thread too]("http://ubuntuforums.org/showthread.php?t=595288"), so hopefully a few people have been spared the headache.

---

### Post by explainer on 2008-01-19
I am using the Preferences>Screen Resolution>Make default option, but if the monitor cannot be polled by the boot sequence, then I get 1024x768, and my 'default' 1440x900 resolution is not listed as an option.  I appreciate the dynamic discovery, but once found, I would like to be able to lock it down and KNOW it will be the same until I change it.

HERE IS A TEST I SUGGEST SOMEONE TRY:   Boot your system (or simply restart it) and turn the monitor off.  After it boots, check to see if your screen resolution is the 'default'.  It certainly isn't on my system.

I have an nVidia card with a ViewSonic 1440x900 monitor.

---


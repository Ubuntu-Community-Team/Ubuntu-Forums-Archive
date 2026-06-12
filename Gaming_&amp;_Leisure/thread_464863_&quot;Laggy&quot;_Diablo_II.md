---
title: "&quot;Laggy&quot; Diablo II"
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by Cappy on 2007-06-05
My Diablo II game becomes "laggy" as soon as I leave the town (about .3 FPS). If I hit escape the game returns to normal for as long as I am in the menus.

 I am using the newest nvidia binary drivers. 

I installed the game (no expansion), the video mode selector didn't find any video modes for me to play the game. I installed the glide driver in the game directory and it detected it. I have no option to "skip" the test and pick my which driver I want to use. 

I patched Diablo 2 to the latest version and I am using the D2Loader_v1.11b_(Dec_29_2006) with -sleepy (otherwise the lag is even worse). The game just keeps asking for the CD if I don't use D2Loader even though winecfg is set to Windows 2000)
Audio is ALSA.
No Virtual Desktop.

The game won't run fullscreen either. (I did try rebooting)
I tried Virtual Desktop 800x600 and it didn't improve anything.

When I run the game I get this:
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)

I'm using 64-bit Feisty and the 64-bit wine repos, if that matters at all.

---

### Post by Enverex on 2007-06-05
I found this bug myself before. Ubuntu is missing a needed symlink for the 32bit xrandr library. You need to link libxrandr.so.X (X being a number) to libxrandr.so in the lib32 folder.

---

### Post by Cappy on 2007-06-05
That fixed it, thank you!! I needed to copy the i386 library over to my /usr/lib32 folder and now it works perfectly!! (except not being full screen)
And to think I was 5 minutes away from reinstalling a copy of Windows XP! =P

---

### Post by disturbedite on 2007-06-05
too bad this doesn't fix the lagginess making the game unplayable for i386...

---

### Post by Enverex on 2007-06-06
> **Cappy said:**
> That fixed it, thank you!! I needed to copy the i386 library over to my /usr/lib32 folder and now it works perfectly!! (except not being full screen)
And to think I was 5 minutes away from reinstalling a copy of Windows XP! =P

You don't need to copy it over, just symlink it else you may get issues. If it's not fullscreen then either turn off Virtual Desktop in winecfg (if you're using it) or fix your xorg.conf file (which I assume is missing the required video mode so X can't switch).

> **disturbedite said:**
> too bad this doesn't fix the lagginess making the game unplayable for i386...

The game runs perfectly for anyone who hasn't got anything wrong with their setup so lets figure out what's broken on your machine.

Does "glxinfo | grep -i direct" say Yes? If so are you using DirectDraw or Direct3D for Diablo 2?

---

### Post by disturbedite on 2007-06-06
i know wth i'm doing.
i WAS NOT referring to a bad setup.  you didn't understand what i meant.  since wine v 0.9.30 (iirc) alsa support has been in the process rewriting and so d2's audio is totally screwed up since the other sound systems are basically in disrepair (or not mature enough) in regards to wine.
i'm not entirely sure this is the case for EVERYONE on i386, but for me and at least some others, alsa being broken makes d2 completely unplayable cuz it runs at 1fps or so no matter what combo of options one tries.
i know that my first comment didn't really apply to your "workaround" or fix for 64bit since i'm referring to a bug/reworking of something within wine, so sorry for the confusion.  it was just kind of an off-the-cuff remark.

---

### Post by Enverex on 2007-06-06
> **disturbedite said:**
> i know wth i'm doing.
i WAS NOT referring to a bad setup.  you didn't understand what i meant.  since wine v 0.9.30 (iirc) alsa support has been in the process rewriting and so d2's audio is totally screwed up since the other sound systems are basically in disrepair (or not mature enough) in regards to wine.
i'm not entirely sure this is the case for EVERYONE on i386, but for me and at least some others, alsa being broken makes d2 completely unplayable cuz it runs at 1fps or so no matter what combo of options one tries.
i know that my first comment didn't really apply to your "workaround" or fix for 64bit since i'm referring to a bug/reworking of something within wine, so sorry for the confusion.  it was just kind of an off-the-cuff remark.

This is really quite wrong. The only really usable sound driver in the past in Wine has been OSS and that's still true now. Wine's ALSA driver isn't being completely re-written, just upgraded in parts. Nothing has changed in ALSA that would affect Diablo II like this and no-one else is experiencing the problems, just you.

So as I said before, either you've broken Wine somewhere along the way or something is wrong with your setup.

---

### Post by disturbedite on 2007-06-07
no, i respectfully believe you're wrong on several counts.

1.  alsa is being rewritten, in part or whole, whatever, and it has been reported by other users that d2 will not work.  (read the wine appdb entries AND here on the forum, its been reported more than a little here on the ubuntu forums).  

2.  i did nothing to mess up my d2 install nor did i do an improper install.  i had the problem on feisty (testing) and feisty (final) so i decided to do a clean install of feisty and had the same exact problem.  also, i upgraded to gutsy to test and still have the same problem.

3.  based on always reading the wine newsletters & appdb all the wine sound drivers have been given no attention (both development-wise & literally) cuz alsa has been the main focus.  (hence it being rewritten now AND the fact that it is the sound system supported in the linux kernel).

---

### Post by Enverex on 2007-06-07
> **disturbedite said:**
> no, i respectfully believe you're wrong on several counts.

1.  alsa is being rewritten, in part or whole, whatever, and it has been reported by other users that d2 will not work.  (read the wine appdb entries AND here on the forum, its been reported more than a little here on the ubuntu forums).  

2.  i did nothing to mess up my d2 install nor did i do an improper install.  i had the problem on feisty (testing) and feisty (final) so i decided to do a clean install of feisty and had the same exact problem.  also, i upgraded to gutsy to test and still have the same problem.

3.  based on always reading the wine newsletters & appdb all the wine sound drivers have been given no attention (both development-wise & literally) cuz alsa has been the main focus.  (hence it being rewritten now AND the fact that it is the sound system supported in the linux kernel).


1. Diablo 2 DOES work. If it doesn't work then you're doing something wrong. End of. I wouldn't go by people reporting issues on the Ubuntu forums as proof that Diablo 2 doesn't work because with all due respect, most (not all) Ubuntu users have no idea what they are doing and normally end up breaking things (this is a FACT as I have to sift through all the invalid and bad testing data on a daily basis.

2. Is there honestly isn't anything wrong with your setup and you've found a bug with ALSA + D2 then it needs to be regression tested for it to ever get fixed. See [http://wiki.winehq.org/GitWine#head-fc6d68a85d32bb6a8f4ea0485f50dbb6409ab6f4](http://wiki.winehq.org/GitWine#head-fc6d68a85d32bb6a8f4ea0485f50dbb6409ab6f4) but this is unlikely as it works fine for me and others with ALSA or OSS.

3. Look you're just wrong. ALSA IS being worked on at the moment but it's still much worse than Wine's OSS driver. The only reason none of the sound drivers had been given any work was simply because there WAS no-one to work on them. Now there is one person that's come along and has instead decided to work on fixing the ALSA driver which is STILL not as functional and reliable as the OSS driver in Wine. All you need to do to use the OSS driver in Wine is to make sure you have the oss-compat package installed in Apt.

---

### Post by disturbedite on 2007-06-07
i don't wanna turn this into a war, but...

in regards to the oss driver working better, i tried it before with the same exact results as the alsa driver (or any other for that matter).  i would try it again, but the 0.9.38 upgrade causes d2 to freeze the entire system, so a downgrade is in order...

but in regards to oss/alsa, we were both right (& wrong) in different aspects.  (i believe were both referring to the wine soc project to improve alsa).  on a different note tho i did not remember ever reading (nor did i get the impression) that oss was the "most used" but apparently you are right about that.  but, i was right about some things too.  see this part of a wine newsletter (several issues back) for example:

(Even though the Linux kernel integrated ALSA a while back) "In Linux, the most used sound backend for Wine is OSS, this is years obsoleted  and doesn't work well with modern Linux systems. This is one of the weak sides  of Wine, and I want to propose to improve the ALSA sound backend to be as  good a backend as OSS, or if possible an even better backend."

also, you said that you don't have the problem so it most likely isn't a bug...
thats a very misleading statement.  just cuz you don't experience it *doesn't mean others don't*.  who says we have the same system?

and the problem is well known, there was even a wine newsletter that discussed the problem!  but the problem is i don't remember which one and don't feel like looking through a bunch of back issues.  (too bad they don't have a search feature).

---

### Post by Enverex on 2007-06-07
To be honest you're just spreading FUD. The game works fine. There is NO bug report, NO reports on the AppDB of it not working (infact the one report for ,38 says platinum). It works fine for me, it works fine for the devs and it works for random people I checked with in the IRC channel.

And yes, if it doesn't work properly on your machine and it does work properly on mine then it DOES mean there is something wrong with your machine or setup. The only time things may go wrong like this are because of dodgy graphics drivers, etc, which still means it's that particular persons setup, not Wine.

Stop trying to negtioate with me with comments like "you were right about this, but I was right about that...". It's getting annoying.

I never argued that OSS wasn't obsolete on Linux, what I pointed out was that the OSS driver in Wine is THE best sound driver available in Wine at the moment (although ALSA is quickly catching up).

So, end comment is this:
You seem adament it is an issue with Wine yet no-one else is able to see it. Regression test it and find which patch broke it, otherwise we're just not going to take you seriously.

---

### Post by disturbedite on 2007-06-07
well you can deny what i told you about there being a wine newsletter article mentioning it, ppl posting about it on this forum, & in the comments section of d2 entry in the wine appdb, so whatever...it doesn't matter either way.

EDIT:
in an ironic twist of events, you kind of gave me an idea to find a workaround for this problem.  i tried running d2 in an 800x600 virtual desktop and got it to run with oss audio.  i'm beginning to think that it could possibly be related to full screen vs vd & alsa...

---

### Post by Enverex on 2007-06-08
> **disturbedite said:**
> well you can deny what i told you about there being a wine newsletter article mentioning it, ppl posting about it on this forum, & in the comments section of d2 entry in the wine appdb, so whatever...it doesn't matter either way.

EDIT:
in an ironic twist of events, you kind of gave me an idea to find a workaround for this problem.  i tried running d2 in an 800x600 virtual desktop and got it to run with oss audio.  i'm beginning to think that it could possibly be related to full screen vs vd & alsa...

Can you attach the entire terminal output from Wine while running it in fullscreen mode and also point me to the forum postings, articles and comments please.

---

### Post by disturbedite on 2007-06-08
i'd gladly do that, except for one problem, as i mentioned before, with 0.9.38 in full screen d2 freezes the entire computer so i can't save the term output...

---

### Post by Enverex on 2007-06-08
> **disturbedite said:**
> i'd gladly do that, except for one problem, as i mentioned before, with 0.9.38 in full screen d2 freezes the entire computer so i can't save the term output...

wine "Diablo II.exe" &> ~/Desktop/diablo2.log

---


---
title: "Why does Compiz Fusion cause tearing on flash videos?"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by KARaidl on 2008-02-03
Whenever I enable Compiz Fusion Youtube videos begin having an issue with an unbearable amount of tearing. I can see it in other flash videos, too, but so far Youtube videos are the worst.

Is my hardware not being detected correctly?

I've got an 8800GT using the 169.09 driver installed by Envy with a Samsung 226bw (digital) monitor.

---

### Post by nilarimogard on 2008-02-03
i'm having the same problem :(

if i disable compiz, everything works just fine, but with compiz, flash is laggy and it looks like wobbly windows or something :(

---

### Post by KARaidl on 2008-02-03
You know I was thinking that it might have something to do with my monitor not being auto-detected. It's just being detected as a generic plug and play monitor, although my native resolution is automatically displayed. My 8800GT is also not auto-detected, or else I wouldn't have used Envy.

When I used the Screen and Graphics utility to try and manually set my monitor and video card, something must have gone wrong, because now my screen is completely screwed up. There are lines going across the screen that make the entire environment completely unusable, to the point where I can't see what I'm doing now.

---

### Post by KARaidl on 2008-02-05
Bumpity bump bump

---

### Post by nilarimogard on 2008-02-05
bump from me too. i'm not using compiz anymore until i get flash to work

---

### Post by LavianoTS386 on 2008-02-05
Did you set your refresh rate in CCSM?

---

### Post by nilarimogard on 2008-02-05
I tried setting it at 50, at 75 and it didn't work :(

---

### Post by Borbus on 2008-02-05
Did you enable "sync to vblank" in the compiz-fusion general options and in the nvidia driver options..?

---

### Post by nilarimogard on 2008-02-05
I just tried that and it didn't work. And i'm using ATI not nVidia video card.

---

### Post by KARaidl on 2008-02-07
Yes, I've also tried the sync to vblank in both CCSM and in Nvidia Settings, and I've also got my refresh rate set at its native 60 HZ. Even still there is a lot of tearing in flash videos, particulary big files, such as the HD flash trailers on Gametrailers - 

[http://www.gametrailers.com/player/23434.html](http://www.gametrailers.com/player/23434.html)

Can anyone honestly watch that with Compiz Fusion on and not see a hint of tearing?? I can only do it either in Windows or with Compiz turned off!

Does anyone have an answer? I'm tired of bumping this.

---

### Post by saygin on 2008-02-07
I have the same problem too. I love compiz and it is always enabled on my linux. However, after upgrading flash player to ...0.115, they can't work properly at the sam time. If compiz is enabled, flash videos are so choopy that it can't be watched normally. the frame rate is very low. If I disable compiz, vids in flasj player gets normal, high frame rate etc... Is there a solution???

---

### Post by KARaidl on 2008-02-08
Okay, it seems I have found a solution just by downgrading back to 9.0.48 r2. There's no tearing... at least for now.

---

### Post by nilarimogard on 2008-02-08
Where did you get 9.0.48 r2, because i can't find it?

---

### Post by nilarimogard on 2008-02-08
Never mind, i found it, and yeah, it works great now :D
Thanks!

---

### Post by saygin on 2008-02-10
ok, but is there a permanent solution for this??

---

### Post by KARaidl on 2008-02-10
Well since downgrading solved the problem, then that must mean that the issue lies with either Compiz or Flash. So I guess the only solution is to wait for the next release of Flash.

---

### Post by ChesterP on 2008-02-11
I only noticed this on Friday when the latest Flash Update came out.  I had no issues before that.

---

### Post by saygin on 2008-02-11
I've seached more.The issue is written into the compiz fusion forums, and it is looks like it is not solved yet.
[http://forum.compiz-fusion.org/showthread.php?t=6555&highlight=flash]("http://forum.compiz-fusion.org/showthread.php?t=6555&highlight=flash")

---

### Post by SmokinJuan on 2008-02-16
Another bump.

I'd been fiddling with Compiz settings and configuring Twinview (Nvidia 5500, LCD & TV) around the time that the flash upgrade was installed.  I wasn't sure which action may have broken the video, but it seems clearer now.  Question is, what's broken?  Flash, Compiz or something else?

It'd be interesting to know if anyone else is running dual monitors or odd video configurations: [This thread]("http://www.phoronix.com/forums/showthread.php?t=7713") indicates problems with dual twinview and vsync, but the date on the post is Jan 5th while the flash upgrade was Jan 7th (according to my Synaptic history).  Fiddling with vsync in compiz and nvidia-settings yields no results here, but I didn't restart X after making the changes so YMMV.

Searching bug tracker gives no results for this issue... may be a good idea to submit this after some more information is collected.

Also, downgrading flash doesn't work for this machine.  Youtube and the game trailer video posted earlier in this thread both gave errors telling me to upgrade to the most recent version of flash player... does that still work for you all or did I do it wrong?

---

### Post by nilarimogard on 2008-02-16
Try flash 9.0.48 r2 and see if you still have problems.

---

### Post by KARaidl on 2008-02-16
Flash 9.0.48 r2 doesn't work with Firefox 2.0.0.12, so that's probably your error. It'll only work with either 2.0.0.11 or you can use Swiftweasel, like me.

---

### Post by nilarimogard on 2008-02-16
Works with FF 2.0.12 and 3beta3, do you want a print screen with that? If I upgrade to the latest version of flash, if i watch a football match on youtube, i see it like it's a slow motion replay :(

---

### Post by SmokinJuan on 2008-02-16
Ok, I tried to downgrade flash from synaptic.  There were 2 versions, but I think they were copies of the same package (really0ubuntu12 and really0ubuntu12.1).  [_This thread_]("http://ubuntuforums.org/showthread.php?t=690038") gives the link to the [_[SIZE="4"]flash player archive[/SIZE]_]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip"), in case anyone no longer has that on their system.  After downloading that 70+Mb file (they put all their archives in one file!?) uninstall flash nonfree from synaptic and use the installer in the 9r48 folder.

I couldn't tell you about Firefox as I'm using Epiphany.

This did fix the tearing and sites no longer complain about the version.

Thanks for the fix folks! :)

---

### Post by KARaidl on 2008-02-18
> **nilarimogard said:**
> Works with FF 2.0.12 and 3beta3, do you want a print screen with that?

Nevermind, the one I got off of debian-multimedia.com didn't work with 2.0.0.12, but the one in the zip file did.

---


---
title: "Ubuntu, Dell &amp; Performance"
date: 2008-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BunnyGirlDoom on 2008-12-02
Hello everyone =)

I wasn't sure how to best search this question, so forgive me if this has been discused prior.

I have a Dell Inspiron 2650 with Ubuntu 8.10 running Dual Boot with WinXP SP2.

First off - I Love Ubuntu and am wanting to switch to linux almost exclusively (I used both WinXp and Mac regularly). I am having some issues that are of some concern and I would like to resolve before making the leap. I have solved a number of problems, but one inpartuclar I woould like to remedy is performance.

Performance in Ubuntu seems noticably poor. Especially video/effects, but there is also some concern as to why programs take longer than expected to initialize and trouble with multi-tasking.

I have tried installing a number of applications that will run poorly (or not at all) on Linux, but will run smoothly on WinXp on the same laptop. For isntance, the MMO *Regnum*. I installed the linux executable of Regnum and the game will start - but only when all gaming options are at minimum levels (low terrain detail, low effects, graphics, etc). It is very jumpy and is basically non-playable, though *techncially* it runs.

I then decided to run it on the same system, but under XP. Now, even in XP I still have to turn a lot of the options to their minimum levels, but it runs exceptionally smoother than the Ubuntu install - it is actually very playable. So, I know the hardware *is* capable of playing the game - so why is it having so much trouble in Ubuntu?

I am running the correct Driver for my Geforce2 GO card and have nothing else running in the background (with the exception of having Desktop Effects turned on). I even disabled the AWN dock I had running to make it as CPU free as possible to run the game. No luck. This typically isn't a huge issue on the laptop since I would normally play games on my other PCs. But I did want to try it to see how it performed. One of the reason I had a prior concern was because Ubuntu doesn't like to multi-task well on my laptop. If I run more than 2 apps at the same time, it gets very slow. And playing Rhythmbox and Movie PLayer at the same time? Well, *forget it*. I am really not one to say "WinXP blah, blah, blah" but it seems a resaonable concern since they both are installed on the same laptop. In XP I can run the latest version if iTunes and WMP without so much as a stutter and even browse online thru FF or Opera. To be fair, I can do this in Ubuntu, too - it just isn't very friendly and audio and video tend to stutter when both movie player and Rhythmbox run simultaneously.

So my question isn't really about gettig the game to work. Its about optimizing performance within Ubuntu. Is there a way to squeeze better performance out of Ubuntu sicne I know that the hardware is capable of doing what I want it to?

Or is it more that the drivers for my hardware are not as good as they can be because of poor support/drivers from the developers when it comes to Linux distros?

I would tend to go with the latter, but I wanted to run this by you - partiularly Dell owners - since Dell is the system in question (I have yet to install Linux on any of my other systems until I know Ubuntu can function as desired).

Some info:

[I]Dell Inspiron 2650
GeForce2 GO card
512MB RAM
1.5 Ghz CPU (*cough*Celeron*cough*)
20GB HD
Ubuntu 8.10[/I]

PS I have been addicted to Ubuntu since I installed it weeks ago. I'm really looking forward to moving on in the direction of Ubuntu and less in the direction of mainstream alternatives.

---

### Post by sirjoebob on 2008-12-02
Good post- lots of detail..

This is a laptop, right? If so, Dell laptops have fan issues in Ubuntu- see my signature for Dell laptops and i8k fans.If your fan is not running, your system is probably over heating and this would cause issues regardless of what programs you are running. 

Also, your specs are a little low to expect a speedy Ubuntu installation. I would recommend Xubuntu. It uses the XFCE window manager and is a lot lighter on system resources than gnome (which is what is used by standard Ubuntu). Hope that helps.

---

### Post by BunnyGirlDoom on 2008-12-02
Thanks for your post Sir JoeBob!

I will look into the fan situation. It isnt necessary for me to get performance to achieve excellence on this particular installation. I am using it as (basically) a test model before putting it on my more current systems. I'm really only concerned with whether people find that Ubuntu performance is usually realtively comparable to OS's like OSX and WinXP - because this laptop, as you have noticed, is not exactly optimal by hardware standards and I recognize functionality could very well be due to out of date hardware - but specifically linux drivers versus XP drivers for said hardware.

Thanks again!

---

### Post by sirjoebob on 2008-12-02
?

---

### Post by sirjoebob on 2008-12-02
Understood about the HW but Xubuntu runs a lot leaner.

As far as Ubuntu performance, I use it all day every day on my Dell Vostro 1500. I have an Intel core II Duo at 2.0 Ghz and 2GB of RAM. It is a powerful machine to be sure but the level of performance U get in Ubuntu is about twice as good as I had in XP. 

I usually run anywhere between 6 and 14 programs simultaneously with Compiz Fusion loaded down with effects and have ample resources left over- and think I almost bought the 4GB of ram... lol. Seriously, I game, surf, watch, listen, monitor, chat, IRC, Skype, often at the same time and have NO issues with performance. I have never had more fun running an OS!

Also, my email is [email]sirjoebob@gmail.com[/email] if you ever have any quick questions, feel free to shoot me an email. Hope I have been helpful.

---

### Post by BunnyGirlDoom on 2008-12-02
Thats fabulous!

 Pretty much what I was hoping to hear! Next step is to install it on my main system. As of right now I'm installing it on my HP Pavilion Laptop to compare.

You have been helpful and thanks for the heads up on the fan problem in Dells =)

---

### Post by sirjoebob on 2008-12-02
no problem. The forums have always been a good source of help to me and I like to pass it along when I can.

---

### Post by shae on 2008-12-03
Your main performance issues stem from compiz in that laptop.  The video card does not have the power to run compiz + a game at the same time at an acceptable rate.  In face running any game with compiz running will take a performance hit.  Remember XP does not use 3d acceleration in its desktop so it is not competing with the game for video card use.  Disable compiz completely (Visual Effects: None) and try again.  

Secondly, the problems with sound stuttering likely is not a performance issue.  I would suspect pulse audio to be the root of the problems.  Try setting your computer to use alsa.

---

### Post by BunnyGirlDoom on 2008-12-03
Great input. Thanks much!

---

### Post by druellan on 2008-12-03
I'm also gathering information about performance enhancements for run Ubuntu on reduced hardware (like an eeePC computer). Currently my concern is about ext3 filesystem: I understand that the journal system is not a critical feature to have on a self-powered laptop and can be switched off. Also, a partition can be converted to ext2 which seems to be faster, but I cant get onto a good benchmark to confirm that.

---

### Post by BunnyGirlDoom on 2008-12-03
> **shae said:**
> Your main performance issues stem from compiz in that laptop.  The video card does not have the power to run compiz + a game at the same time at an acceptable rate.  In face running any game with compiz running will take a performance hit.

Disabling compiz did the trick! I thank you. Later I'll try Alsa as opposed to Pulse and see how I fare with running aud and vid from separate apps.

Cheers

EDIT: My main reason for running Desktop Effects was to have AWN Dock working... but it's purely an unimportant, aesthetic situation, and besides - I already have a mac, so no reason to make Ubuntu look like one. =)

---

### Post by BunnyGirlDoom on 2008-12-04
> **shae said:**
> Secondly, the problems with sound stuttering likely is not a performance issue.  I would suspect pulse audio to be the root of the problems.  Try setting your computer to use alsa.


I tried a number of things. The idea of removing Pulse was kinda scrapped when I couldn't find a decent suggestion on how to do it - especially without removing ubuntu-desktop, so I opened the Audio preferences and changed everything from Pulse to ALSA. Rebooted. Could not get audio out of Rhythmbox but could with games and such. I finally ended up selecting OSS for all of the play back and recording, rebooted and the game I was having issues with no longer suffered from stuttering and poor performance (performance was improved but not totally corrected when I deactivate compiz). Rhythmbox is working again as well, so I think I may finally have this all sorted. *knock on wood*

So far so good! Thanks again for you suggestions!

:KS

---

### Post by falcon61102 on 2008-12-04
Many people have reported seeing increased performance in Ubuntu over Windows installations on the same computer.  Many times it relies on the individuals' hardware and whether Ubuntu can take full advantage of some aspects of it but overall, they should be very compareable.  One area that Ubuntu does out perform Windows in is in long term use.  As any long time Windows user will say, Windows becomes cluttered and requires regular disk cleanups and defrags even with just general use.  Ubuntu does not require most of this type of maintenance and performance normally will not decrease as time goes on because of the system becoming bogged down.

---

### Post by druellan on 2008-12-04
> **BunnyGirlDoom said:**
> I finally ended up selecting OSS for all of the play back and recording, rebooted and the game I was having issues with no longer suffered from stuttering and poor performance (performance was improved but not totally corrected when I deactivate compiz). Rhythmbox is working again as well, so I think I may finally have this all sorted. *knock on wood*
I also noticed this. Seems that on 8.10 there is some sort of bug on Alsa drivers or gStreamer that eats ups CPU power. Since pulseaudio currently uses mainly Alsa compatibility, you end having poor performance on both. A gStreamer fix is on the way, so hopefully this problem can be addressed.

About uninstalling pulseaudio, since I want to keep my installation as much "factory default" as possible, I currently use a small script that kills pulseaduio server on start, among other things :)

```
#!/bin/bash
pkill pulseaudio
```

I set it to run on bootup on preferences -> session. There you can find a pulseaudio mixer that can be disabled.

---

### Post by elcman on 2008-12-04
I was going to recommend disabling Compiz as well, but I didn't get to it.

The thing is, I'm looking for a way to disable it myself. I have a Dell C400 (Pentium 3, 768MB Memory), which seems a tad ridiculous to try running Ubuntu on, but it is the only machine I really can mangle and get away with it.

In any case, moving to Jaunty I had trouble. I had the SAME trouble when moving from 8.06 to 8.10. The video kept saying it was operating in low graphics mode so I continued booting with low graphics mode with the intention of turning off Compiz when I got in under Pref > Appearance.

It is grayed out when I'm booting into low graphics mode.

Is there a way I can do this from the command line without having to fuss with hamfisting the compiz loader? I tried **sudo apt-get remove compiz** but I don't think that was what I needed.

Heh, just talking through this I found that my problem is with my driver, not with Compiz. I guess I'll be barking up another tree.

---

### Post by BunnyGirlDoom on 2008-12-04
> **elcman said:**
> Heh, just talking through this I found that my problem is with my driver, not with Compiz. I guess I'll be barking up another tree.

What card is in your dell for graphics?

---

### Post by BunnyGirlDoom on 2008-12-04
> **shae said:**
> Secondly, the problems with sound stuttering likely is not a performance issue.  I would suspect pulse audio to be the root of the problems.  Try setting your computer to use alsa.

Ok, an update is in order:

While the OSS thing appeared to work, I didn't think about how it would affect two apps running audio simultaneously - such as listening to msuic on Rhythmbox and watching a web video with audio. That wouldn't work. Once one app grabbed the audio, the other apps/broswer could not use it - but to be honest, I should have expected this - just hadn't thought about it at the time.

So, what I have done is this: I created another user. I didn't realize that creating another user in Ubuntu would allow me to have a completely different setup (for the most part). On one user I have Pulse initialized as it was with the initial OS install and have enabled medium desktop effects. On the other user I have OSS for all the sound output and have desktoop effects disabled.

The werid thing is that soemtimes running a game under the 2nd user with OSS, the audio will stutter and jitter along with graphics. Sometimes I reboot and it clears up and plays fine. Sometimes it doesn't. I'm a little confused as to why it is inconsistent.

As far as Pulse... what a headache that lil' bugger is. Sometimes even opening a browser will cause audio from Rhythmbox to cut out a sec or have a short stuttery burp. Is there a way to optimize Pulse? Or is there a relatively straight-forward guide to replacing Pulse with something similar (that any of you know of)? I went on a Pulse search last nigth for an hour and read through threads and threads on various forums that resulted in no real solution.

I know my hardware is capable of performing better, I ust am not sure why it's having so many problems under Ubuntu. 

I refuse to give up, though! I shall perservere!

---

### Post by figi22 on 2008-12-04
Do **all** Dell laptops have problems with the fan with Ubuntu?   I just bought a brand new Dell Studio for my mother, and it's not something that she's likely to notice!  Have to say I haven't heard the fan while I've been sorting it out...

---

### Post by Jammanuser on 2008-12-04
> **figi22 said:**
> Do **all** Dell laptops have problems with the fan with Ubuntu?   I just bought a brand new Dell Studio for my mother, and it's not something that she's likely to notice!  Have to say I haven't heard the fan while I've been sorting it out...

No...ALL Dell laptops do not have this problem with the fan on Ubuntu! ;) I have the Dell Studio 1535 laptop, dual boot with Ubuntu and Vista...and have to say that so far, there has not been a problem with my fan on Ubuntu! :)

Cheers! ;)

-jammanuser

:D

---

### Post by druellan on 2008-12-05
> **BunnyGirlDoom said:**
> Is there a way to optimize Pulse?
Check this: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

> **BunnyGirlDoom said:**
> Or is there a relatively straight-forward guide to replacing Pulse with something similar (that any of you know of)?

You can remove completely pulseaudio and install esound. Don't worry about the ubuntu-desktop being uninstalled, since is not the whole desktop, just the metapackage. 
Another thing you can try is to update Alsa drivers, to see if they  improve somehow the performance.
[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

Also, seems that gstreamer has a bug the has been addressed on latest versions.
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/73744](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/73744)

---

### Post by figi22 on 2008-12-05
> **Jammanuser said:**
> No...ALL Dell laptops do not have this problem with the fan on Ubuntu! ;) I have the Dell Studio 1535 laptop, dual boot with Ubuntu and Vista...and have to say that so far, there has not been a problem with my fan on Ubuntu! :)

Cheers! ;)

Thanks!  That's good news :D

---

### Post by BunnyGirlDoom on 2008-12-05
Thanks. Druellen =)

---

### Post by iggykoopa on 2008-12-05
If your having troubles with the fans you can look into i8kutils or dellfand. I know on the 1420's that the fan just goes medium speed all the time unless you use one of those. I like dellfand better because you can use it on a 64 bit system too.

---

### Post by BunnyGirlDoom on 2008-12-05
I tried i8kutils on my Dell (I wasn't really having a fan issue but tried it to see if I would notice any difference) and it hung up my system. CPU reported at 90% usage - all from the program. So, anyone with an older Dell, be mindful of that if you choose to try i8kutils out.

---

### Post by Jeroen de Lange on 2009-01-20
[http://ubuntuforums.org/showthread.php?p=6586386&highlight=Dell+C400#post6586386](http://ubuntuforums.org/showthread.php?p=6586386&highlight=Dell+C400#post6586386)

---

### Post by sirebral on 2009-01-20
You might also want to reduce desktop effects to Nothing. 

I am going to say that it is Driver support.  Maybe I am wrong, but I think that would be the ultimate problem.  Ubuntu has it's set of ALSA drivers that can get a lot of hardware to work, but my guess is they don't have the capital to create drivers for hardware that are 100%.  Like I said, maybe I am wrong.  (I just think that MP3 codecs need to be installed seperately still.)

Of course, Vista just sucks, IMO.  Aero, in Vista, for some reason is a HUGE resource hog and after shutting it off I never really understood why.  Why, Jesus, why?

---


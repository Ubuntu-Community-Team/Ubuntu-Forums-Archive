---
title: "Problem: Sound - Only one speaker works"
date: 2005-12-27
forum: General Help
---

### Post by Flukey on 2005-12-27
Hey guys,

Im running KUBUNTU however i get the same problem on UBUNTU, but seeing as the UBUNTU forum gets more views i would post it in here (i hope thats ok mods :) ) 

I have a logitech speakers, ONe subwoofer and two speakers. 

One speaker and the sub works, but the other speaker doesn''t

Any ideas as to why? and what i can do? 

Cheers

:)

---

### Post by BathroomNinja on 2005-12-27
OK, I'll take the lead and ask:  Do both of the speakers work if you plug them into a CD player/MP3 player?  Do both speakers on a set of headphones work if you plug them into the computer instead of the speakers?

Just asking to make sure this isn't a hardware problem.  You'd be suprised.

---

### Post by Flukey on 2005-12-27
[QUOTE=BathroomNinja]OK, I'll take the lead and ask:  Do both of the speakers work if you plug them into a CD player/MP3 player?  Do both speakers on a set of headphones work if you plug them into the computer instead of the speakers?

Just asking to make sure this isn't a hardware problem.  You'd be suprised.[/QUOTE]

Hi,

Yeah they do work. My computer is partitioned for windows xp and ubuntu.

Speakers work absolutely fine in windows xp pro. 
How does one go about changing my sound driver, i think this may be the problem.

Cheers :)

---

### Post by BathroomNinja on 2005-12-28
Try this:

Boot up your computer to the Ubuntu Live CD.  See if both speakers work with the plain Ubuntu kernel.  This will help us see if it's just not seeing your hardware properly, or if there may be another issue.


If the live CD works, then it's game on.  We just need to check your settings.  If it doesn't, then it's possible we may need to find a driver for your sound card.  Also, do you know what make/model your sound card is?

---

### Post by LiquidIQ on 2005-12-28
Also make sure in the mixer with Ubuntu that the balance is correct.

---

### Post by BathroomNinja on 2005-12-28
OK, home finnaly.  Right click on your speaker icon at the top right, next to the date/time.  click on Preferences.  It will show you the name of your soundcard.  Write that down.  click Close.  Now Right click on the speaker icon again, this time click on Volume Control.  Make sure where it says 'Master' that both right and left bars are about even.

---

### Post by Flukey on 2005-12-29
Right ok guys. The sound slider is even. But still only one speaker.

On board Realtek AC97 Audio card. Not exactly sure what model number.

*go tests live cd*

will get back to you. 

Thanks guys

---

### Post by zuehls on 2007-10-21
I slid the volume control and now I have both speakers working.  They were already evenly set but I get it just needed to be moved.

---

### Post by MidBSD on 2007-11-04
> **zuehls said:**
> I slid the volume control and now I have both speakers working.  They were already evenly set but I get it just needed to be moved.

I suffer from the one speaker problem too. Until recently, I was able to solve it by unlinking the left and right channels, sliding the non-working channel (always the left speaker but that may be different depending on your model of PC/laptop and dependent on wiring too) down to zero and then back up again.

Unfortunately, this solution has stopped working and now I only have sound out of one speaker only. It also affects headphones (as it did before).

My speakers and headphones work fine as I've tested them in Windows too.

Has anyone else found any other solutions to this problem?

---

### Post by aquamammal on 2007-11-15
Yo dude, I don't know if this will help, but I was having that exact same problem, and I went and double right clicked my volume button, and muted my volume then unmuted, and the sound went to both speakers.


I don't think you haven't tried that, but it's worth 10 seconds.

---

### Post by andreasmascher on 2008-01-08
hello people, 

its an old post, I know, but I have the exact same problem!! It drives me crazy! None of the above solutions have worked for me. My left speaker stops randomly... Any Idea? I am really freakn out here, like to watch my dvd... beggin for creativity!

THX

---

### Post by MikeJJ on 2008-01-10
From googling (i also experience the sound occasionally only coming out of the Left speaker, while other times both work, and it not the speakers, because i change the stereo the pc is plugged into to radio / cd and it works perfect) this bug was first mentioned in 2003.  Someone suggested in 2006 to install QAMix and just load it up as it fixed it for them.  It just fixed it for me as well.
So this is a linux / ubuntu bug, which is over 5 years old.  Installing and running QAMix my resolve the issue, but doesn't fix the source of the problem. :)

---

### Post by andreasmascher on 2008-01-10
\\:D/  worked for me as well. thanks dude!  :-\"

---

### Post by SwimDude0614 on 2008-04-05
well.... unfortunately installing QAMix and playing with as many controls as i could did not take care of the problem for me, and i've had various sound problems ever since first running ubuntu (with 7.04, then 7.10, now 8.04).

one thing to note, my sound *breifly* worked. about two days ago i think it was, i installed a bunch of updates (as there are every day with beta OSs) and when i rebooted, THE SOUND WORKED PERFECTLY! it was miraculous. i turned the computer off that same day, and today is the first day i've been back. soon as i booted up, it was back to it's old self. darn thing.

any more ideas? i've tried everything so far listed.

---

### Post by SwimDude0614 on 2008-04-05
sorry. this is just to make sure i'm subscribed. I just set up this account for the last post.

is there a way to subscribe to a thread without posting?

---

### Post by robholmes on 2008-04-11
Hi, I've had exactly the same problem everyone else is having. Most of the time the sound comes from both speakers of my laptop, but sometimes when i boot i only get sound from the right speaker.

I used to just reboot and the problem would go away, but today I just discovered another way to fix my problem:

Just plug my headphones in the jack, then take them back out again. Voila... Stereo sound again!

This baffles me slightly, but I hope this helps someone else with the same problem, until a fix is released.

Cheers,

Rob

---

### Post by another_sam on 2008-04-20
Same problem. Same solution. But I will give one detail:

Installing qamix was not enough. I had to start qamix (Applications > Sound & Video > QAMix), and saw astounded that right speaker was muted. Then I simply unmute the right speaker (right from the user pov) and it worked.

My audio card:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by merlos on 2008-06-11
Same problem for me on a DELL Latitude D620

```
merlos@merlos-lap:~$ lspci  | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

Solved doing mute/unmute on tray sound icon

Tks
:guitar:

---


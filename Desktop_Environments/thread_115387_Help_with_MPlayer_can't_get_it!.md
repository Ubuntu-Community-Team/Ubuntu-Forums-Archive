---
title: "Help with MPlayer: can't get it!"
date: 2006-01-10
forum: Desktop Environments
---

### Post by Steve S. on 2006-01-10
I'm new to ubuntu, but a little linux experience (gentoo).

I tried to add mplayer via the graphic Synaptic thing, including the Firefox plug-in, but it gave an error message and said something to the effect of, it could see that mplayer was used/noted by something else but that it couldn't find it, perhaps the source had changed....  Something like that (trying to remember, I'm at another computer right now).

Anyway, tried to add other players, but totem doesn't get it done, and the others aren't picking up nearly the same stuff mplayer could within my gentoo box.  And, I can't watch anything on firefox right now, and I need to fix that.

Gotta have mplayer!  Anyone have any ideas?  If there is a graphical way to do it, great, but I could do command line if it is explained out to me as to a newbie.

Thanks in advance.

---

### Post by hillbilly on 2006-01-10
When you try to add mplayer via synaptic, theres a description about the app that you are downloading. Does it mention anything relevant ? Check that out ? Maybe you were trying to install an obsolete version of mplayer or something.

---

### Post by Steve S. on 2006-01-10
[QUOTE=hillbilly]When you try to add mplayer via synaptic, theres a description about the app that you are downloading. Does it mention anything relevant ? Check that out ? Maybe you were trying to install an obsolete version of mplayer or something.[/QUOTE]

Thanks, hillbilly.  I'll check to see exactly what it says and quote it for everyone.  It says some relevant stuff and it seems that it is an outdated version of mplayer, but should synaptic be current if I just installed my ubuntu system and updated it (which I did)?

That being said, I tried via command line using sudo apt-get install mplayer but it gave me a similar message.  Do I need to do it from the source?  I tried to do it from the mplayer site, but it is not a tar file and to be honest with you, that is the only type of file that I have documentation on how to set it up on command line.  Any tips?

I'm not averse to command line, I just have to have the steps listed out since I'm still not that adept at it.  Gentoo cured me of some of that;) , but still learning.

---

### Post by jrib on 2006-01-10
take a look at: [https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)

---

### Post by bikeman on 2006-01-10
Cough ... [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix")

Just make sure that you have your sudo permission set up (I used the expert installation option, which did not put my user account in the sudo group).  Worked amazingly well.  Be sure to read the entire thread, and the warnings about restricted formats.

Daniel

---

### Post by Steve S. on 2006-01-10
[QUOTE=bikeman]Cough ... [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix")

Just make sure that you have your sudo permission set up (I used the expert installation option, which did not put my user account in the sudo group).  Worked amazingly well.  Be sure to read the entire thread, and the warnings about restricted formats.

Daniel[/QUOTE]

I'll check it all out and keep everyone posted.  thanks.  Appreciate the prompt response without the tedious yelling-at-the-newbie. ;)

---

### Post by mlalkaka on 2006-01-10
I have a question somewhat related to this thread.
 :?: Why does mplayer and mencoder depend on xmms? 
I want mplayer-586 and mencoder-586, but they both depend on xmms (which I do not want). As far as I can tell, neither mplayer nor mencoder requires xmms, yet they are dependent upon it in the Ubuntu repositories.

Thanks

---

### Post by Steve S. on 2006-01-10
[QUOTE=mlalkaka]I have a question somewhat related to this thread.
 :?: Why does mplayer and mencoder depend on xmms? 
I want mplayer-586 and mencoder-586, but they both depend on xmms (which I do not want). As far as I can tell, neither mplayer nor mencoder requires xmms, yet they are dependent upon it in the Ubuntu repositories.

Thanks[/QUOTE]

Speaking as a newbie, so keep that in mind.  But why don't you want XMMS?  I've always had good luck with it.  Use something better or is it just incompatible with something?  Just curious.

---

### Post by TiZeta on 2006-01-10
hi Steve

try this, by console

[COLOR="Blue"][FONT="Lucida Console"] sudo apt-get install mplayer-386 mozilla-mplayer[/FONT][/COLOR]

but before doing this, make shure you have everything in /etc/apt/souces.list.

This is my file, it is meant for breezy.

[COLOR="Blue"][FONT="Lucida Console"]
## Uncomment the following two lines to fetch updated software from the network
###italian mirror#####
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main universe multiverse restricted
[/FONT][/COLOR]

Hope this helps! Let me know.

---

### Post by Steve S. on 2006-01-10
Thanks, TiZiana, I tried all that, in the correct order.  Uncomenting that stuff allowed me to get other things, just not mplayer.

I'm going to try out some of the other stuff, including Automatix.  I'll keep everyone posted.

---

### Post by mlalkaka on 2006-01-10
[QUOTE=Steve S.]Speaking as a newbie, so keep that in mind.  But why don't you want XMMS?  I've always had good luck with it.  Use something better or is it just incompatible with something?  Just curious.[/QUOTE]

I prefer Rhythmbox Music Player and BMP (beep-media-player) over XMMS. You're right that XMMS is good. But I find BMP to be better. Indeed, BMP is a fork project of XMMS. It is basically XMMS with GTK 2.x instead of GTK 1.x, and a few other improvements.

---

### Post by Steve S. on 2006-01-11
[QUOTE=mlalkaka]I prefer Rhythmbox Music Player and BMP (beep-media-player) over XMMS. You're right that XMMS is good. But I find BMP to be better. Indeed, BMP is a fork project of XMMS. It is basically XMMS with GTK 2.x instead of GTK 1.x, and a few other improvements.[/QUOTE]

Good to know...I'll check it out.

> Cough ... Automatix

Just make sure that you have your sudo permission set up (I used the expert installation option, which did not put my user account in the sudo group). Worked amazingly well. Be sure to read the entire thread, and the warnings about restricted formats.

I put it in last night, but didn't have time to see if it worked for my mplayer issues.  It looked pretty impressive, so we'll see later today.

---

### Post by Steve S. on 2006-01-11
Looks great!  Automatix found it and set it up! Rockin'!

---

### Post by jerrykenny on 2006-01-11
Steve, it sounds like synaptic is worried your going to be downgrading some of your libraries, or dependencies, in synaptic, try Edit > fix broken packages . . . . but its hard to say without the right message.

tip. . . . next time something daft like this happens,  take a screenshot for future reference.

By the way, my system runs the mplayer 386 version better than the 586, or custom versions . . . . dont know why, and dont know prevalent this is either . .. but the 386 is fine.

---

### Post by Steve S. on 2006-01-12
[QUOTE=jerrykenny]Steve, it sounds like synaptic is worried your going to be downgrading some of your libraries, or dependencies, in synaptic, try Edit > fix broken packages . . . . but its hard to say without the right message.

tip. . . . next time something daft like this happens,  take a screenshot for future reference.

By the way, my system runs the mplayer 386 version better than the 586, or custom versions . . . . dont know why, and dont know prevalent this is either . .. but the 386 is fine.[/QUOTE]

It runs real well right now, including the plug-ins for Mozilla.  It kicks back a couple of errors on certain videos, but I'll have to check to see what the exact error message is and post it (at a different computer right now).

---

### Post by Steve S. on 2006-02-06
All right, I have a slightly different mplayer question:

When I click on a video, it defaults to totem.  Is there a way to make it default to mplayer?

I know that I can right click it and and get mplayer to play it, but I can't find anywhere to set the defaults on the players.

Advice?

---


---
title: "Unity + Dual Monitors just a bad user exp?"
date: 2011-10-25
forum: Desktop Environments
---

### Post by blitzd on 2011-10-25
Ok, so I have a laptop with an external monitor, and a freshly installed 11.10 64-bit (desktop). I have my monitor to the right of the laptop, and I'd like to use it as the main screen when it's connected. 

I've managed to get past several nvidia/11.10 dual monitor issues and have both displays working with twinview, but my issue now is how do I get the unity bar to show up on my external screen?

I tried configuring the two displays to use separate x screens thinking maybe that would do it, but that was a whole new can of worms, and just resulted in a white old school x screen on my external monitor... or a frozen desktop with xinerama enabled.

I thought I'd give Unity a try again when I did a fresh install after 11.10 came out, and I've grown rather attached to using it to switch windows and workspaces now. But if I have to deal with my menu and all my apps opening on a monitor that is not my MAIN monitor, well - that's just not going to work out.

---

### Post by robert shearer on 2011-10-25
There is a discussion here about moving the Unity launcher that covers the dual/multi-monitor issue.
[https://bugs.launchpad.net/unity/+bug/668415](https://bugs.launchpad.net/unity/+bug/668415)
(about half way in from memory...posts by Tal Liron ?)

As Emblem Parade he/she posts some workarounds here...
[http://ubuntuforums.org/showthread.php?p=11368937](http://ubuntuforums.org/showthread.php?p=11368937)

It appears Canonical will not be allowing launcher movement anytime soon...
from the bug report quoted above...
> 
Mark Shuttleworth (sabdfl) wrote on 2010-10-30: Re: [Bug 668415] Re: Movement of Unity launcher 	#2

I think the report actually meant that the launcher should be movable to
other edges of the screen. I'm afraid that won't work with our broader
design goals, so we won't implement that. We want the launcher always
close to the Ubuntu button.

 status wontfix

Mark
Mark Shuttleworth (sabdfl) on 2010-10-30
Changed in unity:
status: 	Invalid &#8594; Won't Fix 

---

### Post by blitzd on 2011-10-26
Thanks Robert,

I'll check that out tomorrow. I was hoping to not have to 'hack' anything as that's what led me to having to do a fresh install of 11.10 in the first place.

Based on the responses from Mr. Shuttleworth and Devs it doesn't sound like Unity is going to support multiple monitors (or movement of the Unity  bar) any time soon - if ever, so I think I'll just ditch it. It's a shame because I had a nice workflow going with it at work where I have a single 24" monitor, but I don't think I want to use two different desktop managers between work->home. So much for a nice out of the box experience.

The new GNOME desktop seems to support multiple monitors - so maybe I'll give that a shot too, it looks a bit sketchy though.

---

### Post by robert shearer on 2011-10-26
> I was hoping to not have to 'hack' anything as that's what led me to having to do a fresh install of 11.10 in the first place.


Hack away, as now is the best opportunity ever !

Fresh installs mean nothing left to lose (could be a song there...?) no data, no configs, no custom apps, and only a click away from pristine again !!

Hack like there's no tomorrow, risk everything, and when it works...!!!  celebrate...:D

Cheers, Bob.

---

### Post by Pziko on 2011-10-26
WAIT wait wait wait wait. Just... Wait. Now, I'm coming back to Linux, specifically Ubuntu, after a few years of working on Macs and Windows due to my job. Part of why I've preferred Linux workstations is quite simple: I can make it MINE. With Apple, with Microsoft, this business of &quot;our broader design goals&quot; was what, in effect, drove me away. Essentially &quot;This is how we want you to interact, take it or leave it&quot;.   Is that, in effect, what's going on with this new &quot;unity&quot; desktop? I came here specifically to find out how to move that bar and customize the shell.  

 EDIT: Not that I'm not going back to Ubuntu :) But I'll be using KDE or Gnome 3 instead of Unity.  > **robert shearer said:**
> There is a discussion here about moving the Unity launcher that covers the dual/multi-monitor issue.
[https://bugs.launchpad.net/unity/+bug/668415](https://bugs.launchpad.net/unity/+bug/668415)
(about half way in from memory...posts by Tal Liron ?)

As Emblem Parade he/she posts some workarounds here...
[http://ubuntuforums.org/showthread.php?p=11368937](http://ubuntuforums.org/showthread.php?p=11368937)

It appears Canonical will not be allowing launcher movement anytime soon...
from the bug report quoted above...

---

### Post by blitzd on 2011-10-26
> **Pziko said:**
> WAIT wait wait wait wait. Just... Wait. Now, I'm coming back to Linux, specifically Ubuntu, after a few years of working on Macs and Windows due to my job. Part of why I've preferred Linux workstations is quite simple: I can make it MINE. With Apple, with Microsoft, this business of &quot;our broader design goals&quot; was what, in effect, drove me away. Essentially &quot;This is how we want you to interact, take it or leave it&quot;.   Is that, in effect, what's going on with this new &quot;unity&quot; desktop? I came here specifically to find out how to move that bar and customize the shell.  

 EDIT: Not that I'm not going back to Ubuntu :) But I'll be using KDE or Gnome 3 instead of Unity.

Indeed. Though it seems that with Ubuntu you're now going to find yourself with shrinking options in addition to the inevitable 'upside' of open source software (which is clearly on display in that Launchpad bug, from this comment):

> Louis, it's open source! If you want to change it please do. Or use
Docky. Or AWN. Or any number of alternatives. But please recognise that
we've got the right to build Unity the way we think it's going to be
best for folks, and that explicitly precludes trying to fit everything
that everyone wants into it.

Mark

While he's right in a sense, that kind of response just rubs me the wrong way. There seems to be a continuous uproar regarding many of the decisions made in Unity - and it would appear to me that this uproar is at least partially coming from the same people that Mark refers to as the 'folks' that they're apparently trying to build the 'best' Unity for.

Also telling, although this bug was set to 'wontfix' by Mr. Shuttleworth himself a mere two comments in, essentially putting an end to all prospects of the Ubuntu team even discussing the problem, almost a full year later we see this from a member of the Canonical Desktop Experience team:

> Right now the launcher is tied to the left-bottom most monitor.

This was a design decision which had no real good answer. This is
something that we are looking at now with design for better
multi-monitor support.

Right now, if you have a monitor set to the left of your primary
display and you want the launcher on your primary, the only real
solution is to move the other monitor to the right. Sorry about that,
but we are working on it.

So, in the end the 'best' Linux distribution, essentially doesn't support multiple monitor setups with the 'best' desktop manager a full year after it was a known issue - a shame, but I guess this is the downside of that 'upside'. Also seems rather ironic, but I think Unity is one of the more divisive issues I've seen with Ubuntu to date.

---

### Post by Pziko on 2011-10-26
> **blitzd said:**
> So, in the end the 'best' Linux distribution, essentially doesn't support multiple monitor setups with the 'best' desktop manager a full year after it was a known issue - a shame, but I guess this is the downside of that 'upside'. Also seems rather ironic, but I think Unity is one of the more divisive issues I've seen with Ubuntu to date.



 I find that mind boggling. After some google-fu I've found more info about this fellow. He seems fairly intelligent, one does wonder if he realizes that a mutiny among linix/unix users is a dreadful sight to behold. 

 Admittedly it's "cute", and I am certainly going to give it a shot and the benefit of the doubt. So far though I'm not in love. But I'll keep giving it a go and tinkering. So far it does run beautifully on my Dell Precision E6500, I've had no crashes or anything like that. Duel monitor support is going to be fairly important for me, as will switching back and forth between connected external monitor and the laptop's screen. Thanks for the reply.

---

### Post by blitzd on 2011-10-27
> **Pziko said:**
> I find that mind boggling. After some google-fu I've found more info about this fellow. He seems fairly intelligent, one does wonder if he realizes that a mutiny among linix/unix users is a dreadful sight to behold. 

 Admittedly it's "cute", and I am certainly going to give it a shot and the benefit of the doubt. So far though I'm not in love. But I'll keep giving it a go and tinkering. So far it does run beautifully on my Dell Precision E6500, I've had no crashes or anything like that. Duel monitor support is going to be fairly important for me, as will switching back and forth between connected external monitor and the laptop's screen. Thanks for the reply.

I've since switched to GNOME3... It looked sketchy at first, but I have to say it's really quite slick. It seems geared towards exactly what I was looking for, which is a secondary monitor that usually has reference material or a web page, and the main monitor flipping between workspaces. Now if I can figure out a way to get Xinerama to work and flip the reference screen into portrait that would be killer!

---

### Post by robert shearer on 2011-10-27
Whoop !  Unofficial workaround to allow Unity launcher to be **moved to the bottom**.....

[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

Just a day old and look how many comments it has garnered.

On a related matter...
New bug report some may wish to follow/participate in....
[https://bugs.launchpad.net/unity/+bug/882274](https://bugs.launchpad.net/unity/+bug/882274)

---

### Post by blitzd on 2011-10-30
> **robert shearer said:**
> Whoop !  Unofficial workaround to allow Unity launcher to be **moved to the bottom**.....

[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

Just a day old and look how many comments it has garnered.

On a related matter...
New bug report some may wish to follow/participate in....
[https://bugs.launchpad.net/unity/+bug/882274](https://bugs.launchpad.net/unity/+bug/882274)

I gave up on Unity. GNOME 3 blows it away once you get used to it, especially with a dual monitor setup. From the sounds of the discussion in that bug report that's not going to change any time soon either. There's still something that bugs me about Mark's tone in any of those responses of his - sounds a lot like 'it's my ball' kind of crap. It's kind of putting me off of Ubuntu - thinking I may try fedora again.

Edit: Ended up switching back to Windows 7 - after a year and a half on Ubuntu, as the NVIDIA driver support in Ubuntu 11.10 is horrible. After trying Fedora (for the love of god someone please get those folks some decent fonts!), and 4-5 different ways to fail installing openSUSE I decided to quit wasting my time. As much as I dislike Windows, it works.

---

### Post by Mark Phelps on 2011-10-31
I must be an exception because I'm using Unity (11.10) with dual monitors -- and the experience is a lot better than with previous Ubuntu versions, in that I don't have to mess with the ATI restricted drivers to get multi-monitor displays.

But then, all you have to do is breath hard -- and UNITY is trashed, at least, that's what it seems now that 11.10 is out.

---

### Post by graphius on 2011-11-10
> I must be an exception because I'm using Unity (11.10) with dual monitors -- and the experience is a lot better than with previous Ubuntu versions
Very interesting, because one of the reasons I have been frustrated is Unity on multiple monitors. How can you get the dock thing away from the center of the view? ie, how can I have the dock either on the far left or far right of my desktop?
I use my multiple monitors for graphics, so I have my work on my high end calibrated monitor. I have a smaller and cheaper monitor to the left where I put all the dialogue boxes, image browser, etc. Unity INSISTS on placing itself on the left side of my right hand monitor, right in the way...
I have found hacks that allow you to put the dock on the bottom, but I am a bit reluctant to start adding random software to my nice stable system.

---

### Post by Nick Smith on 2011-12-29
> **blitzd said:**
> Ok, so I have a laptop with an external monitor, and a freshly installed 11.10 64-bit (desktop). I have my monitor to the right of the laptop, and I'd like to use it as the main screen when it's connected. 

I've managed to get past several nvidia/11.10 dual monitor issues and have both displays working with twinview, but my issue now is how do I get the unity bar to show up on my external screen?

I tried configuring the two displays to use separate x screens thinking maybe that would do it, but that was a whole new can of worms, and just resulted in a white old school x screen on my external monitor... or a frozen desktop with xinerama enabled.

I thought I'd give Unity a try again when I did a fresh install after 11.10 came out, and I've grown rather attached to using it to switch windows and workspaces now. But if I have to deal with my menu and all my apps opening on a monitor that is not my MAIN monitor, well - that's just not going to work out.

I hooked my computer up to my tv via an hdmi cord and was having the same problem. what i figured out is in the monitors set up if you drag the computer monitor under the tv monitor so its touching it somewhat works but its still a pain in the butt because the screens arent the same just whatever you open apears on the tv instead of on the computer.....try that its better then nothing and allot less work then hacking all the stuff to make it the same

---


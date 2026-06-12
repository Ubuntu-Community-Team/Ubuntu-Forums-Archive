---
title: "XGL/Compiz causes LCD monitor to make noise when scrolling"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by Number_6 on 2007-08-23
I'm running a Dell Inspiron 6400 laptop (Mobility Radeon X1400 video card). When I log into an XGL/Compiz desktop (just normal Compiz, haven't tried Compiz-Fusion or Beryl), my laptop's monitor makes a whirring sound whenever I scroll through a page (like in Firefox or a folder with lots of stuff in it). I'm tired of the dull looking Gnome desktop and I'd really like some eye-candy, but I'm worried about hardware damage. Can anyone help?

Thanks!

EDIT: Just to clarify, it doesn't do this on the standard Gnome desktop, just Gnome with XGL (come to think of it, I'm not sure I've checked without Compiz running. I'll have to do it later though, I have some other stuff to deal with right now).

EDIT2: It still makes noise without Compiz running, but not as much. It's most noticeable without Compiz whenever a window snaps to the the side of the screen.

EDIT3: Just the same with Beryl

---

### Post by Number_6 on 2007-08-23
No one's encountered this before? I've found some similar problems with searches, but no solutions.

---

### Post by Number_6 on 2007-08-24
Okay, last bump and I'll let this thread die.

---

### Post by jsully1 on 2007-08-24
I get a similar noise too on my T60 thinkpad, though I don't think it's actually your LCD.  I think it's CPU related - open up System Monitor and do some CPU intensive work and you should hear it make the same sounds.  XGL seems to definitely exacerbate the issue.

---

### Post by Number_6 on 2007-08-24
You know, I think you're right. There's a faint noise even when the screen doesn't change that corresponds with the CPU in the system monitor. Also, the noise is completely different when I'm running on battery.

While I'm glad that it's not my monitor that's the problem, I'm a bit worried about my CPU. From what I can tell, the noise has to do with the piezoelectric effect in capacitors. Since they're vibrating, could this damage them or reduce their lifespan? Is there any way to reduce the CPU usage of Compiz/Beryl? 

Thanks

---

### Post by pertti on 2007-10-03
I have the same laptop (Dell 6400, Radeon X1400) and it makes that noise you are talking about. It only happens with XGL, no matter wether Compiz is on or off. The CPU doesn't make such a noise when under heavy load.

I'm having this problem with Gutsy Beta, but I recall I could also hear the noise using Beryl and Feisty. In fact, that was one of the reasons I got back to regular X.org + Metacity. I want to try with another live CD distribution, e.g. openSUSE, and see if it does make the noise (I don't really thinks this is a Ubuntu-only problem).

---

### Post by _indie_ on 2007-10-05
I have a Dell XPS M170 laptop with an Nvidia Go 6800 Ultra card in it, or rather I did until the card blew a couple weeks ago. In the weeks prior to that I noticed this same noise, but didn't think too much of it. Compiz has seemed relatively free of issues damaging hardware, but now finding this thread I wonder if I took too much for granted.

Dell replaced my card with an Nvidia 7800 GTX, and the sound continued so I've sworn off compiz (compiz-fusion) until I find out more.

From my own observations I can say the sound is coming from the video card. It is a very high pitched resonation, almost like you would expect from an old CRT tube. I don't want to be alarmist, and I am not accusing compiz of anything at this point, but this is spendy hardware we have it running on, and any problem like this should be caught ASAP.

If anyone else has heard this sound from their card, or had an inexplicable failure of their video card shortly after (within a couple months) of installing compiz or compiz-fusion, please add something to this thread.

---

### Post by pertti on 2007-10-06
> **_indie_ said:**
> I have a Dell XPS M170 laptop with an Nvidia Go 6800 Ultra card in it, or rather I did until the card blew a couple weeks ago. In the weeks prior to that I noticed this same noise, but didn't think too much of it. Compiz has seemed relatively free of issues damaging hardware, but now finding this thread I wonder if I took too much for granted.

Dell replaced my card with an Nvidia 7800 GTX, and the sound continued so I've sworn off compiz (compiz-fusion) until I find out more.

Were you running Compiz with XGL or with AIGLX? I've noticed the sound when using XGL, even with plain Metacity instead of Compiz. I haven't tried with AIGLX since the latestt drivers for my ATI X1400 don't support it yet. However, it looks like it's not an ATI-only problem.

---

### Post by victorgreen on 2007-10-06
Funnily enough I just got the same sounds scrolling through this forum :) 

Im on an X61 which used to have compiz but 3d acceleration suddenly died 3 days after I got compiz working (it took out google earth too) so I uninstalled it. Im just using the default metacity now and I get the sound when scrolling through docs and sites.

---

### Post by pertti on 2007-10-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
OK, I've filed a bug in Launchpad about this issue. I've filed it against the xserver-xgl package, since in my case it only happens when I'm using Xgl (even if I use Metacity instead of Compiz). But** if you have experienced a similar problem, please report your configuration** (graphics card, Xgl or AIGLX...) so this can be further refined.

---

### Post by siavash.mahjoob on 2008-01-01
first time I installed compiz+xgl , I noticed  noise from inside of my laptop then understood 
this problem related to ATI driver that installed via restricted driver manager (XGL).
and finally I found a recommendation about this case in ubuntu bug report :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130)

"Xgl uses the graphics card more intensively than a standard unaccelerated desktop. In addition, it is known to be inefficient with CPU and graphics resources while scrolling. What's happening is that as you scroll, each line it goes down it generates a large spike of CPU and graphics instructions to re-render the screen, which causes the amount of power draw by components on your motherboard to change. This sudden change can often cause certain capacitors in your power supply unit to make weird noises."
John Dong

I  follow the instruction :
[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html](http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html)

and now everything is OK.:)

---

### Post by _indie_ on 2008-01-02
Interesting information, thanks for adding it. :)

If anyone knows of a similar solution for Nvidia cards please post. Mine is a Go 7800 GTX (used to be a Go 6800 Ultra til it blew (dunno if that was related to the XGL issue)).

I'm still leery of using XGL until this has been proven to be fixed. It seems to me that if the components are struggling so much that they resonate audibly, it would be logical to assume that this would shorten the life of the device.

---

### Post by lapicide on 2008-02-03
Thanks. I followed the instructions in the link below and happily the noise in my desktop disappeared. It had become quite a nuisance and was making it almost impossible to use the machine for any length of time.

> **siavash.mahjoob said:**
> first time I installed compiz+xgl , I noticed  noise from inside of my laptop then understood 
this problem related to ATI driver that installed via restricted driver manager (XGL).
and finally I found a recommendation about this case in ubuntu bug report :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/150130)

"Xgl uses the graphics card more intensively than a standard unaccelerated desktop. In addition, it is known to be inefficient with CPU and graphics resources while scrolling. What's happening is that as you scroll, each line it goes down it generates a large spike of CPU and graphics instructions to re-render the screen, which causes the amount of power draw by components on your motherboard to change. This sudden change can often cause certain capacitors in your power supply unit to make weird noises."
John Dong

I  follow the instruction :
[http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html](http://www.ubuntu1501.com/2007/12/installing-newest-ati-driver.html)

and now everything is OK.:)

---


---
title: "Touch pad wayyyy too sensitive!"
date: 2007-11-17
forum: Dell  Ubuntu Support
---

### Post by Tombo5150 on 2007-11-17
My touchpad is absolutely tooo sensitive. I don't even feel myself touch it when i type and it messes me up because the cursor will move or links will find themselves being clicked on. Is there any way to turn this down???

---

### Post by zhaozhou on 2007-11-17
Sure. The gnome-control-center has a mouse-sensitivity-setting. Try turning it down. (:

---

### Post by erfahren on 2007-11-17
there;s an additional configuration utility for Synaptic Touchpads  called GSynaptics. If you have a different make there may be one for it as well.

for GSynaptics you need to enter a line into the /etc/X11/xorg.conf in the touchpad section
Option		"SHMConfig"	"true"

---

### Post by viking777 on 2007-11-17
I hope one of the above solutions work for you, I have never tried either of them so I don't know how well they work.

FWIW my experience is that all touchpads are too sensitive with all versions of Linux whatever you do with them, that is why I always plug in a small portable usb mouse.

---

### Post by Tombo5150 on 2007-11-21
I do have a mouse, however its when i type that my hands accidentally touch it enough to move my cursor around and it is horribly aggravating. I'll try those two options, where is the gnome-control-center?

---

### Post by Tombo5150 on 2007-11-21
Or i just found in my mouse settings that I can turn off tap to click.......that sounds simple enough.

---

### Post by erfahren on 2007-11-21
> **Tombo5150 said:**
> Or i just found in my mouse settings that I can turn off tap to click.......that sounds simple enough.
Tap-to-click drives me nuts as well. I have no idea how anyone would find that useful. I don't have that option in my regular mouse settings though (what gives?), which is why I use GSynaptics.

One thing I do *immediately* after a fresh install of Ubuntu is add the following to the touchpad section of my /etc/X11/xorg.conf
Option		"MaxTapTime"		"0"

that gets me through until I install GSynaptics

---

### Post by scarboni on 2007-11-24
> **erfahren said:**
>  I have no idea how anyone would find that useful. 

I thought it fairly obvious that it's quicker to tap where your finger already is than to have to locate and/or tap on a button that is somewhere else.  But I am biased - either in my laziness or my striving for efficiency - I leave it for you to decide which.

---

### Post by teasum on 2007-11-25
I have had the same problem with every version of Ubuntu since 5.10.  I too have chosen to disable the tapt o click option, but I think it is a feature that should be better supported in Linux in general and Ubuntu in particular.  In XP, I have no trouble with the sensitivity of the touch pad... I scroll, and when I want to click something, I tap.  In Ubuntu, however, any touch that does not then move is registered as a tap.  I have tried adjusting the sensitivity via gsynaptics, but no luck.  For now, I'm happy with my usb mouse or the buttons on my Inspiron 8600; however, I would welcome tap-to-click back if it could be worked out.

---

### Post by buccaneere on 2007-11-25
> **Tombo5150 said:**
> My touchpad is absolutely tooo sensitive. I don't even feel myself touch it when i type and it messes me up because the cursor will move or links will find themselves being clicked on. Is there any way to turn this down???

...or turn it off??? How to disable tapping?

---

### Post by erfahren on 2007-11-25
> **scarboni said:**
> I thought it fairly obvious that it's quicker to tap where your finger already is than to have to locate and/or tap on a button that is somewhere else.  But I am biased - either in my laziness or my striving for efficiency - I leave it for you to decide which.
the problem I have is that I pick my finger up and set it down often just while normally using it. When I had that tap-to-click enabled I would inadvertently click on things. I'd unintentionally open and close programs, etc.

For me it wasn't useful, it was downright annoying.

---

### Post by erfahren on 2007-11-25
> **buccaneere said:**
> ...or turn it off??? How to disable tapping?
I have a Synaptics touchpad. If you have that you can use GSynaptics, it has the option to disable it.

What I do after a fresh install is put the following in under the touchpad section of my /etc/X11/xorg.conf
```

Option		"MaxTapTime"		"0"

```
if you have something other than a Synaptics touchpad you still might try that.

---

### Post by buccaneere on 2007-11-25
> **erfahren said:**
> I have a Synaptics touchpad. If you have that you can use GSynaptics, it has the option to disable it.

What I do after a fresh install is put the following in under the touchpad section of my /etc/X11/xorg.conf
```

Option		"MaxTapTime"		"0"

```
if you have something other than a Synaptics touchpad you still might try that.


Acer 5100 - 3825.

I got xorg configure open, but where in the list does the value go?

[I]section input device

identifier..............syn touchpad
driver.................synaptics
option................sendcoreevents..............true
option................device..........................dev/psaux
option................protocol........................auto-dev
option................horizscrollldelta................0

end section[/I]

---

### Post by erfahren on 2007-11-25
@buccaneere - look for this part:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MaxTapTime"	"0"
	Option		"SHMConfig"	"true"
EndSection

```
that "SHMConfig true" one is for GSynaptics. 

you have the same notebook as I do so anything you see in my section above that's different than what you have was added by GSynaptics.

As I mentioned, GSynaptics has the option to disable tapping as well so you really could either install gsynaptics (and add that "SHMConfig true" line in there for it). or just add the "MaxTapTime" "0" option in there. - it's up to you

In any event that's where it goes.

---

### Post by buccaneere on 2007-11-25
> **erfahren said:**
> @buccaneere - look for this part:
```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option		"MaxTapTime"	"0"
	Option		"SHMConfig"	"true"
EndSection

```
that "SHMConfig true" one is for GSynaptics. 

you have the same notebook as I do so anything you see in my section above that's different than what you have was added by GSynaptics.

As I mentioned, GSynaptics has the option to disable tapping as well so you really could either install gsynaptics (and add that "SHMConfig true" line in there for it). or just add the "MaxTapTime" "0" option in there. - it's up to you

In any event that's where it goes.

Excellent there erfahren. Works perfect! [NOT]:guitar: 

Was the wireless difficult to initiate? This is a fresh install/linux newb also...

Thanks........

---

### Post by erfahren on 2007-11-25
> **buccaneere said:**
> 
Was the wireless difficult to initiate? This is a fresh install/linux newb also...
not really, but there's a little story to that for me.

First off, I just use my wifi at home and have my computers set up with static IP addresses (as opposed to using DHCP) and WPA encryption. Fiesty had a problem with using WPA when setting up through the Network Manager. So what worked for me is the guide here: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
...which just basically sets up everything through the /etc/network/interfaces file manually. (There's a script there to restart netwoking when booting up as well.)

So when I went to Gutsy I messed around just a little trying to set it up through the Network Manager and after I didn't get immediate results, I just went back to setting it up the way I did before.

so it wasn't really difficult, but I never really got into it too much with Gutsy.

... that wasn't very helpful was it? lol

but I suggest that if you don't use wifi at home and go somewhere to try it (wireless "hot spot", cafe or whatever) then look into it ahead of time (and save some various instructions and troubleshooting guides to have them on hand) in case you run into problems.

BTW: what did you mean in your post by "works perfect[NOT]", it isn't working well?

---

### Post by buccaneere on 2007-11-25
> **erfahren said:**
> 

BTW: what did you mean in your post by "works perfect[NOT]", it isn't working well?


I'm meanin' that the fix is workin', and the touchpad ain't.! Just the way I like it. Thanks.

---

### Post by bluedragon436 on 2007-11-25
I just went into the mouse settings and turned my down, and it works just fine with my touchpad, the little nipple-mouse, as well as an attached USB mouse.....but maybe I was just lucky in this.....

---


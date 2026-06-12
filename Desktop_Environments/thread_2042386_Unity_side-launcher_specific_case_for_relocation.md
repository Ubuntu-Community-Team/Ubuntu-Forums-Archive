---
title: "Unity side-launcher: specific case for relocation"
date: 2012-08-14
forum: Desktop Environments
---

### Post by decibelcooper on 2012-08-14
Dear peeps,

I've found threads that talk about the Unity side launcher not being relocatable.  They are, however, closed.

In most cases, I like the launcher on the side just fine.  I don't agree with the idea that one should "just live with it" on the side, but for me I do just that without complaint for the most part.  However, I wanted to describe a particular case where the side-launcher in 12.04 just doesn't work for me.  This is a plea for more customizability for function, not form.

I have an old Thinkpad X41 tablet pc.  I use it exclusively for notes and scratch with its Wacom enabled screen.  I can't use Windows and keep my sanity, so naturally I have Ubuntu on there, for a worry free GNU/Linux experience.

With the screen rotated to profile mode the way you would write on a normal piece of paper, the Unity launcher squeezes the available space down to a width that is unreasonably small (I have the launcher icons set to the smallest size, but the resolution on this screen isn't high).  Starting in 12.04, if I have the launcher auto-hide, I can't get it to pop up with the pen, since it's an absolute position pointer, not relative. Hence even with the highest sensitivity, the launcher will not pop up unless I bail on tablet mode by opening it up, turning the screen around, and using the trackpoint.

If I could move the launcher to the bottom, this aggravating problem of mine would disappear.  The other alternative is reverting the launcher un-hide ability so that a relative pointer can open it.  The latter is not nearly as desirable as the former.

The low level of customization in unity should be addressed.  I'm not saying it can be an overnight thing, but plans for improving this would make it easier for me to deal with the shortcomings for now.  I may switch to xfce, but I do like Unity in general so I am reluctant.

Thanks for reading my thoughts,
- dBCooper

---

### Post by Jay MC on 2012-08-14
Not much consolation, but I agree.

I think I understand why customisation is limited.  Designing a new desktop environment isn't a trivial task, and presumably, beginning with a less customisable environment has fewer variables (and less potential for bugs).  It's a more manageable task to start with.

However, if Canonical were going to implement just *one more* bit of user configuration in the short term, then the ability to move the launcher to the bottom of the screen feels like it would probably be a popular one?

---

### Post by Roger E Critchlow Jr on 2012-08-19
I just went through a similar search for solutions to the same problem.   Relocating the launcher would help me.  But the real solution is to make the autohide work correctly with a stylus or touch panel, where ever the launcher is located.

This issue is raised in this bug report, which is confirmed but given a low importance because we're using unusual hardware.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938758](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/938758)

---

### Post by cariboo on 2012-08-19
The developers don't as a rule read the forum, so your post really doesn't do much good here. Unity is open source, so you are welcome to make changes yourself, or to hire a developer to do it if you don't have the skills yourself.

---

### Post by mc4man on 2012-08-19
While awaiting a fix I'd probably try a few things (if I was affected which I am not

A toggle could be created using a script to switch modes, then activated by edge binding or desktop launcher. A little funky & would expose a minor window shift bug when changing mode to always with a window open.

What I'd likely try with is an xdotool script set to a left edge, top or bottom left edge binding. Obviously don't have the means to test with your wacom so don't have a clue if super means anything?

Note that this may work out, may not, to disable remove the command & binding from ccsm

To try if inclined - 
install xdotools

Create a small script, easiest to put in PATH so I'd create a bin in home, then restart & it would be added
So like 
```
mkdir bin
```
restart
Assuming the above - 
```
gedit ~/bin/show1
```

Use this,  blue is adjustable. 0.3 seems good
```
#!/bin/bash
xdotool keydown super
sleep [COLOR="Blue"]0.3[/COLOR]
xdotool keyup super

```
Then close out gedit & 
```
chmod u+x ~/bin/show1
```

Then open compizconfig-settings-manager (install if need be
```
ccsm
```

Enable the 'Commands' plugin, then open the plugin settings
For command just enter
show1
Click on the bindings, for command 0 click on 'edge', I'd go with top & or bottom if inadvertent left edge is an issue
(if going left edge may get a conflict with 'flip left', can ignore if desired
As soon as the launcher is exposed (if it is??) then slight  move up or down & it should then stay exposed till cursor leaves

---

### Post by asuastrophysics on 2012-11-12
I agree that not allowing users to change the position of the launcher is ridiculous. There was a plugin called Unityshell-rotated that would accomplish this, but it does not work for 12.XX. The developer has not released any new updates for this plugin since December of last year, and it is probably safe to say that he either quit developing it or gave up. It's now mid-November. 

I am riding out 11.10 until it becomes unsupported. If there is still no bottom launcher workaround for a newer version of Ubuntu by the time this happens, I'm dropping Ubuntu entirely and going with a different flavor of linux. This lack of customization and support for those who want it is completely inexcusable for an operating system that totes itself as being open-source and open to the suggestions of the community. No offense, but it is the truth.

---

### Post by Frogs Hair on 2012-11-12
The bottom launcher was for one specific version of Unity and only for 32 bit in the beginning. There may have been bigger picture to consider when it came to maintaining that project. It was a Compiz plugin which has also changed since since the plugin was created.

---


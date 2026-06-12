---
title: "Adjust touchpad sensitivity"
date: 2007-08-29
forum: Dell  Ubuntu Support
---

### Post by wireddad on 2007-08-29
I was trying to follow the instructions at:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adjust_touchpad_sensitivity](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Adjust_touchpad_sensitivity)

Is the instruction for both/all Ubuntu flavors of 7.04?  Or just Kubuntu?  Thanks.

---

### Post by kuja on 2007-08-30
It'll work for all flavours.

---

### Post by wireddad on 2007-08-30
It does not matter if it says the same thing, just add the extra options?  And reboot?  It did funny thing like I was not able to type or copy/paste into the run menu.  It was fun trying to redo the xorg.conf file.

---

### Post by kuja on 2007-08-30
You can play with the settings to get things "the way you like them": 
Option		"MinSpeed"		"1.0"
Option		"MaxSpeed"		"1.3"
Option		"AccelFactor"		"0.3"

I personally use these:
MinSpeed of 0.75 and MaxSpeed of 0.9 (I don't have the other one set)


There are other interesting things you can do to the touchpad though. I've got a script setup to have syndaemon making it such that the touchpad is disabled for a second or two after typing.

Another thing I've found handy is a program called qsynaptics.

---

### Post by mrli on 2008-03-25
I know it's an old post but the script kuja mentions, is exactly what I need, so if someone has it please post it !

---

### Post by notwen on 2008-03-25
> **mrli said:**
> I know it's an old post but the script kuja mentions, is exactly what I need, so if someone has it please post it !

This is relatively easy.  We're going to edit xorg.conf again, so back up your current one first.  Once you've got your backup you simply need to add the following to your Synaptics Touchpad section before the 'EndSection'.

```
Option "SHMConfig" "on"
```

 Save and close.  Now let's add this to your startup so it's in effect every time you boot up your machine.  System--->Preferences--->Startup

Add a New Entry, name it whatever you prefer and use the following for the command:

```
syndaemon -t -d
```

Let me know if you have any issues getting it working.  =]

---

### Post by gfxguy on 2008-03-27
Thanks for the wiki link, now I have the reverse question...

So the wiki shows how to configure things like the sensitivity... I despise the touchpad, I absolutely hate using them, and have two external mice (one wireless) just to avoid using it...

But I tend to brush the surface while typing and not even using the mouse, making the mouse go all over (and if I hit it hard enough, doing a button click).

So I want to disable it completely.  I thought I'd disabled it in bios, but it didn't seem to have any affect.

---

### Post by xjb2003x on 2008-04-10
I have 8.04 and was able to get rid of the touchpad.  I found it under systems - preferences - mouse

---


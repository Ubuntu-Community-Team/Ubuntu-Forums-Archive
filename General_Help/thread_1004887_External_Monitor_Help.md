---
title: "External Monitor Help"
date: 2008-12-07
forum: General Help
---

### Post by nvikram on 2008-12-07
Hello,

I currently am working on a laptop with Ubuntu 8.10, but I have an external Monitor. When I plug-in the monitor I have to go to the screen resolution application turn my laptop monior off and the external one one. Which is a pain. I was wondering if there was anyway to keymap a keyboard shortcut that could switch to my external monitor (1280x1024) or back to my laptop (1280x800). Any help is greatly appreciated.

Thanks :)

---

### Post by jgoguen on 2008-12-07
Does your keyboard have a button that has what may appear to be an empty square in it?  Perhaps with a vertical line on either side.  On most (maybe all?) modern laptop keyboards, it's the F4 key.  If you push Fn+F4 (or FN+whatever button for you) with the external monitor attached, it should cycle through laptop monitor, external and laptop, and external only.  Can you let us know if you can find that button, and if you can whether connecting the monitor and pushing it with the Fn key works for you?

---

### Post by utnubuuser on 2008-12-07
Fn+F7 on thinkpad

cool tip!  thanks

---

### Post by nvikram on 2008-12-07
> **jgoguen said:**
> Does your keyboard have a button that has what may appear to be an empty square in it?  Perhaps with a vertical line on either side.  On most (maybe all?) modern laptop keyboards, it's the F4 key.  If you push Fn+F4 (or FN+whatever button for you) with the external monitor attached, it should cycle through laptop monitor, external and laptop, and external only.  Can you let us know if you can find that button, and if you can whether connecting the monitor and pushing it with the Fn key works for you?

Yea, for me its Fn+F4, And when i hit it, nothing happens. Even when the the cable is connected.

---

### Post by jgoguen on 2008-12-08
Do you know what card you have, or at least what driver you're using?

---

### Post by nvikram on 2008-12-08
> **jgoguen said:**
> Do you know what card you have, or at least what driver you're using?

Yeah I am using an Intel 965GMA Card with the Intel gma965 Linux Driver.

---

### Post by jgoguen on 2008-12-09
There's a limitation in that card requiring the screen resolution to be less than 2048x2048.  That could be why the external monitor key won't work, it would bring one side of the screen over 2048.  Try this command with the monitor attached:
```
xrandr --output VGA --same-as LVDS
```
That should clone your laptop monitor to your external monitor.  Once you're done, you can turn off cloning with:
```
xrandr --output VGA --off
```
If those work for you, you can make a script for them and add icons to one of your panels to make it easier to switch from cloning to laptop only.

---

### Post by nvikram on 2008-12-09
> **jgoguen said:**
> There's a limitation in that card requiring the screen resolution to be less than 2048x2048.  That could be why the external monitor key won't work, it would bring one side of the screen over 2048.  Try this command with the monitor attached:
```
xrandr --output VGA --same-as LVDS
```
That should clone your laptop monitor to your external monitor.  Once you're done, you can turn off cloning with:
```
xrandr --output VGA --off
```
If those work for you, you can make a script for them and add icons to one of your panels to make it easier to switch from cloning to laptop only.

Tried both commands with the VGA cable attatched and I got no results. Nothing happened. The command finished but with no effect, no errors, or anything like that.

---

### Post by jgoguen on 2008-12-10
Most likely I have the output names wrong then.  Can you please post the output of this command with the monitor attached, inside a code block:

```
xrandr
```

That will give a lot of information, among it the names of your displays.

---

### Post by nvikram on 2008-12-13
> **jgoguen said:**
> Most likely I have the output names wrong then.  Can you please post the output of this command with the monitor attached, inside a code block:

```
xrandr
```

That will give a lot of information, among it the names of your displays.

Ok, this is what I get. (btw, the external monitor is connected.)

```
vikram@vikram-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1280 x 1280
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0*+   60.0  
   1280x960       60.0     60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
vikram@vikram-laptop:~$ 


```

---

### Post by jgoguen on 2008-12-14
When you did that, were you using the external monitor as the main monitor?  Or was the laptop monitor the only one being used?  It looks to me like you're only using the external, but I want to make sure.  Based on that output, it looks like your external monitor is named "VGA", your laptop is named "LVDS", and you're currently using your external monitor only at 1280x1024 resolution.  Which means I got the output names right.

Try one of these commands based on what your setup is right now (when you're reading this):

[LIST]
[*]if you're using the external monitor only, try this command:
```
xrandr --output LVDS --same-as VGA
```
[LIST]
[*]Use this command to go back to external only:```
xrandr --output LVDS --off
```
[/LIST]
 
[/LIST]

[LIST]
[*]If you're using the laptop monitor only and the external monitor is plugged in and turned on (but not active), use this command:
```
xrandr --output VGA --same-as LVDS
```
[LIST]
[*]Use this command to go back to laptop only:```
xrandr --output VGA --off
```
[/LIST]
[/LIST]

---

### Post by nvikram on 2008-12-14
> **jgoguen said:**
> When you did that, were you using the external monitor as the main monitor?  Or was the laptop monitor the only one being used?  It looks to me like you're only using the external, but I want to make sure.  Based on that output, it looks like your external monitor is named "VGA", your laptop is named "LVDS", and you're currently using your external monitor only at 1280x1024 resolution.  Which means I got the output names right.

Try one of these commands based on what your setup is right now (when you're reading this):

[LIST]
[*]if you're using the external monitor only, try this command:
```
xrandr --output LVDS --same-as VGA
```
[LIST]
[*]Use this command to go back to external only:```
xrandr --output LVDS --off
```
[/LIST]
 
[/LIST]

[LIST]
[*]If you're using the laptop monitor only and the external monitor is plugged in and turned on (but not active), use this command:
```
xrandr --output VGA --same-as LVDS
```
[LIST]
[*]Use this command to go back to laptop only:```
xrandr --output VGA --off
```
[/LIST]
[/LIST]

Ok. Previously, I was using just the VGA monitor. When I use the first command nothing happens. The second command causes X.org to crash and resets my system. Third command does nothing and the 4th command crashes X.org and resets my system. I have tried all the commands on both just the laptop and on just the external monitor.

---

### Post by nvikram on 2008-12-14
Just fyi. I want to be able to use my monitors in 3 modes. 1) Just the Laptop (1280x800) 2) Just the Ex. Monitor (1280x1024) 3) Cloned (Preferrably at my preferred resolutions, but I can live with the same resolution on both( i.e. 1024x768)). So far the only way to do this is through the screen resolution application, but that is just a total pain to keep going back and forth. I liked your idea of a panel shortcut option so If I couldn't map a keyboard function, I could atleast click one icon.

---

### Post by linux_tech on 2008-12-14
You should be able to accomplish that by using either xrandr or xorg.conf
this article explains how-
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

---

### Post by nvikram on 2008-12-14
> **linux_tech said:**
> You should be able to accomplish that by using either xrandr or xorg.conf
this article explains how-
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

Hmmm. The reading is intresting, but thats for extended desktop. I just want to permanently switch from one to the other or clone both.

---

### Post by linux_tech on 2008-12-14
This article explains more on using xrandr or xorg to regulate video choices. I like xrandr because it is dynamic, faster to troubleshoot and usually resolves issue faster.   
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

---

### Post by nvikram on 2008-12-14
> **linux_tech said:**
> This article explains more on using xrandr or xorg to regulate video choices. I like xrandr because it is dynamic, faster to troubleshoot and usually resolves issue faster.   
[http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html)

When it comes to X.org and XrandR, I am complete newb. Could you help me set it up with these specs

Screen:LVDS (1280x800)
Screen: VGA (1280x1024)

For now all I want todo is switch from one to the other.

---

### Post by jgoguen on 2008-12-14
> **nvikram said:**
> Ok. Previously, I was using just the VGA monitor. When I use the first command nothing happens. The second command causes X.org to crash and resets my system. Third command does nothing and the 4th command crashes X.org and resets my system. I have tried all the commands on both just the laptop and on just the external monitor.
The commands with --off should only have been run if the one before it worked.  Sorry I wasn't clearer about that.  Also, only one of the first and third commands should have been tried.  One will legitimately do nothing, the other should have cloned the output.  Still, it's strange that any of them would force a system reset...

Let's try something similar and see what happens.  Set yourself up so that you're only using your laptop monitor, but your external monitor is plugged in and turned on.  At this point, your laptop should be displaying everything, and your external monitor displays nothing.  Then, use this command:
```
xrandr --output VGA --same-as LVDS
```
That should clone them, so not both monitors are displaying the same thing.  If (and only if!) this is actually what happened, use this command to go back to using only your laptop:
```
xrandr --output VGA --off
```

---

### Post by nvikram on 2008-12-14
> **jgoguen said:**
> The commands with --off should only have been run if the one before it worked.  Sorry I wasn't clearer about that.  Also, only one of the first and third commands should have been tried.  One will legitimately do nothing, the other should have cloned the output.  Still, it's strange that any of them would force a system reset...

Let's try something similar and see what happens.  Set yourself up so that you're only using your laptop monitor, but your external monitor is plugged in and turned on.  At this point, your laptop should be displaying everything, and your external monitor displays nothing.  Then, use this command:
```
xrandr --output VGA --same-as LVDS
```
That should clone them, so not both monitors are displaying the same thing.  If (and only if!) this is actually what happened, use this command to go back to using only your laptop:
```
xrandr --output VGA --off
```

Nope it does nothing. :(

---

### Post by jgoguen on 2008-12-15
I have no idea why that isn't working for you. :(  I suggest taking your question to the Ubuntu Users mailing list, it's possible that there's someone there who knows a lot more who hasn't seen this thread.  You can sign up by going to [https://lists.ubuntu.com/mailman/listinfo/ubuntu-users](https://lists.ubuntu.com/mailman/listinfo/ubuntu-users) and filling out the section for subscribing.  Then, once that's done, send an email to [email]ubuntu-users@lists.ubuntu.com[/email] re-stating your question.  Also mention that you have tried using xrandr with no success, and include a link to this thread so people can see what hasn't worked for you.

---


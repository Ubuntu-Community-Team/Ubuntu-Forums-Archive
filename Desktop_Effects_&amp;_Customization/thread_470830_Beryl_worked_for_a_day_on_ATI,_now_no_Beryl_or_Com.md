---
title: "Beryl worked for a day on ATI, now no Beryl or Compiz (Beryl message included)"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by OzzyFrank on 2007-06-11
Hi. Now, while I'm not one of those who cry and moan and curse Ubuntu for being in Beryl Hell, and swear I'll uninstall Ubuntu coz the only reason I installed it was so I could spin a desktop cube around all day, I thought I'd finally put a post up in case someone has an answer.

Yes, I know, throw out the ATI card and go for Nvidia... hehe... but after installing Ubuntu the second time (my Edgy drive died so I installed Feisty on the new one) and finding Beryl had gotten easier to download and install, I thought I'd give it another shot. Didn't bother trying to fix up ATI's lack of drivers for my Radeon 9200, as in Edgy i found I was happy with the xorg driver as long as i had a choice of resolutions.

Anyway, Beryl installed and worked, for a day anyway (that could have been one session, and then died after the next boot?). Now, if i try to start Beryl it tries painfully to load but reverts back to the default theme (or the one i have set, I should say). Here and there (maybe when I try ot run "beryl" from the prompt?)  it will do what others complain of, being the missing title bars (when that happens I can't even cycle through windows/programs with alt+tab, but I can bring up a terminal and type either metacity or compiz and it "fixes" it). As for selecting Beryl as the windows manager in Beryl manager menu, that's when it reloads all windows 2 times trying to change the theme, and the selected window manager always reverts back to Metacity.

Oh, and I can't get back the Wobbly Windows, and it tells me that Desktop Effects can't be enabled, so does that mean that Compiz isn't working either?

I've tried getting the ATI drivers happening, and they install, but invariably I get an xserver crash upon boot and I have to replace my xorg.conf at the prompt. But I'm pretty sure that when I got Beryl up and running originally that I had only gone as far as getting some higher resolutions than 1024x768 by reconfiguring xorg.conf.

So what I would like to know is if Beryl can run on my card, can I get it back? Does the output below offer any info you guys understand? I've gone to uninstall Compiz, then noticed it said it was taking ubuntu-desktop with it, so declined. And since most people have Compiz, Metacity and Beryl running happily besides each other, I'd rather see if i can fix this.

Hope that is enough info. Thanks in advance guys.

Frank

(PS: Added the output from desktop-effects from the prompt)

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0


now desktop-effects:

nvidia hardware not available
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real: Failed to manage screen: 0
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4600003 specified for 0x46007c8 ().

---

### Post by Soybean on 2007-06-11
Well, I've never seen it before, but it looks like your problem is with "non power of two texture support." Some sort of driver thing from the sounds of it... I don't really have any idea what it is, but the important thing is that Beryl wants it and thinks you don't have it. ;)

Here are a couple of forum threads I found that seem related:
[http://ubuntuforums.org/archive/index.php/t-388451.html](http://ubuntuforums.org/archive/index.php/t-388451.html)
[http://ubuntuforums.org/showthread.php?t=352350](http://ubuntuforums.org/showthread.php?t=352350)

It looks like some people solved it using the following line to start beryl:
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl-manager
```

---

### Post by OzzyFrank on 2007-06-12
Hiya. Had mixed results with that command, as it initially brought Beryl back to life, but before I could post a reply regarding my success, it crashed and took the system with it. Or should I say things got slower and slower then finally I had to reboot. Since then, that same command has done the same as trying to load Beryl before, ie tries but goes back to Metacity, and also has loaded Beryl but without title bars (and you can't move windows, or alt+tab between them). I now have Beryl up with a script that has a variation of the fglrx command in it; don't know if that means the extra bits like "sleep" made a difference, or if this is somehow (amazingly) an intermittent problem. Here's the script:

[B][COLOR="Purple"]!/bin/sh
beryl-manager
sleep 1 
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
fi[/COLOR][/B]

and here is the output from the offending 2 textures line onwards:

[COLOR="Blue"][B]Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
beryl: water: GL_ARB_fragment_program is missing
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
[Snow]: Loaded Texture /usr/share/beryl/snowflake2.png
beryl: water: GL_ARB_fragment_program is missing
^[[Cberyl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing[/B][/COLOR]

The quest continues...

Frank

---

### Post by OzzyFrank on 2007-06-15
Just confirming that small script continues to bring up Beryl without fail, and only mucking with Compiz settings or trying to make Beryl the window manager via its menu etc kills it. If i just initiate it and go do my stuff and open a bunch of programs and maybe change Beryl settings and Emerald themes, all is fine till i shut down. About the panel menu button, it still lists Metacity as the manager, even though Beryl is running fine, and trying to change this kills Beryl, so just leave it as it is and enjoy Beryl. So far it has been really stable, and I have to admit that while at first I was like "Yeah, but I have to run a script to get it going..." I'm seeing it as a plus, as I actually prefer not to automatically load it. The bells and whistles are great, but who really needs them the whole time, especially as no matter how fast your PC and video card is, it's always going to run quicker without such eye-candy. And when I want to impress those who think Vista looks so cool it might just be worth shelling out a few hundred bucks for, all I have to do is double-click an icon and show them the wonders of Ubuntu and Beryl!

---

### Post by zero244 on 2007-06-15
You should be able to get beryl working with your card.
If you go with XGL it should work.
Set it up so XGL loads in a separate session. So if you have a problem with beryl you can log in with your standard desktop config.
I have beryl running perfectly with XGL and a nvidia card......I could never get berly working with aiglx or anything but XGL.
I have all the effects and have been running it for a week now and not one problem.
I will post a link for a how to with XGL and ATI. Its very simpe to set up.....just some cut and past.
Beryl can be hell to setup....but once you get it running right......its very impressive.
Dont give up..........I think just about every video card can work if you tweak it right.
Also if you do get beryl up and running the way you like.......leave it alone......and dont do updates.......they can only cause problems.
Good Luck.

---

### Post by OzzyFrank on 2007-06-15
Hiya. Not sure if the difference between nVidia and ATI is that one runs Beryl with XGL and the other AIGLX, but Beryl is running on my ATI with the script above, the terminal output telling me it is running AIGLX. Would like to try adding an XGL session to my list of options. But for now at least I can double-click a link to a script and it works. Can't tell you why the desktop "cube" is only 2D though, hehe. I even made sure I had 4 desktops in case, even though having 2 when i originally got Beryl to run after installing gave me a proper 3D cube (it's trivial, but still a "problem" of sorts).

So one thing I have been trying to get going since Edgy is nearly where I want it... being able to boot straight into Beryl at login would be even better...

... now for that Leadtek Winfast TV Expert card that still isn't being recognised...

---

### Post by ForzaItalia250 on 2007-06-16
> **Soybean said:**
> 
It looks like some people solved it using the following line to start beryl:
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl-manager
```

This worked for me! I encountered a similar problem of having it work at first and then refuse to start (ATI Mobility 9600 64mb) but using this fixed everying =D

---

### Post by OzzyFrank on 2007-06-16
Yeah, the single-line command worked for me too... at first. But that little script works a charm every single time. I can force Beryl to crash and it will come back to life as soon as I run the script. So at least this post contains 2 different solutions for people to stumble on.

---

### Post by Soybean on 2007-06-16
Regarding your 2d cube... can you get into your Beryl settings without everything going to hell? If so, in the Desktop section, make sure the Desktop cube is checked, and make sure the Desktop plane isn't (if it's even there). Then, in the Desktop Cube options, make sure you haven't got anything weird checked (things like "slide when changing viewports..." or "keep the cube planar..."). 

As for starting beryl at login, it should be easy enough... in theory. :D I can think of 3 ways that might work.
1) Add your script as a Startup program under System-Preferences-Sessions
2) put "LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa" (without quotes) in /etc/environment **WARNING: I have no idea what this does in general, or what it might do to other programs, but it ought to help Beryl work better** If this doesn't ruin everything completely, it might even make beryl-manager work.
3) As zero244 recommended, follow a guide for XGL/Beryl on Feisty. I'm not sure what video driver you're using, but you'd probably want to go with fglrx if you go this way. This would probably be the most stable solution in the end, but there might be some snags along the way, since the guide will assume that you're starting from a "no Beryl" position rather than... wherever you actually are. ;)

---

### Post by OzzyFrank on 2007-06-16
Yes, I can get into the Settings Manager fine, and do anything I like in there. That's why i said it seems stable, as I can change settings as much as I please. Try to do something like set Beryl to be the manager in the menu (even though it is already running) kills it. And yes, gone through those 3D cube settings trying to fix it, but no go yet. The interesting thing is that when I got Beryl to work again, it remembered all my settings from when i initially got it to run after install. So why it gave me a 2D cube is beyond me. I thought it could have been something in that command or script that gets Beryl up again.

As for startup, thought about adding the script to the startup (note that I've said the one line command only really worked once, so it will not cut it for me... it would have to be a link or reference to the script, which does work without fail for me each time). But I'd rather see about creating a separate session for boot up. The script I can run with a simple double-click. As for the other suggestion, if you don't know how much damage it could possibly do, then I'm afraid I don't even wanna know about it. And since Beryl manager works, that isn't an issue anyway. So where I am is that I can get Beryl to work with a script, can use the manager no worries, but the cube is 2D and Beryl is listed as disabled (or not the current window manager at any rate) in its own menu.

Any links to decent guides on how to get Beryl to start in an XGL session or whatever would be appreciated.

---


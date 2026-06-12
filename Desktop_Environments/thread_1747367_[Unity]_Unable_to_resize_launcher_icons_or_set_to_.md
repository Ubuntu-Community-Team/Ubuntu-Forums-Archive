---
title: "[Unity] Unable to resize launcher icons or set to auto-hide... any workarounds?"
date: 2011-05-02
forum: Desktop Environments
---

### Post by Entyrion on 2011-05-02
I recently upgraded to 11.04 and I've been tweaking Unity to get the desktop just the way I like it. I've come across two minor problems though:

1. When I tweak the icon size settings in the Unity tab of CCSM, the icons do not change size; they remain at the default "48" setting regardless of what I type in.

2. When I set the Unity launcher to auto-hide (also in the Unity tab of CCSM), it stays at the default "dodge windows" setting.

Are there any workarounds to change these settings when tweaking them in CCSM's interface does not work? (Or is there some trick I don't know to get CCSM to work properly?)

Thanks guys!

---

### Post by Copper Bezel on 2011-05-02
Do any of the CompizConfig settings apply to Unity, or is it just those two that have problems?

---

### Post by Entyrion on 2011-05-02
CompizConfig in general is working (I'm able to set wobbly windows and edit the open/close window animations, etc). However, it does not seem like any of the settings in the Unity Plugin tab of CCSM are working. For example, to tweak the panel opacity, the Unity Plugin tab's opacity settings did nothing at all. I had to figure out the workaround I mentioned here: [http://ubuntuforums.org/showthread.php?t=1746381](http://ubuntuforums.org/showthread.php?t=1746381)

Is there a way to kick the Unity Plugin in the pants to get it to work, or maybe another similar workaround like the one I found?

Thanks!

---

### Post by Copper Bezel on 2011-05-02
I really don't know then, honestly - I'm going by the guides, as I haven't actually upgraded yet. That shouldn't happen and sounds like a bug, but hopefully someone else can help you identify it. Sorry.

---

### Post by mc4man on 2011-05-02
I would suggest temp creating another user and then logging into that user and see if you can adjust the unity specific settings.
If so then it's either some setting changes you've made or possibly some setting carried forward from the upgrade
(never done an upgrade so don't know how that's handled

If the above is the case and you wanted to start fresh than there are 2 commands where either should do so, minor diff's. (in this case I'd use the 2nd command or both

unity --reset
gconftool --recursive-unset /apps/compiz-1

---

### Post by Entyrion on 2011-05-02
Hmm. I created a temp profile and tried modifying ccsm settings from there and it looks like the same problem came up. I was able to enable generic Compiz effects like wobbly windows, but none of the changes I made to the Unity Plugin menu had any effect (icon size, transparency, auto-hide, etc). 

In the terminal from that same temp profile, I also ran 

unity --reset 

and it gave me an error that reads:

...
Initializing session options...done
compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"

and it's stuck there so I can't input any new terminal commands (although the computer itself seems to be running just fine) =\

For additional information, I didn't mean to be misleading when I said "upgraded" but I simply meant that I had replaced my old 10.10 system with 11.04, but the actual process involved a fresh install, not the automated upgrade process.

Also, I'm not sure what the error message above means, but it might be worth mentioning that Unity 3D does not automatically run on my machine... in order to get Compiz to work at all, I have created a special launcher on my desktop to run "compiz --replace" and only after running this will any of the 3d settings kick in. I'm just confused as to why all the other ccsm settings can be tweaked just fine and the Unity 3D UI is running just fine, but the Unity Plugin menu in ccsm seems to have no effect at all >.<

---

### Post by mc4man on 2011-05-02
> I'm not sure what the error message above means
Normally I'd think it means your graphic's doesn't support unity and the unity plugin isn't running.. 
But you've indicated it is?
(you aren't running unity-2d are you?

What does this say 
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Entyrion on 2011-05-02
```
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV250 4C66) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no
```

So am I running Unity 2D then? WITH Compiz enabled? My understanding was that the two were incompatible. I installed the Unity 2D desktop environment separately and when in that, I am not able to enable any Compiz settings (like wobbly windows, cube desktop, and other animations --which I AM running just fine now O.o). When I select the "Ubuntu" (therefore Unity) desktop environment from the login screen, it initially boots to Unity 2D without any eye candy, but as soon as I use my "compiz --replace" launcher, Compiz seems to be working just fine.

However (just to throw yet another complicating factor into this mess), even if I am running Unity 2D WITH Compiz... I've downloaded the Unity 2D Configuration tool ([http://www.ubuntugeek.com/a-simple-gui-for-unity-2d-settings-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/a-simple-gui-for-unity-2d-settings-on-ubuntu-11-04-natty.html)) and when toggling that auto-hide option, nothing happens >.<

Wow, I'm confused /facepalm =P

---

### Post by Copper Bezel on 2011-05-02
Weird. Yes, Unity 2D is compatible with Compiz. The Unity plugin, specifically, has caused trouble on some graphics cards that are supported by Compiz. But the 2D settings, such as they are, should apply....

---

### Post by mc4man on 2011-05-02
unity-2d in natty uses qt4 so it has nothing to do with compiz

While I've never used it, (2d),  looks like the config tool uses gconf settings, have you had a look around in gconf-editor?

---

### Post by Entyrion on 2011-05-02
So it appears that you guys were right... I am running Unity 2D, and the custom launcher is simply rebooting Compiz to run alongside Unity 2D (rather than magically making my computer run Unity 3D as I had thought). I was able to trigger the auto-hide function by using the 2D desktop config GUI to set the launcher to auto-hide before activating the "compiz --replace" launcher, so I've figured that problem out :) Thanks guys!

Now to see if the icon customization instructions at [http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html) will let me shrink the icons a bit ^.^

---


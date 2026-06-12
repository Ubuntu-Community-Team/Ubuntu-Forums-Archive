---
title: "Unity 2D Launcher Resize Options?"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Entyrion on 2011-04-30
I recently installed 11.04 and Unity 2D (because my old laptop can't run the full 3D version). So far I'm pretty impressed and its growing on me, despite the negative press I'd heard and my own skepticism of change going into the new UI.

One thing that I haven't been able find out is if there is an option to vertically resize the launcher based on the number of active icons. I only have about half a dozen icons pinned to the launcher permanently, so there's a lot of blank "dead space" on the bottom half of the launcher unless I have a zillion other things open simultaneously. 

Is there a way to make the Unity 2D launcher automatically shrink upwards to fit the number of pinned icons + active applications? (I've attached a mock up of the sort of feature I'm talking about.) It would be fantastic if there was a way to do this because it would be a much cleaner and more efficient use of my screen space. I've already downloaded the Unity 2D Settings application, but there are only 5 or so things you can edit with that little app. I was hoping for a method with a bit more flexibility. 

Also, as a side question, I've heard that Unity 2D is specifically designed NOT to use Compiz, so things like cube desktop and wobbly windows will never be available in this 2D desktop environment. Can someone please confirm this for me? (Sadface for losing out on the eye candy I used to have in 10.10 :()

Thanks in advance for your help!

---

### Post by Krytarik on 2011-04-30
There are not too much options to customized Unity as of now, even less for Unity 2D, as you noticed. So, no shrink feature, but in usual Unity the background of the launcher can be set to transparent, so that would be nearly the effect you want.

And yes, no eye candy for Unity 2D, otherwise it would of course miss its purpose.

Did you fully test if you can really not run usual Unity?

If not, try logging in to "Ubuntu" (thus Unity), creating a launcher at the desktop for the command "compiz --replace", and launching it. Make sure before to have Ctrl+Alt+Backspace enabled, to be able to kill the xserver if it doesn't work.

---

### Post by Entyrion on 2011-05-03
Just as a follow up to this thread for the benefit of anyone else who might come across it in the future:

1. Creating the launcher for "compiz --replace" DOES re-enable Compiz within Unity 2D, but it does not activate the 3D version. So while I'm stuck with Unity 2D, I AM able to use Compiz to restore a lot of the eye candy functionality like wobbly windows, cube desktop, and window animations, so thanks for the tip Krytarik :)

2. Like I said, I am in fact running Unity 2D, so the Unity Plugin menu for Unity 3D in CompizConfig Settings Manager will NOT work. However, after running the launcher above, I CAN use CCSM to modify non-unity Compiz settings to restore most of the eye candy I wanted... Unity 2D is NOT incompatible with Compiz.

3. While I was not able to specifically change the launcher settings to create the effect I originally mentioned in this post, I WAS able to modify a surprising amount of Unity 2D effects that I had otherwise been led to believe were incompatible with Unity 2D (including the transparency feature Krytarik mentioned). 

It took a little work, but in the end, here are the features I was able to modify in my Unity 2D setup. 

-Transparent Menus
-Wobbly Windows
-"Dodge" focus window animation
-Open/close/min/max windows animations
-Unity 2D transparency effects (change the opacity for the Unity launcher, panel, and places menus)
(This can all be done in the standard CCSM interface. See [http://ubuntuforums.org/showthread.php?t=1746381](http://ubuntuforums.org/showthread.php?t=1746381) for how I was able to modify the opacity for UI elements in Unity 2D.)

-Cube desktop
([http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/](http://www.omgubuntu.co.uk/2011/04/compiz-cube-natty/))

-Toggle the Unity launcher to auto-hide
([http://ubuntuforums.org/showthread.php?t=1747367](http://ubuntuforums.org/showthread.php?t=1747367) and using the tool at [http://www.ubuntugeek.com/a-simple-gui-for-unity-2d-settings-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/a-simple-gui-for-unity-2d-settings-on-ubuntu-11-04-natty.html))

-Remove the "workspaces" icon from the launcher
([http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html) note that there are also a bunch of other things you can tweak like icon size and whatnot on this page too.)

For anyone else struggling to customize your Unity 2D interface, don't let anyone tell you that there are no customization options for Unity 2D, it just takes a bit of effort. With the resources above, I was able to replicate virtually all the functionality and eye candy of the official Unity 3D interface in Unity 2D! I'm a noob and I was able to figure it out (although I had to learn CCSM and gconf-editor, etc as I went), so you can too!

---

### Post by GavinZac on 2011-05-03
I'm confused. If your computer can handle all the, well, useless eyecandy like Cube and Wobbly windows, why can't it handle the Unity 3D shell?

I'm using Unity 2D but only because I'm on a fairly old laptop that splutters when it hits a HD youtube video!

---

### Post by Entyrion on 2011-05-03
@GavinZac: Very good question! I most certainly don't know!

All I do know is that when I booted 11.04 in the Unity session for the first time, it notified me that my hardware was insufficient and sent me back to the old Gnome interface. 

When I run ```
/usr/lib/nux/unity_support_test -p
``` I get the output ```
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

So, apparently no Unity 3D for me. Why can it run Compiz and not the fancy-pants Unity? Dunno, I didn't build either of them, nor do I have the experience or technical knowledge to tell you why =P I just wanted to have the same effects I had in 10.10 so I found a bunch of workarounds :)

---

### Post by karmila on 2011-05-03
@[Entyrion]("http://ubuntuforums.org/member.php?u=1276433"): If unity-2d is not a compiz plugin, so how could it can be set up through ccsm? Do you have unity plugin enabled on ccsm?
Also, is there a way to resize unity-2d launcher size? Default size is too big.

---

### Post by GavinZac on 2011-05-03
> **karmila said:**
> @[Entyrion]("http://ubuntuforums.org/member.php?u=1276433")
Also, is there a way to resize unity-2d launcher size? Default size is to big.

Not yet; unity-2d is not really a finished product yet. A month or so ago it wouldn't even run most of the time for me.

---

### Post by GavinZac on 2011-05-03
> **Entyrion said:**
> @GavinZac: Very good question! I most certainly don't know!

All I do know is that when I booted 11.04 in the Unity session for the first time, it notified me that my hardware was insufficient and sent me back to the old Gnome interface. 

So, apparently no Unity 3D for me. Why can it run Compiz and not the fancy-pants Unity? Dunno, I didn't build either of them, nor do I have the experience or technical knowledge to tell you why =P I just wanted to have the same effects I had in 10.10 so I found a bunch of workarounds :)

Very odd. Perhaps it's because of the kind of obscure 3D card, Unity might not have recognised it despite it being able to run it. I would submit a bug! Because I think the error might be in detection rather than an actual problem with your PC.

First, you could try booting into it again. Surely Ubuntu didn't _force_ you to use Classic? Despite my netbook not being able for 3D at all (it's a struggle to keep Firefox and Netbeans stable while running at the same time), it did boot into Unity at the start.

---

### Post by Entyrion on 2011-05-03
> **karmila said:**
> @[Entyrion]("http://ubuntuforums.org/member.php?u=1276433"): If unity-2d is not a compiz plugin, so how could it can be set up through ccsm? Do you have unity plugin enabled on ccsm?
Also, is there a way to resize unity-2d launcher size? Default size is too big.

1. CCSM is used to modify all the non-Unity stuff like wobbly windows, animation effects, and cube desktop. CCSM is not able to directly modify any of the values for Unity 2D. Yes, the Unity Plugin is activated in CCSM, but it is non-functional; changing settings in the Unity Plugin menu does nothing whatsoever. The only setting you can change for Unity 2D via CCSM is the opacity of the panel, launcher, and places menus, and even this cannot be done via the Unity Plugin - you need to use the "Opacity, Brightness, and Saturation" menu. (See my thread on how I learned to do this at [http://ubuntuforums.org/showthread.php?t=1746381](http://ubuntuforums.org/showthread.php?t=1746381))

2. There appears to be a (complicated) way to resize the launcher and the launcher icons, though I haven't tried it myself, at [http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html) Might be worth a look if you're REALLY interested in resizing it. Otherwise, no, I have not found any other way to modify it (and I've been looking around quite a bit)!



> **GavinZac said:**
> First, you could try booting into it again. Surely Ubuntu didn't _force_ you to use Classic? Despite my netbook not being able for 3D at all (it's a struggle to keep Firefox and Netbeans stable while running at the same time), it did boot into Unity at the start.

After I installed 11.04 originally and tried to boot into the default Ubuntu (therefore Unity 3D) session, I got an ugly gray pop-up that said something to the effect of "This computer does not have sufficient hardware to operate Unity" and when you click OK, it brought up the standard Gnome2 interface. After I installed Unity 2D, then that became the default fallback every time I booted into the default session since.

I am not aware of any way to try to force Unity 3D to run; running "compiz --replace" reloads compiz, which works perfectly with the exception of the Unity Plugin. When I toggle that box on and off, by windows borders and ui is generally messed up, but nothing like Unity boots up =\

---

### Post by Entyrion on 2011-05-03
> **GavinZac said:**
> Very odd. Perhaps it's because of the kind of obscure 3D card, Unity might not have recognised it despite it being able to run it. I would submit a bug! Because I think the error might be in detection rather than an actual problem with your PC.

Hmm, well Unity 3D requires OpenGL of 1.4+ and I currently only have 1.3. Maybe I should look into trying to update my video card driver in Ubunut? (I thought that was supposed to happen automatically... not quite sure where to begin.)

---

### Post by Entyrion on 2011-05-03
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758747](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/758747)

I recently found this. Apparently the bug has been marked as "invalid" because my video card does not support OpenGL 1.4 or higher. Good thing I found those workarounds!

---

### Post by Krytarik on 2011-05-04
Entyrion, thanks for the detailed guide and the link to ubuntu-root's guide, bookmarked both of them!

Since I noticed in the screenshot of your respective thread that Compiz' "Opacity, Brightness and Saturation" plugin is affecting your entire launcher, including the buttons, -as expected-, how about setting just the launcher background transparent, completely, by following ubuntu-root's guide and setting a completely transparent image as the background image!? :)

---

### Post by karmila on 2011-05-04
> **GavinZac said:**
> Not yet; unity-2d is not really a finished product yet. A month or so ago it wouldn't even run most of the time for me.

Thanks, so developer now have 6 months to make unity-2d a solid fall back for OO :D

> **Entyrion said:**
> 1. CCSM is used to modify all the non-Unity stuff like wobbly windows, animation effects, and cube desktop. CCSM is not able to directly modify any of the values for Unity 2D. Yes, the Unity Plugin is activated in CCSM, but it is non-functional; changing settings in the Unity Plugin menu does nothing whatsoever. The only setting you can change for Unity 2D via CCSM is the opacity of the panel, launcher, and places menus, and even this cannot be done via the Unity Plugin - you need to use the "Opacity, Brightness, and Saturation" menu. (See my thread on how I learned to do this at [http://ubuntuforums.org/showthread.php?t=1746381](http://ubuntuforums.org/showthread.php?t=1746381))

2. There appears to be a (complicated) way to resize the launcher and the launcher icons, though I haven't tried it myself, at [http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html) Might be worth a look if you're REALLY interested in resizing it. Otherwise, no, I have not found any other way to modify it (and I've been looking around quite a bit)!

Actually, I have unity-capable graphic. I installed unity-2d to see if I can use unity with a little less source. Now, that i know if unity-2d is not completed yet i will go back to unity-3d.

But, I like your tweak to change launcher transparency. Maybe i can use it on unity-3d.

---

### Post by Entyrion on 2011-05-04
> **Krytarik said:**
> Entyrion, thanks for the detailed guide and the link to ubuntu-root's guide, bookmarked both of them!

Since I noticed in the screenshot of your respective thread that Compiz' "Opacity, Brightness and Saturation" plugin is affecting your entire launcher, including the buttons, -as expected-, how about setting just the launcher background transparent, completely, by following ubuntu-root's guide and setting a completely transparent image as the background image!? :)

That's a brilliant idea, thanks!! I'll try it out asap (might be busy over the next day or so) but I'll keep you posted on what I find out! Thanks again! :) 


> **karmila said:**
> Actually, I have unity-capable graphic. I installed unity-2d to see if I can use unity with a little less source. Now, that i know if unity-2d is not completed yet i will go back to unity-3d.

But, I like your tweak to change launcher transparency. Maybe i can use it on unity-3d.

Well, I recently made my first How To guide ever to walk through  this combination of Unity 2D + Compiz effects, so I'm just waiting for the moderator people on the Tutorial forums to approve it. I'll post the link here once its up and you can take a look and see if there's anything there you want to try (and let me know what you think) =D

---

### Post by Entyrion on 2011-05-04
Well, I was excited enough about Krytarik's suggestion that I tried it out right away last night. Unfortunately, when I tried to replace the default background image with a transparent one, I received an error message to the effect of "you can't use transparent images" and when I rebooted to check the effect, the background was white rather than transparent, so no dice :(

However, I did discover a couple things that might be worth mentioning.

1. The "Launcher background" instructions at [http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html](http://www.ubunturoot.com/2011/02/remove-and-rearrange-items-in-unity-2d.html) appear to be incorrect. While the process itself is basically valid, it looks like the author got his file locations messed up.

From my testing, editing the image "/usr/share/unity/themes/launcher_background_middle.png" had NO effect on the Unity 2D background. The correct image you need to edit is located at "/usr/share/unity-2d/launcher/artwork/background.png"

2. For fun, I came up with a cheater way to work around this and simulate complete transparency which is surprisingly simple: just take a screenshot of your blank desktop when the launcher is auto-hidden, then crop it down to 66 pixels wide (those 66 pixels should the the far left strip of the screen that is covered by the launcher btw), trim off the very top of that 66px strip (where you can see the Ubuntu logo and part of the top panel), and use that image in place of /usr/shared/unity-2d/launcher/artwork/background.png. Make sure you back up the original of course :) When this is done, the launcher background will *appear* to be fully transparent and the launcher icons will be floating on their own directly over the left side of the desktop!

Now, obviously this is not true transparency. It looks neat on a perfectly blank desktop, but as soon as windows are opened and the launcher overlaps them, the illusion is broken and it looks pretty ghetto. Furthermore, in my visual opinion, then you use the Super button to open the places window and launcher at the same time, the sharp black line on the left-hand side of the places window is an eyesore.

In the end, I reverted back to what I had before and I chose not to use my poor man's transparency. But it was fun to figure out, so I though I'd mention it.

And thanks again to everyone on this forum for their input! I'll be sure to post a link here when my howto guide is up :)

---

### Post by Bucic on 2011-05-08
> **karmila said:**
> Now, that i know if unity-2d is not completed yet i will go back to unity-3d.
Is it "not completed" in a way that it will cause artifacs, teared UI elements/windows and/or crashes more frequently than unity 3D? The answer is important to me as I'm currently struggling with my graphics driver 
[http://ubuntuforums.org/showthread.php?t=1748187&page=2](http://ubuntuforums.org/showthread.php?t=1748187&page=2)

---

### Post by Entyrion on 2011-05-08
> **Bucic said:**
> Is it "not completed" in a way that it will cause artifacs, teared UI elements/windows and/or crashes more frequently than unity 3D? The answer is important to me as I'm currently struggling with my graphics driver 
[http://ubuntuforums.org/showthread.php?t=1748187&page=2](http://ubuntuforums.org/showthread.php?t=1748187&page=2)

I'm using Unity 2D as my primary UI and I don't have any such problems. It runs smoothly, no artifacts or anything of the sort. I do get some slight screen tearing, but ONLY when I enable Compiz effects like cube desktop and wobbly windows and move them around really fast. This is due to my old laptop's video card more than Unity 2D though.

If you run Unity 2D WITHOUT Compiz in its standard mode, it is extremely smooth and works like a charm in my experience; only when you use Compiz to try tweaking things does it even slightly start to act up (and that's more of a problem with my comp+compiz than Unity 2D).

---

### Post by Bucic on 2011-05-08
Thanks, Entyrion! I'll just make sure compiz is dead on my system. ;)

---

### Post by Entyrion on 2011-05-09
I hope it works out Bucic!

----------------------------------

Also, I mentioned earlier in this thread that I was working on posting my first how to guide for using Compiz to get Unity 2D to replicate the appearance of the 3D version. My guide is posted at [http://ubuntuforums.org/showthread.php?p=10765568#post10765568](http://ubuntuforums.org/showthread.php?p=10765568#post10765568) let me know what you guys think!

---

### Post by abh83 on 2011-06-24
Some Nvidia cards have been blacklisted in Ubuntu such as the Geforce Go 7000 series:

[http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

I was having the same problem and when I enabled Unity 3D it would crash the system upon logging in.

Unity 2D is working fine though.

---

### Post by abh83 on 2011-06-25
btw. I don't know if this thread is still relevant or not, but I managed to get Unity 3D working just fine with my blacklisted Nvidia GeForce Go 7300 by installing the Nvidia Accelerated Graphics Drivers 173 and following the instructions at the following link to force start Unity 3D: [http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

Also not that Unity 2D needs to be uninstalled first.

---

### Post by celiapgt on 2011-07-28
> **GavinZac said:**
> I'm confused. If your computer can handle all the, well, useless eyecandy like Cube and Wobbly windows, why can't it handle the Unity 3D shell?

I'm using Unity 2D but only because I'm on a fairly old laptop that splutters when it hits a HD youtube video!

I thank you, GavinZac! [Just because I love people from Ireland]

---


---
title: "Gutsy + NVIDIA 7100GS + Dual Display + Compiz + Xinerama/TwinView"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by heizenberg on 2008-02-02
I just setup a new Gutsy box with an Intel Core 2 duo processor, Asus Mobo and a PCIe NVIDIA 7100GS card. While installing Ubuntu, I just had a single monitor (NEC MultiSync 2070NX) hooked up via a KVM switch to the analog o/p of the 7100GS (analog because I don't have a DVI KVM)

Thanks to these forums, it was quite easy to figure out how to enable compiz and get all the full effects by enabling the restricted drivers.

The trouble started when my second monitor arrived - NEC MultiSync 2070VX - looks identical, has the same resolution, but not the same exact model as my other monitor. (2070**N**X v/s 2070**N**X). I hooked it up to the DVI, opened up my ubuntu display settings and enabled
it at the same resolution (1600x1200). It worked but I noticed that my AWN disappeard. It took me a short while to realize that Compiz stopped working as well. Checking the 'Use desktop effects'
reported that Desktop effects couldn't be enabled. Weird! Another bizzare thing was that my first monitor (still reporting 1600x1200) was a larger virtual window... i.e. the display would pan both 
left-right and top-bottom when I moved the mouse around. The second display stayed the right size.

At this point, I decided to try using Envy. I uninstalled the restricted driver, installed Envy and installed the 169.09 nvidia driver. After rebooting/restarting X a couple of times here, there
was no change at all! The settings still reported both monitors at 1600x1200 but I still had a larger pannable virtual desktop on the first monitor. I tried changing refresh rates, as a few people on this forum mentioned, but had no luck.

While playing around further with nvidia-settings I noticed both monitors had Absolute positioning; so I changed the second monitor to be relative to the first. Restarting X now brought the size on the first monitor - no more edge panning.

At this point I had both monitors at the right resolution, but still no desktop effects that could be enabled. On a whim, I switched off Xinerama (and perhaps something else I can't remember right now) and I now had two independent desktops... both with their own copies of the taskbar at the top. Oddly, I could enable desktop effects independently on each monitor! But having two taskbars independent of each other, was oddly disconcerting. So I switched on Xinerama in nvidia-settings... and again couldn't enable desktop effects!

Xinerama on = Desktop effects off!

Looking around some more on this forums, I changed the nvidia-settings config to use TwinView instead of Xinerama. That was the last change and now I have desktop settings enabled with compiz and awn working, with a single task bar at the top on my primary monitor. An annoyance is 
that AWN shows up in the middle of my second monitor and I can't find a way to move it back to the primary monitor. I can live with this though. Another minor point is that desktop cube rotation
shows two cubes - one in each monitor, but the viewports on the screens are synched... i.e. rotating one cube, causes the other one to rotate as well... I do admit that it would have been nice to have a single cube show (as I'm guessing it would had Xinerama and desktop effects worked together).

Net conclusion is that using Xinerama, causes my desktop effects to be disabled and using Twinview allows DT effects to be enabled... albeit with the annoyance of AWN being in the wrong window.

It's not a deal breaker for me, but having one wide cube with Xinerama would be nicer than having two synchronized cubes... as well as having AWN on the primary monitor.

Any thoughts/ideas?

Thanks,
H

---

### Post by rune0077 on 2008-02-02
Xinemara won't work with Compiz, not even with the latest Nvidia drivers (they even admit this much). I got AWN on the right window, though, using TwinView - it's always been that way, so I'm not sure why you don't, but try fiddling around 'coz it's doable. 

You can have one big cube with TwinView if you want: just open up CCSM (install it if you don't have it), go to Desktop Cube and set Multi Output Mode to "One big cube".

---

### Post by heizenberg on 2008-02-05
Thanks! I enabled a single wide cube. Easier to wrap my brain around that than two synchronized cubes.

---

### Post by ergosteur on 2008-02-12
Hello,
I've got the same issues as described in the first post. I tried the same solutions, enabling xinerama and losing compiz, installing NVIDIA drivers with envy. But in my case, my primary LCD is 19" and my secondary LCD is 15". Using TwinView however, some objects appear off screen, as if Ubuntu thinks I have two 19" panels.

---

### Post by rune0077 on 2008-02-12
> **ergosteur said:**
> Hello,
I've got the same issues as described in the first post. I tried the same solutions, enabling xinerama and losing compiz, installing NVIDIA drivers with envy. But in my case, my primary LCD is 19" and my secondary LCD is 15". Using TwinView however, some objects appear off screen, as if Ubuntu thinks I have two 19" panels.

Yeah, that's because TwinView creates a Virtual Desktop (meaning that it pretends that your two screens are just one big area). The Virtual Desktop resolution will be set to (width of ScreenA + width of ScreenB)X(highest height).

Sorry if that didn't make much sense, not sure how to describe it. But try setting your screens at the same resolution, or as close to it as you can get (the important thing is that they have the same height).

---

### Post by Ck.asdf on 2008-02-15
> **rune0077 said:**
> Yeah, that's because TwinView creates a Virtual Desktop (meaning that it pretends that your two screens are just one big area). The Virtual Desktop resolution will be set to (width of ScreenA + width of ScreenB)X(highest height).

Sorry if that didn't make much sense, not sure how to describe it. But try setting your screens at the same resolution, or as close to it as you can get (the important thing is that they have the same height).

Hello, I tried setting mine to twin view, but that option is not selectable.  I can either choose "disabled" or "separate X screen."  Twin view's circle is gray, and non-clickable.

I tried turning off Xinerama and then restarting X, and then trying twin view, but no luck.

Suggestions? I have a couple monitors that I'd love to get some compiz stuff goin' on.

---

### Post by rune0077 on 2008-02-15
> **Ck.asdf said:**
> Hello, I tried setting mine to twin view, but that option is not selectable.  I can either choose "disabled" or "separate X screen."  Twin view's circle is gray, and non-clickable.

I tried turning off Xinerama and then restarting X, and then trying twin view, but no luck.

Suggestions? I have a couple monitors that I'd love to get some compiz stuff goin' on.

I have no idea why TwinView shouldn't be enabled, if both your screens are detected correctly. Are you using the latest drivers from Nvidia, or the ones from Restricted Manager? (if the later, it may help to update to the newest version).

---

### Post by Ck.asdf on 2008-02-15
I believe it's the nVidia drivers ... whenever I boot my computer it shows the full-screen "nVidia" logo.
it was a while back that I got the drivers working ... where can I look to check for sure which drivers I installed?

---

### Post by rune0077 on 2008-02-15
> **Ck.asdf said:**
> I believe it's the nVidia drivers ... whenever I boot my computer it shows the full-screen "nVidia" logo.
it was a while back that I got the drivers working ... where can I look to check for sure which drivers I installed?

If you're using Gnome, then check under Application > System Tools. Do you have Nvidia settings there? If yes, then open it and you can see what driver version you're using. The latest is 169.09. 

If you don't have Nvidia settings, then you probably installed the driver through Synaptic, in which case you have an old version and should install the newest instead (get it from Nvidia's homepage).

---

### Post by sclewis12 on 2008-03-21
I also have a similar problem as the original poster.
I have 2 samsung 17's on ubuntu 7.10. I have an nvidia 7800gt with the latest drivers installed.

The twinview I got to work fine. At first the  primary panel had the pan issue as described. I solved this by using the default display config rather than having it set to the samsung model in the data base.

The second issue is that compiz works fine when twinview is disabled. Then when I enable it. Compiz stops running and will allow it's self to be turned back on.

third
I can't use the nvidia console to write to x and make changes, because I believe that the Ubuntu screens and graphics applet takes authority over x. This is fine as long as I can get the screens to display.

My last question is pretty noobish, but i am fairly new to linux. When you look in the folder and see xorgconfig files named 1-6. Is the current one the one that would be considered?  As in the one without a number given.?

---

### Post by ergosteur on 2008-04-19
I updated to the latest nVidia drivers using Envy. Then I rebooted, switched to TwinView mode and restarted X. Finally, I enabled 'Desktop Effects' using the Ubuntu appearance prefs. It prompted me to enable the nVidia restricted driver (even though it already said 'in use', the box wasn't checked). I rebooted and compiz works great. I can even wobble video windows across the two screens!

---

### Post by khughitt on 2008-06-13
> **heizenberg said:**
> ...AWN shows up in the middle of my second monitor and I can't find a way to move it back to the primary monitor....

I have the same problem. Anyone have any luck selecting the desktop where AWN is placed?

---

### Post by khughitt on 2008-06-16
For AWN's settings in gconf-editor there is an "xoffset" value which is supposed to let you move the dock to the left or right some, however, even when "force monitor" is checked, it is not having any affect on my machine :\

---


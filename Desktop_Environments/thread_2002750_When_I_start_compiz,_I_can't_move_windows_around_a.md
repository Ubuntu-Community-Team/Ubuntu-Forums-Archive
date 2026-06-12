---
title: "When I start compiz, I can't move windows around anymore."
date: 2012-06-13
forum: Desktop Environments
---

### Post by wilsonsamm on 2012-06-13
Since upgrading from 10.04 to 12.04 I found I didn't much like the new GUI, so I switched to Xfce4. I ran apt-get install xubuntu-desktop and am now running Xfce. But I liked some of the features the old Gnome had, like being able to zoom in on something, so now I'm playing with getting Compiz to fill that gap. I'll type into a terminal the following, and get the following warnings:
```
$ compiz --replace ccp &
[1] 1838
<the bash promt>$ Backend     : ini
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing cube options...done
Initializing mousepoll options...done
Initializing gnomecompat options...done
Initializing ezoom options...done
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks

Setting Update "texture_compression"
Setting Update "command"
Setting Update "mipmap"
Setting Update "zoom_in_key"
Setting Update "zoom_out_key"
Setting Update "scale_mouse_static"
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: failed to bind pixmap to texture
compiz (decor) - Warn: No default decoration found, placement will not be correct
Window manager warning: Failed to load theme "Clearlooks": Failed to find a valid file for theme Clearlooks

compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


```

You can see some warnings about window placement going to be wrong. I don't understand precisely what's going on though, and why I can't move any windows around after I start compiz. Can anyone help me solve this?

---

### Post by 3Miro on 2012-06-13
Have you enabled the plugin for moving windows, I think the base compiz has pretty much all plugins disabled. Install CCSM and check to see if it is enbled.

---

### Post by LewisTM on 2012-06-13
Make sure compiz-gnome is installed.
Then in ccsm (CompizConfig Settings Manager) enable Window Decoration along with Window Move, Place, Resize and Composite.
In Window Decoration settings, use this command:
```
gtk-window-decorator --replace
```
That should fix everything.

Cheers!

---

### Post by wilsonsamm on 2012-06-14
Fantastic! It works well. I thought that would already have been enabled in the config, but ...

One thing more is that the desktop cube (that rolls right and left) seems "separate" from the window buttons and the desktop switcher on the Xfce panel. The window buttons show windows from all desktops, and if I switch to a different desktop using the desktop switcher on the panel instead of the compiz shortcut, then I end up with an unresponsive screen that's identical to the login screen. Compiz is still running, and makes the visual effect of rolling the cube to the left or right, but it still leaves me with that screen.

I hope this description is understandable!! And does anyone know how to fix that?

---

### Post by LewisTM on 2012-06-14
I *think* I know what's the problem.

It stems from the different conceptions of what a desktop is according to Compiz vs other window managers.

Compiz treats each cube face a different **viewport**. It can have multiple desktops each with it's own set of viewports. This is effect makes you desktop 4D! You can easily get lost in the fourth dimension, where there are no panels or icons.
The solution is to go to CCSM/General/Desktop size and set the Horizontal Virtual Size to 4 (= 4 viewports), 1 Vertical and _1 Desktop_. The Xfce Workspace switcher will then switch between the viewports. An ill effect it that the switcher won't be able to move windows between workspaces since it doesn't know how to handle viewports. Use Compiz Expo for that.

Hope this helps! :)

---

### Post by wilsonsamm on 2012-06-15
Ah thank you, Lewis! That's brilliant. I followed your instructions and everything is working as expected now.

That is, except for a one little artefact. When I switch from one desktop to another, whichever desktop I was on flashes up briefly. If I switch from desktop 1 to desktop 2, then the animation shows the transition to desktop 2, desktop 1 flashes up for a fraction of a second, then the screen shows desktop 2 as normal. What causes this? Is it a bug?

I'll mark the thread as solved though, because this is aesthetic and not a functional problem.

---

### Post by LewisTM on 2012-06-15
The cube flickering problem is a well-know, shameless bug. If you can't stand it you can do like me and switch to the Desktop Wall which doesn't flicker.
The [bug tracking system]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/862430") has marked it as "Fix released".
I'll try their fix and report back.

Cheers!

---

### Post by LewisTM on 2012-06-15
FIXED!
I have been waiting so long for that, this just made my day.
```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
sudo apt-get update
sudo apt-get upgrade
```
And logout/login

---

### Post by LewisTM on 2012-06-15
... or not.
As seems to be the tradition with Compiz, every time they fix a bug another one appears. Reminds me of Whac-A-Mole.
This time I get white menus and random freezes. 
Use at your own risk.

---

### Post by wilsonsamm on 2012-06-15
Yep. On my system, compiz stopped loading completely when I did that. What is the way to revert the system to however it was before I made that change?

---

### Post by LewisTM on 2012-06-15
```
sudo ppa-purge ppa:vanvugt/compiz-preproposed
```

---

### Post by DGINSD on 2012-06-17
> **LewisTM said:**
> FIXED!
I have been waiting so long for that, this just made my day.
```
sudo add-apt-repository ppa:vanvugt/compiz-preproposed
sudo apt-get update
sudo apt-get upgrade
```
And logout/login

You have no idea how excited this post made me, Oh to finally go back to the cube...

---

### Post by DGINSD on 2012-06-17
> **LewisTM said:**
> ... or not.
As seems to be the tradition with Compiz, every time they fix a bug another one appears. Reminds me of Whac-A-Mole.
This time I get white menus and random freezes. 
Use at your own risk.

Or not.....

I found the whack-a-mole especially amusing (It's funny cause its true):confused:

---

### Post by luisfmp on 2013-03-27
Thanks LewisTM for all the instructions, I now have Compiz working in my Ubuntu Studio 12.10

---

### Post by pgradone on 2013-11-03
> **LewisTM said:**
> Make sure compiz-gnome is installed.
Then in ccsm (CompizConfig Settings Manager) enable Window Decoration along with Window Move, Place, Resize and Composite.
In Window Decoration settings, use this command:
```
gtk-window-decorator --replace
```
That should fix everything.

Cheers!

OK!
Fiddling with Window Decoration didn't give me back moving window abilities :( .... but:
In CCSM, "Move Window" plugin is in section "Window Management", while "Window Decoration" plugin is in section "Effects"! :)

Hoorray, one step closer to "the perfect desktop" - thanks villmools :5

---


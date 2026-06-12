---
title: "Feisty Desktop Effect causes Panel to vanish"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by regal_dunce on 2007-04-27
Not a huge problem here, but I think it's worth posting.  Whenever I enable desktop effects in feisty, everything seems to work fine.  However, when I reboot, I only have a gnome-panel on my first workspace.  Restarting nautilus and gnome-panel don't help, but if I go to system -> Preferences -> Desktop Effects and turn the desktop effects off and then on again, then I have panels in all four workspaces.

Any one else have this same problem?

---

### Post by sebbouckaert on 2007-04-27
Yes, more or less the same over here. I can use some of the desktop effects but not the cube rotation effect. When I enable this my workspaces get reduced from 2 (or more) to 1 workspace and then my bottom panel disappears. After disabling the cube effect and logging off and on again everything is OK again. Not a major issue for me, but indeed perhaps worth mentioning 
I have HP pavilion desktop PC with NVIDIA Geforce 7000 series card, and I did install the nvidia-glx-new driver which seems to be version 1.0.9755. There is a more recent driver available on the nvidia site but that needs to be installed without the x server running and I haven't figured out yet how to do this on this version of Ubuntu.

Question is whether updating the driver would solve the issue with the rotation effect.

---

### Post by szf on 2007-04-27
> **regal_dunce said:**
> I only have a gnome-panel on my first workspace.
Aye, sometimes the lower panel doesn't load, sometimes the switch desktop goes to an empty space, occupied solely by my wallpaper. An alt+tab returns me to my previous (usable) workspace.

I'd do without "Desktop Effects" but they seem to have a strong impact on the quality of my font display. I've allowed a Feisty update to Gnome-panel on 4/24/07, but it seems to be the same or worse.

---

### Post by stevieb on 2007-04-28
I have problems also- Lenovo 3000 C100.  calling up Desktop effects reduces my 4 workspaces to one, my single panel begins to flicker, then disappears- sometimes accompanied by a "removing panel" message.

-steve

---

### Post by dannemil on 2007-05-01
I posted on this some time ago with no answer so far. I have the same problem. Switching to workspaces 2,3 or 4 leaves me with nothing but blank wallpaper. Some times alt-Tab will get me back tp WS1, but some times not. Unfortunately, this makes that feature completely useless because some times I have to do a hard reboot - not even a keyboard logout will get me out of the dead workspace.

Pretty serious problem - it worked fine on previous versions - Dapper, Edgy - not here.

---

### Post by blamecanada on 2007-05-01
Sometimes on my laptop the panel won't load when I turn it on (Beryl starts too). If you run gnome-system-monitor and end the process gnome-panel it always pops back up. Annoying, but it works after that little trick for me.

---

### Post by SyL on 2007-05-03
Another thread about this issue and with a workaround provided: [http://ubuntuforums.org/showthread.php?t=429231&highlight=desktop+effect](http://ubuntuforums.org/showthread.php?t=429231&highlight=desktop+effect)

>  EDIT:
Have been searching the bugs and it has been reported. The workaround that got it working for me again is to issue the following commands (one at a time) in the terminal
Code:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4

Code:

 gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

The reported related bugs I found were #82957 and #89786

I hope the workaround will also work for you  

---

### Post by Radioactive_Ape on 2007-05-04
That fixed that problem for me but, When the effects are turned on I can't type. Anyone else having that problem?

---

### Post by mshamma on 2007-05-05
The fix posted earlier worked for me too. But sometimes I am not able to close some windows.

To be more specific it seems that clicking events on the title bar and the buttons at the same level (minimize, maximize/restore, close) are not handled.

For example I cant close or move the pop up find window in the acrobat reader.

Anybody have the same problem?

---

### Post by JonDubya on 2007-05-12
> **Radioactive_Ape said:**
> That fixed that problem for me but, When the effects are turned on I can't type. Anyone else having that problem?

Yeah, me too. It's stupid annoying.  Is there a way to revert the settings back to default? ...meaning, what were the original settings?  I'd rather just kill gnome-panel and deal with having no panel bars than put up with this annoying "can't-type" "solution."

---

### Post by armalite on 2007-05-16
I still have this problem in Ubuntu Feisty i386. I have nvidia video card. I tried a fresh install of a Feisty amd64 on the same pc, and there is no such issue there (but i had tested it only for a little so i'm not so sure).

The workaround written above doesn't work for me, it takes out my workspaces and I have to re-add them. Please note, I'm NOT using cube effect and i do not want to. I'm using plain old workspaces.

As a workaround i bounded ctrl+f1 to ctrl+f4 to the 4 workspaces, so in case something doesn't work i can safely return to the good workspace. Disabling and reenabling desktop effects correct the issue, until the next reboot.

---

### Post by th3rmite on 2007-05-16
I didn't read the work around post, but I do have a very easy answer. See the gnome panel and the compiz panel are completely different apps not compatible with each other. Anyways here is the package you need:

```
sudo apt-get install gnome-compiz-manager
```

The app can be found under "System::Preferences::GL Desktop"

The settings you need are under the "Workspaces" tab.

I hope this helps.

---

### Post by armalite on 2007-05-18
I installed gnome-compiz-manager long ago, but it didn't solved this problem. 
The problem isn't the cube, the problem is that gnome panel and nautilus icons (all the icons on the desktop) disappear when switching workspaces. Only on the 1st workspace seems having all the things. Instead the other 3 workspaces haven't the panel and/or haven't the desktop icons. These 3 workspaces have the same behaviour.

This is quite annoying, i have to disable and reenable desktop effects in order to make panel & icons reappear in every workspace.


EDIT: 
> **th3rmite said:**
> See the gnome panel and the compiz panel are completely different apps not compatible with each other. 

Are you meaning "gnome workspace switcher" (i translated from italian so i don't know the correct english name)? If so, I still prefer gnome panel over compiz panel since it shows the windows in workspaces way better the compiz panel.

---

### Post by realvz on 2007-05-21
i have kindof same problem here with my hp dv2000 and nvidia 7200

when i enable desktop effects, panels on my TV out xserver disappear..its completely stuck..

i hope the masters of linux fix this quickely..because desktop effects is so cool and its a pain not being able to use them

---

### Post by sebbouckaert on 2007-05-22
Just wanted to say that since I' ve upgraded to the latest Nvidia driver, everything works fine!

In my case I installed driver Nvidia-Linux-x86-1.0-9755-pkg1.run. which is a more recent version than the ones in the repositories

I used method 2 as described in this howto: 

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

After the upgrade I encountered another small problem: my window manager wouldn't work anymore, so no window borders whith the GLdesktop effects enabled. Also described in this thread: 

[http://ubuntuforums.org/showthread.php?t=437404&highlight=compiz+window+manager](http://ubuntuforums.org/showthread.php?t=437404&highlight=compiz+window+manager)

So I edited /etx/X11/xorg.conf and added these lines in the 'screen' section



Option "AddARGBGLXVisuals" "True"
DefaultDepth 24

I am happy to say that all the visual effects are now working smoothly without panels disapearing or other strange issues!

EDIT: forgot to say that my graphics card is a GeForce 7300 LE

---


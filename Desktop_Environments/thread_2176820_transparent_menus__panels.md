---
title: "transparent menus / panels"
date: 2013-09-26
forum: Desktop Environments
---

### Post by timo2 on 2013-09-26
Hey all,

I'm trying for 3 hours to set my upper panel to a transparent design.
With Ubuntu itself I can only set the panel to transparent, the menu buttons
are still grey (Applications, Sound, Bluetooth, WLan etc.)

I already searched with google for a solution and I found a application
called 'CompizConfig' and tried to use it but as much as I try there is no
change at the design.

Do you have any idea what's wrong? It should be possible to set the menu to a transparent
design, or not? Which apps are needed for it?

Friendly regards
Timo

---

### Post by grahammechanical on 2013-09-26
As far as I know the colour of the app indicators in top panel are a function of the theme. That also applies to the background colour of the app indicator menus. For example, If we use the Radiance theme then the colour of the app indicator icons and the characters on their menus have a dark look. Whereas, if we use the Ambience theme (default) the app indicators and the characters on the menus have a light look.

Regards.

---

### Post by timo2 on 2013-09-27
Hey,

After... I think 5 hours of searching I got Compiz working, after logging off, 
Compiz stopped working again.

At first I used this command:
compiz --replace

And then this one:
gtk-window-decorator --replace

Do you know why Compiz is not starting - Or why my compiz settings
does not have any effect without using this commands?

//edit:
After using compiz --replace I get this errors:
> 
Setting Update "opacity_step"
Setting Update "opacity_matches"
Setting Update "opacity_values"
Starting gtk-window-decorator
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct


I only changed some settings in the opacity options.

- Timo

---

### Post by stinkeye on 2013-09-27
What ubuntu release are you running?
What desktop are you logging into?

This terminal command will show your current logged in session...
```
echo $DESKTOP_SESSION
```

---

### Post by timo2 on 2013-09-28
Hey,

I got this info:
> gnome-fallback

- Timo

---

### Post by stinkeye on 2013-09-29
> **timo2 said:**
> Hey,

I got this info:
gnome-fallback

- Timo

...and the release....
```
cat /etc/lsb-release
```

Are you logging into the ubuntu session at the login screen but being dropped back to the gnome-fallback session.
The ubuntu session runs compiz as the window manager. The Unity interface is a plugin for compiz.

If your gfx card is incompatible with a 3d driver, you cannot run compiz/unity.

Test gfx compatibilty for running unity....
```
/usr/lib/nux/unity_support_test -p
```

eg my output...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 313.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

Also install a small application to tell you which window manager is running...
```
sudo apt-get install wmctrl
```

This terminal command will tell you your current window manager...
```
wmctrl -m
```

eg my output when in the ubuntu/unity session...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **wmctrl -m**
Name: [COLOR="#FF0000"]Compiz[/COLOR]
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

If your window manager is not [COLOR="#FF0000"]Compiz[/COLOR], compizconfig-settings-manager(ccsm) will not have any effect.

In the ubuntu session you can make the unity panel and menus transparent using ccsm...
[ATTACH=CONFIG]246582[/ATTACH]

but in the gnome-fallback session the gnome-panel is used and certain areas remain opaque as stated by **grahammechanical**.
[ATTACH=CONFIG]246583[/ATTACH]

---

### Post by timo2 on 2013-09-30
The Release Info:
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

Graphics infos:
> timo@timo-satellite:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 7640G
OpenGL version string:  4.2.12217 Compatibility Profile Context 12.104

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes



My window manager is Metacity...
> timo@timo-satellite:~$ wmctrl -m
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A


How can I set it to Compiz? I'm not using Unity, I'm using gnome <3

- Timo

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> The Release Info:


Graphics infos:


My window manager is Metacity...



How can I set it to Compiz? I'm not using Unity, I'm using gnome <3

- Timo

Try setting compiz back to defaults and then replacing metacity with compiz.
In terminal...
```
gconftool --recursive-unset /apps/compiz-1
```

then...
```
compiz --replace && disown
```

If the unity interface appears use ccsm to disable it.

PS compiz runs a lot better on 13.04 and if you install gnome-panel
you will have 2 extra login sessions...
[LIST]
[*]gnome-classic(no effects)....uses metacity
[*]gnome-classic.......uses compiz
[/LIST]

Both sessions use the old style gnome-panel.

Are you able to login to the unity session running compiz?

---

### Post by timo2 on 2013-09-30
I used your commands, still Metacity :o

//edit:
When I use 'compiz --replace', Compiz is starting BUT: I don't have any menu panels
for closing the windows anymore ^^

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> I used your commands, still Metacity :o

Are you able to login to the unity session running compiz?

The unity session can be changed to a gnome-classic session by disabling the unity plugin with ccsm and adding gnome-panel to startup applications

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> I used your commands, still Metacity :o

//edit:
When I use 'compiz --replace', Compiz is starting BUT: I don't have any menu panels
for closing the windows anymore ^^

In ccsm check the window decoration plugin is enabled.

---

### Post by timo2 on 2013-09-30
How do I add gnome to startup applications?

In Unity Compiz is the window manager and I already disabled the
Unity plugin.

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> How do I add gnome to startup applications?

In Unity Compiz is the window manager and I already disabled the
Unity plugin.
Easiest way would be to re-enable unity and search "startup" in the dash.
Add new entry as shown in pic and then disable unity again.

---

### Post by timo2 on 2013-09-30
thanks I tried it by myself.
The result is... I can't login anymore.

When I login with my correct user password, it throws me back
to the login screen.

I disabled the Unity plugin and now I can't even use gnome mode anymore :oo

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> thanks I tried it by myself.
The result is... I can't login anymore.

When I login with my correct user password, it throws me back
to the login screen.

I disabled the Unity plugin and now I can't even use gnome mode anymore :oo
I don't see how disabling the unity plugin and adding **gnome-panel** to startup would affect login.
You should still be loading the window manager compiz just with gnome-panel instead of the unity interface.
Check caps-lock isn't enabled.

---

### Post by timo2 on 2013-09-30
hey,

I tried it by myself :D
I disabled the Unity Plugin and then I  wanted to enable it but
the manager wasn't there anymore so I logged of without adding
gnome / unity to startup. The Unity plugin is disabled and gnome
is not autostarting.

With every login (Gnome / Unity) it throws me back to the login screen.

Any ideas without reinstall? :D

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> hey,

I tried it by myself :D
I disabled the Unity Plugin and then I  wanted to enable it but
the manager wasn't there anymore so I logged of without adding
gnome / unity to startup. The Unity plugin is disabled and gnome
is not autostarting.

With every login (Gnome / Unity) it throws me back to the login screen.

Any ideas without reinstall? :D

Are you saying you can't login to any session????

---

### Post by timo2 on 2013-09-30
Yeah. 
Do you think that it would be better to reinstall system?

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> Yeah. 
Do you think that it would be better to reinstall system?
Yep, it's all getting a bit silly.
Learning experience....

Use a live cd/usb to backup any personal files and reinstall.
Install 13.04 if you can.
As I said earlier, compiz has less bugs and if you install gnome-panel it will give you a 
session running compiz with the old style panel.

---

### Post by timo2 on 2013-09-30
Hey,

I reinstalled everything (and deleted windoof from my harddisk) but there are some
changed in 13.04 where I have 1 or 2 questions:

How do I change the panels? In 12.04 it was ALT + Mouse Click. In 13.04?
-> Win + Alt ;) Already solved :D

Another question is, why Compiz changed? There is no button opacity anymore...

-> Timo

---

### Post by stinkeye on 2013-09-30
> **timo2 said:**
> Hey,

I reinstalled everything (and deleted windoof from my harddisk) but there are some
changed in 13.04 where I have 1 or 2 questions:

How do I change the panels? In 12.04 it was ALT + Mouse Click. In 13.04?
-> Win + Alt ;) Already solved :D

Another question is, why Compiz changed? There is no button opacity anymore...

-> Timo
Hi timo2,
Up and running eh. 
A lot of old plugins aren't installed by default.
You need to install the **compiz-plugins** package.
Search in software centre or install via terminal....
```
sudo apt-get install compiz-plugins
```

Goodluck :p

---

### Post by timo2 on 2013-09-30
Hey,

Thanks so much, really. Thanks for your patience.
I'm using Debian for a while but Ubuntu with Unity is a challenge :b

Now I'm a very happy Ubuntu user :-)

- Timo

---

### Post by timo2 on 2013-09-30
I have a last question to you :o

I can't use my 'close, minimize and maximize' buttons anymore?
Every click, the browser get unselected.

---

### Post by stinkeye on 2013-09-30
I have experienced that in the beta release.
Run the software updater and make sure your system is up to date.

---

### Post by timo2 on 2013-09-30
Hey,

I thought it would be my fault :-)

Okay if its a system bug, its okay I thought it would be cause of Compiz :b

---

### Post by timo2 on 2013-10-01
Hey,

I don't wanted to create a new topic for this little question.

I played arround with compiz and everything is fine but I'd like to
set the opacity from 40% to 100%

The icons get the opacity from the panel but I'd like to set them
to 100%.

How can I do it or: How is the rule for compiz? :O

-> Thanks Timo :)

---

### Post by stinkeye on 2013-10-01
> **timo2 said:**
> Hey,

I don't wanted to create a new topic for this little question.

I played arround with compiz and everything is fine but I'd like to
set the opacity from 40% to 100%

The icons get the opacity from the panel but I'd like to set them
to 100%.

How can I do it or: How is the rule for compiz? :O

-> Thanks Timo :)
It can't be done.
Compiz opacity applies to whole window and contents.

Maybe try cairo-dock.
Includes many themes or make your own.
Installing cairo-dock will create a cairo-dock login session.

There are also simpler docks like tint2 and plank.
Pic shows plank at side and tint2 on bottom.
[ATTACH=CONFIG]246673[/ATTACH]

May want to look at installing kupfer or synapse while your messing around.
Gives you access to applications with ctrl+space if something goes wrong.
[ATTACH=CONFIG]246672[/ATTACH]

---


---
title: "Compiz not picking up the Gtk theme"
date: 2018-07-10
forum: Desktop Environments
---

### Post by gdesilva on 2018-07-10
Hi, I am running US 18.04 and installed Compiz. I added Compiz to my Startup Apps list and when I login, Compiz starts without any issues except that I cannot get all the features of the theme I am using - in particular, window buttons and fonts of the theme I am using. This is obviously related to gtk-window-decorator issue so I tried to configure gtk-window-decorator options (there is only a handful options to play with). If I leave gtk-window-decorator to use the defaults, I always get the default button set and fonts. The I tried it with the option --metacity-theme and then I just one button (close window) displayed. In essence, irrespective of what I specify, I either get the default theme buttons and options of a subset of buttons of a theme I force gtk-window-decorator to use.

BTW, this problem is not specific to 18.04 - it also existed in previous versions.

Any suggestions would be greatly appreciated.

---

### Post by again? on 2018-07-11
Do you have the required gtk2/gtk3 engine for your theme installed?
Can you post a link to a theme that gives you these problems?

---

### Post by gdesilva on 2018-07-11
@guber2, thanks for the response.

Synaptic showed that I did not have gtk3/2-xfce engines installed so I installed them - was not aware that the gtk engines need to be installed separately - thanks for the tip. Now when I run compiz, it seems that the general appearance is OK but still lacks the minimize, maximize buttons and only the close button is shown on windows.

I get the following output when I run compiz

```
$ compiz ccp --replace &
[1] 5780
compizza@kanga:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Info: Starting plugin: copytex
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: imgjpeg
compiz (core) - Info: Starting plugin: imgjpeg
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: imgsvg
compiz (core) - Info: Starting plugin: imgsvg
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: wobbly
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: commands
compiz (core) - Info: Starting plugin: commands
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: cube
compiz (core) - Info: Starting plugin: cube
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: rotate
compiz (core) - Info: Starting plugin: rotate
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (decor) - Warn: No default decoration found, placement will not be correct
/usr/bin/gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
compiz (decor) - Warn: No default decoration found, placement will not be correct
```

Only clue is that I get the message 'No default decoration found' even if I run gtk-window-decorator --replace separately.

The link to the theme I would like to use is [https://www.xfce-look.org/p/1191436/](https://www.xfce-look.org/p/1191436/)

Thanks

---

### Post by again? on 2018-07-11
I'm using Xubuntu 18.04 and if I replace xfwm4 with compiz I get a generic title bar
which shows all three buttons.
[ATTACH=CONFIG]280348[/ATTACH]

I haven't kept up with gtk theming so not sure what's going on.
Did come across this dconf setting.
org.compiz.gwd use-metacity-theme

Perhaps you need to install metacity.

---

### Post by gdesilva on 2018-07-11
@guber2, OK, I see....now I can get those default button no problems. However, what I am trying to do is to get gtk-window-decorator to display the buttons as per the theme and not gwd's default buttons. For example, if I set a particular theme, I would like gwd to display the same theme buttons when I run gtk-window-decorator --replace command. So when I start Compiz (and gwd when loading decor module) the windows show the buttons just like in your case. However, if I run gsettings set org.gnome.desktop.wm.preferences theme <whatever theme name> I just get only the close button somewhat similar to the theme buttons but not exactly the same either. The same happens if I set gtk-window-decorator --metacity-theme <name of the metacity theme> and again only the close button is shown.

---

### Post by gdesilva on 2018-07-13
What I found out was that gtk-window-decorator only recognizes metacity themes and does not render gtk2, gtk3 or xfce themes. If I specify the command to be used in the decor module in CCSM to 'gtk-window-decorator --metacity-theme Greybird' then all the theme features are displayed correctly. So, if you want to use a particular theme in Compiz, you have to make sure that the theme has a metacity version - ie there should be a folder called metacity-1 in /usr/share/themes/<your theme name> directory.

---

### Post by again? on 2018-07-14
Interesting...specifying the theme in CCSM works here as well.
Your finding will help others.
Can I ask why you still use compiz?

---

### Post by gdesilva on 2018-07-14
> **guber2 said:**
> 
Can I ask why you still use compiz?

I like to use the rotating cube and wobbly windows - desktop just comes alive when using Compiz as opposed to boring static windows!! No other reason.:D:D

---

### Post by mIk3_08 on 2018-07-14
> **gdesilva said:**
> I like to use the rotating cube and wobbly windows - desktop just comes alive when using Compiz as opposed to boring static windows!! No other reason.:D:D



Cool Stuff... Just Love the 3D Desktop and lots of effects. :D

---

### Post by again? on 2018-07-15
> **gdesilva said:**
> I like to use the rotating cube and wobbly windows - desktop just comes alive when using Compiz as opposed to boring static windows!! No other reason.:D:D
Ah ok.
Yes I stuck with it for a while just because I liked the cube flip and lamp animations even though I only use 2 workspaces.

---


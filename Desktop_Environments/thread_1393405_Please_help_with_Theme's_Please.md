---
title: "Please help with Theme's Please"
date: 2010-01-29
forum: Desktop Environments
---

### Post by lucas777 on 2010-01-29
Ive been here searching for the last 3 hours for themes, Ive been on Gnomelook dowloaded themes and most of them wont drag and drop into Ubuntu Appearance - Themes, All i want is a nice looking Desktop and all ive got so far is less hair on my head.. Are there some sort of program i need? On gnomelook on the left hand bar i see all these things like beryl and all this stuff, which ones work and what do i get? Please seriously someone help Cheers

---

### Post by joey-elijah on 2010-01-29
> **lucas777 said:**
> Ive been here searching for the last 3 hours for themes, Ive been on Gnomelook dowloaded themes and most of them wont drag and drop into Ubuntu Appearance - Themes, All i want is a nice looking Desktop and all ive got so far is less hair on my head.. Are there some sort of program i need? On gnomelook on the left hand bar i see all these things like beryl and all this stuff, which ones work and what do i get? Please seriously someone help Cheers

Start from the beginning and this will be easier =) 

What 'format' (i.e what's on the end, tar.gz, .emerald, etc) are the themes you're trying to download in? Provide a link if you like.

---

### Post by stinkeye on 2010-01-29
There are a few different types of themes.
gtk2.x..... complete window theme
icons.....icon packs
beryl emerald .....window border decorations

gtk2 themes are the most commonly used in ubuntu.
Some are not complete themes and once installed you will find them
in Appearances > theme > customize  under the controls and window border tabs.

beryl emerald themes can give you nice effects similar to windows7 aero,
and need to be installed with the emerald theme manager
Download emerald in synaptic package manager.

You can drag and drop gtk and icon themes into the Appearances window to install but in some cases you need to extract your downloaded file first to get to your theme, because it may contain another type of theme in it as well.
Also if drag and drop doesn't work try using the install button.
When you drag and drop if you don't already have a ~/.themes folder, it fails to create one and exits with an error.
Whereas if you use the install button it will create a ~/.themes folder if needed.

I would also download fusion-icon as well.
It enables you to easily switch between different window managers and window decorators.
To autostart fusion-icon, add it to Startup Applications using
```
fusion-icon -n
``` in the command box.
fusion-icon will show up in the notification area.

Hi joey-elijah,I'm subscibed to the OMG Ubuntu rss feed and used to get updates from someone called Joey.
Now they come from Dood.
So if your involved...nice site, Dude.

---

### Post by t.rei on 2010-01-29
Get some gtk2 themes - install them via drag/drop or, if that fails - put the folder that has the theme's name in ~/.themes/

You might want to check these themes, that actually have a ppa and are really well done mostly:
[http://www.bisigi-project.org]("http://www.bisigi-project.org/")

---

### Post by ebharv on 2010-01-29
Watch this it might help.
[Customizing the Ubuntu Desktop]("http://www.youtube.com/view_play_list?p=075E5352819DECF7")

There's a plethora of other videos on YouTube on the topic.

---

### Post by wsonar on 2010-01-29
Run Kubuntu   :rolleyes:

---

### Post by lucas777 on 2010-01-29
Okay i think i have the basics going, also i was watching some tut's on Youtube lastnight and seen this girl who had a sick setup like she had flames coming off the mouse and pink flame things around a folder when she opened it, how is all that done? Is that difficult?

---

### Post by stinkeye on 2010-01-30
> **lucas777 said:**
> Okay i think i have the basics going, also i was watching some tut's on Youtube lastnight and seen this girl who had a sick setup like she had flames coming off the mouse and pink flame things around a folder when she opened it, how is all that done? Is that difficult?
Sounds like compiz effects.
[_**[COLOR="DarkRed"]How to Configure compiz Fusion in Ubuntu 9.10(Karmic)[/COLOR]**_]("http://www.ubuntugeek.com/how-to-install-and-configure-compiz-fusion-in-ubuntu-9-10karmic.html")

I would also install fusion-icon and add it to Startup Applications with
```
fusion-icon -n
```in the command box.

---

### Post by lucas777 on 2010-01-30
Ok managed to get things going after some searching, compiz is great btw. Just one REALLY annoying problem.

This dock that i got, the black box around it is annoying the hell out of me, and i cannot seem to remove it and just have the icons floating on that silver thing. Any ideas how to remove it?

[http://img251.imageshack.us/img251/6870/screenshotkz.png](http://img251.imageshack.us/img251/6870/screenshotkz.png)

---

### Post by ebharv on 2010-02-01
> **lucas777 said:**
> Ok managed to get things going after some searching, compiz is great btw. Just one REALLY annoying problem.

This dock that i got, the black box around it is annoying the hell out of me, and i cannot seem to remove it and just have the icons floating on that silver thing. Any ideas how to remove it?

[http://img251.imageshack.us/img251/6870/screenshotkz.png](http://img251.imageshack.us/img251/6870/screenshotkz.png)

Looks like Cairo-dock. The should be a setting or something to remove that, or if you're running compiz and have the fusion-icon just reload the window manager and see if it goes away. 

I've also found Cairo-dock to be a bit more buggy than AWN, but thats my opinion.

By the way stinkeye... is that an emerald, metacity, kde, or gnome theme?

---

### Post by stinkeye on 2010-02-01
> **ebharv said:**
> 

By the way stinkeye... is that an emerald, metacity, kde, or gnome theme?
[_**[COLOR="DarkRed"]Moonlight2  [/COLOR]**_]("http://www.gnome-look.org/content/show.php?content=117826&forumpage=0")
with
[_**[COLOR="#8b0000"]Polaris window border[/COLOR]**_]("http://www.gnome-look.org/content/show.php/Polaris?content=93896")

---

### Post by fabounet on 2010-02-01
launch it with cairo-dock -c (your drivers are not enough opengl compliant)

---


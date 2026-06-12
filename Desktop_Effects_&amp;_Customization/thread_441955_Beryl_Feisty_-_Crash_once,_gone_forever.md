---
title: "Beryl Feisty - Crash once, gone forever"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by Abaddon on 2007-05-13
I´ve just done a completely fresh install of Feisty on my newly upgraded computer - which is a 

Core 2 Duo 2.13, 2Gb Ram.
Asus Commando Motherboard
Winfast Nvidia 8800GTS 640Mb

- and not surprisingly, is rather nice to use.

First thing after the feisty install, I installed the NVidia Driver - from Nvidia´s web-page, rather than the restricted driver manager version, and then I installed XGL Beryl, using the instructions [[COLOR="DarkOrange"]_here_[/COLOR]]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#Ubuntu").

It all works fine for a while as I´m trying to tweak my settings, but then all of a sudden it crashes and drops back to Metacity.

Unfortunately, I´m not able to get it to ever work again after than, no matter what I fiddle with, uninstall, delete, purge or otherwise tweak.  Every time I reload, the Beryl-manager gem sits in my tray mocking me, and refusing to give me any shiny.

Does anyone have any ideas - or hints on how I can debug this to provide more useful information?

Cheers,

Abaddon.

---

### Post by strumluff on 2007-05-13
I thought you could install Beryl simply with AIGLX on nvidia cards, it basically means theres nothing to it as you should be able to run Beryl in a standard gnome session. I wouldn't recommend installing on XGL unless you're an ATI user with an unsupported card as XGL eats more resources and Beryl is known to be more buggy/unstable with it.

Step 1 -> Install Nvidia drivers, any method would work, Restricted Drivers being the easiest or using Envy script. I guess the drivers from the nvidia site shouldn't be a problem either, I'm just not sure how it handles the xorg.conf.

Test with: glxinfo | grep direct

If it returns something like ```
direct rendering: yes
``` then the drivers are fine.

2 -> Install Beryl with: ```
sudo aptitude install beryl beryl-manager emerald-themes
```

You should install from the universe repo as there is no need for any specific repo unless you want an SVN version or something.

Once thats done you should be able to run it straight away (assuming you restarted X after installing the drivers) with beryl-manager

---

### Post by Abaddon on 2007-05-13
That did indeed work - much more straight forward, thanks!

---


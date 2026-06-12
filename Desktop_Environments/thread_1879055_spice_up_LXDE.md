---
title: "spice up LXDE?"
date: 2011-11-10
forum: Desktop Environments
---

### Post by Maro848 on 2011-11-10
Hey guys I'm using Lubuntu 11.10 on an old dell with 256mb of ram and 20gb of hard disk space. I would like to spice up the desktop with a dock. Hopefully something similar to Cairo-dock. I have tried "sudo apt-get install cairo-dock" and it reports it couldn't find the package. There something that could give my old laptop a WOW factor or should I just make due with the standard panels?

---

### Post by Rodney9 on 2011-11-10
Hi Maro848, 

I use and love Lubuntu 11.10.

There are many ways to spice up Lubuntu, for a dock follow this [tutorial]("http://blip.tv/ubuntu-switcher/lubuntu-screencast-lxpanel-2-panel-configuration-5316669"), that's what I did for my desktop in the image below -


For more How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

Rodney

---

### Post by 73ckn797 on 2011-11-10
Have you enabled the repositories in Synaptic? You would have to first install Synaptic via the Software Center or in terminal enter:
```
sudo apt-get install synaptic
```Once installed, open and go to "Settings/Repositories/Other Software and select Canonical Partners.

---

### Post by Maro848 on 2011-11-10
thank you I will give conky a try and let you know how it goes

---

### Post by Rodney9 on 2011-11-10
> **Maro848 said:**
> thank you I will give conky a try and let you know how it goes

Conky is terrific and very useful, but it is not a dock like cairo or a second lxde panel as in the tutorial.

Rodney

---

### Post by Maro848 on 2011-11-10
Yes I was hoping it would use fewer resources however I was unsuccessful though in using either conky or cairo as both instantly sent my cpu and ram usage to the point where the computer is hardly useable. taking minutes just to start chromium so I will try something else

---

### Post by rokytnji on 2011-11-10
I don't run Lubuntu. But I do run LXDE and other Open Box type of Desktops on my gear. You are pretty much just limited by know how/experience and imagination.

My thread at LXDE forum in case you need a conky file.

[http://forum.lxde.org/viewtopic.php?f=11&t=31202](http://forum.lxde.org/viewtopic.php?f=11&t=31202)

Tint2 panel will run in a Open Box Desktop Like LXDE also. This is my setup on another Open Box Desktop (Fluxbox) that I am posting from.

[ATTACH]206902[/ATTACH]

As you can see. Tint2 is pretty configureable also. It is the right hand side panel. I have it set to auto-hide when not in use. 

Good Luck with your new Install. 

Happy Trails, Rok

---

### Post by Maro848 on 2011-11-10
Tint2 looks nice I was just looking for a lightweight dock that was similar to cairo since I use that in my Linux Mint installs and have experimented with it in Ubuntu. Nice dock unfortunately when I'm running a 500mhz cpu and 256mb of ram cairo just wasn't able to run. So I will attempt to set up a second LXDE panel and just use that since it would probably be the easiest on my resources.

---

### Post by rokytnji on 2011-11-10
Ok. Saw that your 256MB of ram stumbled with conky and cairo dock.

Tint2 is very light on resources. Too make your Life easier. Here is my ~/.config/tint2/tint2rc file.

You can change the 

```
# APPLICATION LAUNCHER
#---------------------------------------------
launcher_padding = 2 4 2
launcher_background_id = 5
# Icon size
launcher_icon_size = 32

# Each launcher_item_app must be a full path to a .desktop file
launcher_item_app = /usr/share/applications/iceape-mailnews.desktop
launcher_item_app = /usr/share/applications/iceape-navigator.desktop
launcher_item_app = /usr/share/applications/geany.desktop
launcher_item_app = /usr/share/applications/gimp.desktop
launcher_item_app = /usr/share/applications/vlc.desktop
launcher_item_app = /usr/share/applications/gksu.desktop
launcher_item_app = /usr/share/applications/roxterm.desktop
launcher_item_app = /usr/share/applications/Thunar.desktop
launcher_item_app = /usr/share/applications/rox-filer.desktop
launcher_item_app = /usr/share/applications/opera-browser.desktop
```

To whatever ,desktop applications you use in Lubuntu. Unless Lubuntu is way different on file paths. My /usr/share/applications path should be ok to use. Same for everything else in the file including autohide.

Be sure and rename your original tintrc to tintrcbackup to keep the original before inserting my new text file named tint2rc.

Again Good Luck with it.

[ATTACH]206906[/ATTACH]

---

### Post by Maro848 on 2011-11-10
ok I may give this a shot since I have no other current projects I wonder how it will look with that and my LXDE panels..... one way to find out I guess, thanks for the file

---

### Post by Rodney9 on 2011-11-10
> **Maro848 said:**
> 
 So I will attempt to set up a second LXDE panel and just use that since it would probably be the easiest on my resources.

Your correct there and it is fairly easy.

---

### Post by Maro848 on 2011-11-11
yes it was very simple I wish I had a screen shot program on there already so I could show you how I did it but I think that will work out well

---

### Post by Rodney9 on 2011-11-11
> **Maro848 said:**
> yes it was very simple I wish I had a screen shot program on there already so I could show you how I did it but I think that will work out well

Well done, yes we would like to see it.

There is a screen shot program built in Lubuntu called scrot. 

Just press 'print screen' on your keyboard, then look in your home folder where you will see a file called some thing like this - 2011-11-12-044633_1366x768_scrot.png

Rodney

---

### Post by rokytnji on 2011-11-11
Glad it works for you. You can move around that tint2 panel to wherever you want on the desktop by editing 

```
panel_position = bottom right vertical
#panel_position = bottom right horizontal
```

part of tint2 rc file. I just like it on the right hand side is all.

Uncomment bottom right horizontal and comment out bottom right vertical (comment = #)

For future reference though I don't know how well it will work on 256MB of ram. 512MB would be better IMO. Wbar which is also in package manager and fbpanel are others that can be tried out also. They are both lighter on resources than cairo dock. Here is my motorcycle shop wireless Desktop running Fluxbox with wbar on the bottom and lxpanel on top (autohide also). I got this machine out of a dumpster by the way. Just to give you a idea on how configurable open box desktops are is all.

[ATTACH]206978[/ATTACH]

---

### Post by MG&amp;TL on 2011-11-11
Create new panels, move them around, use them for different things, change your background, change your icons, muck about with the openbox configuration thing.

---

### Post by Maro848 on 2011-11-11
Those sound like good ideas there are also a couple of different desktops available for use Im gonna check those out and customize them to find the one that works best.

---

### Post by Maro848 on 2011-11-11
ok well none of the panels/bars I installed were light enough to still use the machine (then again I'm lucky to be using 11.10 with this machine)so here is a screenshot of my desktop with two LXpanels

[ATTACH]206980[/ATTACH]

---

### Post by MG&amp;TL on 2011-11-11
Looks pretty cool-whatever works for you.

---


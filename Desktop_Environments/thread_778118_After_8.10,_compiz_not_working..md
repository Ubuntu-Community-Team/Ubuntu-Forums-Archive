---
title: "After 8.10, compiz not working."
date: 2008-05-01
forum: Desktop Environments
---

### Post by keforex on 2008-05-01
I meant... 8.04 --- doh... sorry.


Well... I upgraded to 8.04 and although it did work fine at first, all of a sudden my effects that were controlled by compiz are simply dead.

I still have compiz installed and all the effects are there and selected and configured, but there are no effects being produced (for example wobbly windows, or minimize effects, etc).

Another thing that completely stopped working is my Avant Window Navigator. I used to have the 3D Leopard style bar at the bottom of the screen but now it's gone. 

Any advice on how to get these 2 issues resolved?

---

### Post by Zorael on 2008-05-02
Upgraders get this sometimes. The problem usually lies in there being incompatible remnants of your old compiz/emerald/awn/app-in-question left in your system. So let's get rid of those and then reinstall.

[list=1][*]First, make sure you don't have any foreign third-party repositories enabled in Software Sources, alternatively as lines in **/etc/apt/sources.list** or *.list files in **/etc/apt/sources.list.d/**.
[*]Then open up Synaptic, search for packages which match "compiz" somehow, and mark them for **complete removal**. Apply, then reinstall them. Terminal command as follows (after repository removal).
```
$ sudo aptitude purge ~ncompiz ~nberyl ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```
[*]If you're running KDE (Kubuntu), do this as well to get all relevant packages (and remove irrelevant ones.)
```
$ sudo aptitude purge compiz-gnome compiz-kde+
```[/list]

You may need to do the same with avant-window-manager packages.

---

### Post by macpeteo on 2008-05-02
I have performed the above steps but I cant get any of the "themes" in Emerald to work. No matter what theme I pick, it does not change the window look!

Is there a config file that I must manually change?

Thanks,
Mac

---

### Post by Zorael on 2008-05-03
> **macpeteo said:**
> I have performed the above steps but I cant get any of the "themes" in Emerald to work. No matter what theme I pick, it does not change the window look!

Is there a config file that I must manually change?

Thanks,
Mac
The Emerald theme manager does enable the theme you pick, but the changes don't apply if Emerald isn't running (as the current window decorator) in the first place.

To begin with, you must make sure you're running Compiz, since Emerald needs a window compositioner to work. I'm not too familiar to the Gnome-integrated way of enabling it as the default window manager, but I hear you need to seek out Visual Effects and pick your setting there.

Alternatively, to enable it until next login, enter this in a terminal.
```
$ compiz --replace &
```
If it outputs error commands, paste them here.


I suggest you install the **fusion-icon** package and have it run upon boot to more easily manage which manager and decorator is running at any given time.

---

### Post by macpeteo on 2008-05-03
This what I get when I execute "compiz --replace &"

root@petes-linux-box:/home/Mac# compiz --replace &
Checking for Xgl: [1] 15749
root@petes-linux-box:/home/porzech# not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0343 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Thanks,
Mac

---

### Post by Zorael on 2008-05-03
Minor thing: you don't want to run stuff like this as root. :>

Compiz seems to have started there. If you're still seeing your Gnome themes, chances are it's running the gtk-window-decorator decorator instead of Emerald. If you enable the Window Decorations plugin in ccsm (compizconfig-settings-manager), you should be able to enter '**emerald --replace**' in the Command field of that plugin's settings.

Regardless; enter that command in a terminal for now to see if it's working.
```
$ emerald --replace &
```

---

### Post by macpeteo on 2008-05-03
"emerald --replace &" seems to have done it, its working.

Now in 7.10 I recall creating a small file to get emerald started and running, is there a config file that I need to create or tweak in order for emerald to be my desk top decorator?

And why isn't this part of the system, I should not be having to do all this manually :(



Thanks,
Mac

---

### Post by macpeteo on 2008-05-03
"If you enable the Window Decorations plugin in ccsm (compizconfig-settings-manager), you should be able to enter 'emerald --replace' in the Command field of that plugin's settings."

Sorry, I'm a bit of a Linux novice, where is it that I can find this config file, if thats what it is?


Thanks,
Mac

---

### Post by Zorael on 2008-05-03
It usually does work, but as an upgrader, you're sadly bound to experience some kinks here and there. Mind, with the Window Decorations plugin enabled in ccsm (compizconfig-settings-manager), it should launch Emerald (or perhaps gtk-window-decorator) by default, in the compiz startup procedure. And again, check the settings for said plugin, notably the command line.

I'd suggest you grab the **fusion-icon** package and add an entry in Sessions to start it upon login. It'll put an icon in your systray with which you can manipulate compiz.

To answer your question, such a script you're talking about could look like this, though needlessly elaborate, but I like it that way.
```
#!/bin/bash

compiz --replace &

# sleep for 7 seconds to let Compiz load properly, modify figure as you please
sleep 7

if [ "$(pidof emerald)" ]
then
	# compiz started emerald, do nothing
else
	# not running, start emerald
	emerald --replace &
fi
```

---

### Post by Zorael on 2008-05-03
> **macpeteo said:**
> "If you enable the Window Decorations plugin in ccsm (compizconfig-settings-manager), you should be able to enter 'emerald --replace' in the Command field of that plugin's settings."

Sorry, I'm a bit of a Linux novice, where is it that I can find this config file, if thats what it is?


Thanks,
Mac
If you have the **compizconfig-settings-manager** package installed, you should have a Compiz Settings Manager entry in your Applications menu. Else just hit Alt+F2 to spawn a run box and enter **ccsm**. The commands I listed earlier should've installed it for you:
```
$ sudo aptitude install compiz **compizconfig-settings-manager** emerald
```

---

### Post by macpeteo on 2008-05-03
Zorael, thanks for all ur help and understanding :)

I decided to just do a clean install and at this point all seems to be working as expected. However a few things did not go a smooth as I would have liked.

1. I had to install compiz and emerald manually and including the compiz fusion icon (that icon is a big help) anyway after doing that, I still did not have the "Advanced Desktop Effects Settings" under System > Preferences

I then had to load in another item the "small ccsm" using Syn. Package Manager.

Now everything is there and running but my Emerald themes are all gone! Is there repository where I can get those? I had about 12-24 nice ones that came with Emerald when I first installed it on 7.10, where can I get all the "default" themes.

Again, thanks for all ur help,
Mac

---

### Post by Zorael on 2008-05-04
Try [http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes).

---

### Post by jonny.milano on 2008-05-04
hi there,

this is my first ever post in the forum, so pls be kind! i am a total linux newbie switching from mac. i am very impressed so far. just one thing: i too tried to install AWN by following the steps on this page:
[http://wiki.awn-project.org/Installation](http://wiki.awn-project.org/Installation)
i installed Compiz and then AWN. thing is after i rebooted, i noticed that my graphics card was not happy at all. 
when i log in and reboot now i see the cursor as an 'X' for a few moments and the screen kind of flashes along a split along the diagonal axis through it. other menus do this as well. when i play movies they are very slow and jerky and i can see a visable split along the diagonal axis from the bottom left to the top right of the window. it's very jerky as the movie plays. i was unhappy, so i completely removed all compiz packages, thinking that that was the problem. but it's still there! and windows are slow too! poor performance. any help would be greatly appreciated. 

thanks!

ps scrolling is jerky too! could it be something else in the AWN install??

---

### Post by LostinSpacetime on 2008-10-13
this is probably because of the xgl package. Deinstall or disable it. Disable: create ~/.config/xserver-xgl/disable

the file is empty

---

### Post by jonny.milano on 2008-10-13
wow! long time since i posted that! thanks for the reply. i don't think that it is that though as that package was not installed. i am on an old, pre 2000 computer though and i think that those effects are just too intensive for the little guy. i eventually turned off all desktop effects and compiz and my computer seems pretty happy with the standard gnome. i really have to say that i am loving ubuntu! it's amazing coming from commercial OS's!

---

### Post by eenofonn on 2008-10-31
Thanks so much can't tell you the headache you saved me ;)

---

### Post by Spasysheep on 2008-11-02
I'm having a slightly different problem, I have compiz installed and set up after a clean install of 8.10 but none of the effects are working? do I need to set compiz as my deafault window manager or something like that, and how do I do it? Idon't (to my knowlege) have emerald or any other dektop manager installed, just compiz.

---


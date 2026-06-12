---
title: "A few Fluxbox questions..."
date: 2008-04-15
forum: Desktop Environments
---

### Post by ichibanhashi on 2008-04-15
I apologize if this post is repetitive and these questions have already been answered. I looked at some similar posts and didn't find the answers I wanted but didn't have time to go through all of the posts about fluxbox! At any rate, feel free to direct me to existing posts if I have missed them.

I recently installed fluxbox and I love the sleek customizability that it affords; however, I've encountered a few problems:

1) My slit applications will sometimes disappear after a period of time. Often it will be when I've left my system for an extended period of time that I come back and find that they've vanished. It's not that I've rebooted or restarted fluxbox or anything. I realize that to keep them through this event I'd need to add them to the apps file. Anyone have any idea what's causing this?

2) I've been experiencing some very strange behavior with my ~/.fluxbox/init file. I edited it to override my theme's background picture with

```
session.screen0.rootCommand:	fbsetbg /home/bacher/.fluxbox/backgrounds/moon.jpg
```

which works fine; however, whenever I add more "session.screen0.rootCommand:"s I end up with a black screen on boot. What's really confusing is that I can manually set the background with this very line of code, but when there are multiple session.screen0.rootCommand: lines in tandem it just doesn't seem to want to work. I like to run several commands at startup to connect me to the network I'm on (my uni has a really strange configuration that required a wacky work-around.) To solve this issue I made a crappy shellscript with these commands in them:

```
#!/bin/sh
sudo rm /var/run/wpa_supplicant/eth0
sudo wpa_supplicant -ieth0 -c/home/bacher/wpa_supplicant.conf -Dwired -B
sudo dhclient eth0
```

and I execute this through my ~/.fluxbox/apps file:

```
[startup] {xterm <script path>}
```

so, whenever I startup, my little script executes the commands I need for network connectivity, but I always get an xterm session popping up and asking for my password at startup. Anyone have any more refined methods for achieving the same goal? Is there a better place for these commands than where they are or in the ~/.fluxbox/init file? Have any ideas what may have been causing the wacky behavior to begin with?

3) Transparency doesn't seem to work as of now. I haven't researched this one at all. If this is a /facepalm moment, feel free to ignore the question. I set it in the menu config and it didn't magically work. If there's a good resource to figuring out how to do this that may save me some googling time, then I'd appreciate a link.

4) GTK programs don't look right at all. Is there any method to deuglifying them? I fixed the fugly and huge fonts that were on by default in GTK programs, but they still just look off in the environment. Is there any way that people have integrated GTK programs with their fluxbox themes? I'd be very pleased with similar sleek functionality in my programs as I have in my window manager.

5) Some GTK programs seem to run slower than when I was using gnome. The worst example of which I have found thus far was Amarok. Scrolling through the playlist was slow, laggy and jerky. I expected a general increase in program speed when switching to fluxbox, or at the very least, a slight decrease. The jerky/nearly buggy amarok playlist was a total shock. Anyone have any clue what's going on here?

Thanks a million in advance!

---

### Post by spupy on 2008-04-15
About point 4) - get the program called "lxappearance". With it you can change GTK programs - themes, icons, fonts, and other things. There are two other programs (gtk-chtheme and one more), but this one is the best. No need to run Gnome's setting-daemon.

About the transparency - fake one should always work, but then the only things that can be transparent are some terminals (like aterm), fluxbox' menus and windows' titlebars. And fake transparency doesn't look so good IMHO. With xcompmgr you can get real transparency. Xcompmgr is a compositing manager that is not a window manager by itself (like compiz is), so works perfect with fluxbox. It has some other effects (well, the only other besides transparency) - shadows and fade-in/-out effects. 

About the other points - can't help you much, sorry. :/ If I remember anything else, i will write it.

---

### Post by kerry_s on 2008-04-15
wait for RedSquirrel, he's the master of fluxbox/openbox around here. i'm all jwm, but i'll try some of these. :)

1) have no idea, might be the version of fluxbox is still buggy.
2) the new method is to use the style_overlay->
[http://fluxbox-wiki.org/index.php/Howto_style_overlay](http://fluxbox-wiki.org/index.php/Howto_style_overlay)

sudo command= add your script to sudoers so it don't need a password.
[B]sudo visudo
[/B]
user    ALL=NOPASSWD: path/to/script

change "user" to your log in name.

3) could be the version, there's a buggy version, that had to be recompiled for things to work right.
4) use a ~/.gtkrc-2.0 file
example:
gtk-theme-name = "SlickGloss"
gtk-font-name = "Sans 14"

5) fluxbox is gtk based, gtk programs will be faster, Amarok i think is a qt program, made more for kde.

---

### Post by RedSquirrel on 2008-04-15
> **ichibanhashi said:**
> I recently installed fluxbox and I love the sleek customizability that it affords; however, I've encountered a few problems: ...

You have had some great help already, but I'll add some more comments. :)

1) I haven't used the slit in a while. It could be that one of the dockapps you're using has a problem or maybe it's a fluxbox bug. You'll have to do some research on that one. Is there anything in your ~/.xsession-errors file?

2) For startup programs, I use ~/.fluxbox/startup.

3) For pseudo-transparency, you need a good wallpapersetter.

```
fbsetbg -i
```Should report:
"blah-blah is a nice wallpapersetter. You won't have any problems."

I always use feh as a wallpapersetter. (Well, these days I use xsetroot/fbsetroot for a grey or blue solid background colour.)

```
sudo apt-get install feh
```Check:
```
fluxbox -i
``````
xdpyinfo | grep RENDER
```Both of these commands should indicate that RENDER has been enabled (it probably has been in both cases).

For true transparency, you need xcompmgr and and transset.

[http://fluxbox-wiki.org/index.php/Transparency](http://fluxbox-wiki.org/index.php/Transparency)

I haven't read through that guide, but it should at least give you a starting point if you want true transparency.

4) Covered above. I edit my own ~/.gtkrc-2.0 file, but you can also use one of the tools, such as gtk-chtheme. Post a screenshot if you want to show the ugly part(s). If you don't specify a GTK+ theme, you get stuck with "Raleigh" which is not very fancy.

You can also edit the colours of the GTK+ theme.
[http://ubuntuforums.org/showthread.php?t=752673](http://ubuntuforums.org/showthread.php?t=752673)


One reason the fonts may look odd is that your DPI is too low (I think GNOME uses 96 by default). One easy way to fix that is to create the file ~/.Xresources and put this line it:

```
Xft.dpi:    96
```If you login via gdm, that file is loaded automatically.

5) Not sure. I don't use Amarok at all.

---

### Post by jviscosi on 2008-04-16
> **ichibanhashi said:**
> 
1) My slit applications will sometimes disappear after a period of time. Often it will be when I've left my system for an extended period of time that I come back and find that they've vanished. It's not that I've rebooted or restarted fluxbox or anything. I realize that to keep them through this event I'd need to add them to the apps file. Anyone have any idea what's causing this?


What dockapps are doing this?  I've found that a couple of the dockapps I use have a tendency to die unexpectedly, so I wrapped them in scripts that just restart them when that happens.  wmBiff, wmLog, and wmSuperMon are three that leap to mind.

---


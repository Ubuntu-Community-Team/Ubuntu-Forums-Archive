---
title: "XGL/Compiz on Xubuntu (XFCE)"
date: 2006-06-26
forum: Desktop Environments
---

### Post by SimoneDice on 2006-06-26
I really like XGL/Compiz and I really like Xubuntu.  However, I have not been able to find a 'how-to' to get this loaded on. I read posts that it has been done, and I tried getting it working several times on new installs, but I wasn't able to.

Does anyone have a link of a good how-to for Xubuntu or does anyone have it installed and is willing to write a 'how-to?

---

### Post by Kashirigi on 2006-06-28
I'm just seconding this motion. My super fancy desktop could be even fancier if I was using XFCE. . .

---

### Post by Kashirigi on 2006-06-28
Some googling around got me to this page:
[http://gentoo-wiki.com/HOWTO_XGL#With_xfce4-session](http://gentoo-wiki.com/HOWTO_XGL#With_xfce4-session)

I'm going to try it when I get home -- my laptop doesn't support XGL, sadly, so I'm stuck with the desktop.

---

### Post by mucnix on 2006-06-28
Well I've got it working.  Put this file in your home directory and name it .Xsession.  Of course you'll have to have xgl and compiz installed from the repos.
begin file:

Start up Xgl, compiz, and xfce
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start xfce 
exec xfce4-session

:end file


I used the same script on gnome I just put xfce4-session rather than gnome-session at the end.

Hope this works for someone

---

### Post by Kashirigi on 2006-07-01
It doesn't work for me.

When I run it, .xession-errors produces this:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "paul"
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
/usr/bin/startxfce4: X server already running on display :0
Xlib:  extension "XFree86-VidModeExtension" missing on display ":0.0".
compiz.real: Another composite manager is already running on screen: 0
compiz.real: No managable screens found on display :0.0

** (update-notifier:8852): WARNING **: already running?


Mind you, when I run 
Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo & (ignore the automatically generated smiley)

I get this:
 X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  94
  Current serial number in output stream:  95

[1]+  Exit 1 


Which, if I interpret it correctly, means I will need a better card or go about this in a different way.

---

### Post by datube on 2006-08-01
Hi,
I've done this with nVidia GeForce MX 440 64Mb P3/800Mhz/256Mb (should be working with ATI also).
Make sure you've got acceleration working, otherwise this will not work. Xgl/Compiz is still not stable, so this setup enables you to start with a normal Xfce session in case things get bad.

***Note**: If you're adventures and want to have the latest plugins, you can use repositories build from cvs found at [http://ubuntu.compiz.net](http://ubuntu.compiz.net/). But remember that downgrading packages afterwards can be tough!*

1) Install the following packages (may need to (re)enable universe repositories):
```
$ sudo aptitude install compiz xserver-xgl libgl1-mesa libglitz-glx1
```

2) Create gdm-session entry:
```
$ sudo gedit /usr/share/xsessions/xgl-xfce.desktop
```
```
[Desktop Entry]
Encoding=UTF-8
Name=Xfce Session (Xgl/Compiz)
Comment=Use this session to run Xfce (Xgl/Compiz) as your desktop environment
Exec=/usr/bin/startxgl-xfce 1 xfce non-ati -ng
Icon=
Type=Application
```

3) Create xgl-startup-script for Xfce session:
```
$ sudo gedit /usr/bin/startxgl-xfce
```
..and paste code found [here](http://svn.xgl-coffee.org/xgl-coffee/trunk/startxgl).

4) Replace code after: elif [ "$2" = "xfce" ]; then.
```
DISPLAY=:$1 xfce-mcs-manager &
DISPLAY=:$1 gnome-window-decorator & 
#DISPLAY=:$1 xftaskbar4 &
#DISPLAY=:$1 xfdesktop &
DISPLAY=:$1 exec xfce4-session
#DISPLAY=:$1 exec xfce4-panel
```

4) Make it executable:
```
$ sudo chmod +x /usr/bin/startxgl-xfce
```

5) Restart GDM with CTRL+ALT+BCKSPC
Before logging in, select the "Xfce Session (Xgl/Compiz)" from session list. Then continue.

**Note #1**: Not all plugins seem to work (maximize/zoom).
**Note #2**: To have 'opacity' plugin, download it from [thread 132063](http://ubuntuforums.org/showthread.php?t=132063) or [directly](http://ubuntuforums.org/attachment.php?attachmentid=6220&stc=1&d=1140209767).
Extract the .so file to the /usr/lib/compiz/ directory ($ sudo thunar). Remember to add it to /usr/bin/startxgl-xfce!
**Note #3**: Here are [some instructions from Gentoo-Wiki](http://gentoo-wiki.com/Compiz) for (latest) Compiz plugins.
**Note #4**: You must restart GDM after your session, before others can be able to use it! (CTRL+ALT+BCKSPC)
**Note #5**: Xfce contains a nice composite manager of it's own; If you customize the panel (opacity), the settings will also be applied in the 'Xgl version'. You can enable it by pasting this at the end of your xorg.conf:
```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

Good luck and have fun!

datube

---

### Post by s0undt3ch on 2006-08-14
> **datube said:**
> Hi,
I've done this with nVidia GeForce MX 440 64Mb P3/800Mhz/256Mb (should be working with ATI also).
Make sure you've got acceleration working, otherwise this will not work. Xgl/Compiz is still not stable, so this setup enables you to start with a normal Xfce session in case things get bad.

***Note**: If you're adventures and want to have the latest plugins, you can use repositories build from cvs found at [http://ubuntu.compiz.net](http://ubuntu.compiz.net/). But remember that downgrading packages afterwards can be tough!*

1) Install the following packages (may need to (re)enable universe repositories):
```
$ sudo aptitude install compiz xserver-xgl libgl1-mesa libglitz-glx1
```

2) Create gdm-session entry:
```
$ sudo gedit /usr/share/xsessions/xgl-xfce.desktop
```
```
[Desktop Entry]
Encoding=UTF-8
Name=Xfce Session (Xgl/Compiz)
Comment=Use this session to run Xfce (Xgl/Compiz) as your desktop environment
Exec=/usr/bin/startxgl-xfce 1 xfce non-ati -ng
Icon=
Type=Application
```

3) Create xgl-startup-script for Xfce session:
```
$ sudo gedit /usr/bin/startxgl-xfce
```
..and paste code found [here](http://svn.xgl-coffee.org/xgl-coffee/trunk/startxgl).

4) Replace code after: elif [ "$2" = "xfce" ]; then.
```
DISPLAY=:$1 xfce-mcs-manager &
DISPLAY=:$1 gnome-window-decorator & 
#DISPLAY=:$1 xftaskbar4 &
#DISPLAY=:$1 xfdesktop &
DISPLAY=:$1 exec xfce4-session
#DISPLAY=:$1 exec xfce4-panel
```

4) Make it executable:
```
$ sudo chmod +x /usr/bin/startxgl-xfce
```

5) Restart GDM with CTRL+ALT+BCKSPC
Before logging in, select the "Xfce Session (Xgl/Compiz)" from session list. Then continue.

**Note #1**: Not all plugins seem to work (maximize/zoom).
**Note #2**: To have 'opacity' plugin, download it from [thread 132063](http://ubuntuforums.org/showthread.php?t=132063) or [directly](http://ubuntuforums.org/attachment.php?attachmentid=6220&stc=1&d=1140209767).
Extract the .so file to the /usr/lib/compiz/ directory ($ sudo thunar). Remember to add it to /usr/bin/startxgl-xfce!
**Note #3**: Here are [some instructions from Gentoo-Wiki](http://gentoo-wiki.com/Compiz) for (latest) Compiz plugins.
**Note #4**: You must restart GDM after your session, before others can be able to use it! (CTRL+ALT+BCKSPC)
**Note #5**: Xfce contains a nice composite manager of it's own; If you customize the panel (opacity), the settings will also be applied in the 'Xgl version'. You can enable it by pasting this at the end of your xorg.conf:
```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

Good luck and have fun!

datube


This worked for me, but I get a 800x600(desktop) on a 1280x1024 resolution on the top left of my screen!

How do I solve that part?

---

### Post by Vinze on 2006-09-11
> **datube said:**
> Hi,
I've done this with nVidia GeForce MX 440 64Mb P3/800Mhz/256Mb (should be working with ATI also).
Make sure you've got acceleration working, otherwise this will not work. Xgl/Compiz is still not stable, so this setup enables you to start with a normal Xfce session in case things get bad.

***Note**: If you're adventures and want to have the latest plugins, you can use repositories build from cvs found at [http://ubuntu.compiz.net](http://ubuntu.compiz.net/). But remember that downgrading packages afterwards can be tough!*

1) Install the following packages (may need to (re)enable universe repositories):
```
$ sudo aptitude install compiz xserver-xgl libgl1-mesa libglitz-glx1
```

2) Create gdm-session entry:
```
$ sudo gedit /usr/share/xsessions/xgl-xfce.desktop
```
```
[Desktop Entry]
Encoding=UTF-8
Name=Xfce Session (Xgl/Compiz)
Comment=Use this session to run Xfce (Xgl/Compiz) as your desktop environment
Exec=/usr/bin/startxgl-xfce 1 xfce non-ati -ng
Icon=
Type=Application
```

3) Create xgl-startup-script for Xfce session:
```
$ sudo gedit /usr/bin/startxgl-xfce
```
..and paste code found [here](http://svn.xgl-coffee.org/xgl-coffee/trunk/startxgl).

4) Replace code after: elif [ "$2" = "xfce" ]; then.
```
DISPLAY=:$1 xfce-mcs-manager &
DISPLAY=:$1 gnome-window-decorator & 
#DISPLAY=:$1 xftaskbar4 &
#DISPLAY=:$1 xfdesktop &
DISPLAY=:$1 exec xfce4-session
#DISPLAY=:$1 exec xfce4-panel
```

4) Make it executable:
```
$ sudo chmod +x /usr/bin/startxgl-xfce
```

5) Restart GDM with CTRL+ALT+BCKSPC
Before logging in, select the "Xfce Session (Xgl/Compiz)" from session list. Then continue.

**Note #1**: Not all plugins seem to work (maximize/zoom).
**Note #2**: To have 'opacity' plugin, download it from [thread 132063](http://ubuntuforums.org/showthread.php?t=132063) or [directly](http://ubuntuforums.org/attachment.php?attachmentid=6220&stc=1&d=1140209767).
Extract the .so file to the /usr/lib/compiz/ directory ($ sudo thunar). Remember to add it to /usr/bin/startxgl-xfce!
**Note #3**: Here are [some instructions from Gentoo-Wiki](http://gentoo-wiki.com/Compiz) for (latest) Compiz plugins.
**Note #4**: You must restart GDM after your session, before others can be able to use it! (CTRL+ALT+BCKSPC)
**Note #5**: Xfce contains a nice composite manager of it's own; If you customize the panel (opacity), the settings will also be applied in the 'Xgl version'. You can enable it by pasting this at the end of your xorg.conf:
```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```

Good luck and have fun!

datube

As all guides I've tried up till now, this didn't work. And again, as with all guides, when I did:
```
Section "Extensions"
          Option  "Composite" "Enable"
EndSection
```
I did get drop shadows and could do a transparent panel, but *I want wobbly windows and cubes*! Weeeeeeeeeh!

When I select the Xgl session in gdm it takes a while, then brings me back to the gdm... How can I solve this? Please help.

---

### Post by Vinze on 2006-09-12
I get the following:

> $ startxgl-xfce 1 xfce nvidia/other
###### STARTXGL SCRIPT ######
Starting X Server with XGL
Using Display 1
Using WM: xfce
Using Card: nvidia/other

Fatal server error:
no GLX visuals available

Starting Compiz
Starting Window Manager
/usr/bin/startxgl-xfce: line 45: gnome-window-decorator: command not found
/usr/bin/compiz: Couldn't open display :1

(xfce4-session:5947): Gtk-WARNING **: cannot open display:

Isn't gnome-window-decorator part of compiz-gnome?

**Edit:** Oh I get it, you used aptitude to install compiz and  compiz-gnome probably is one of the recommended packages so aptitude will automatically install that. I guess I'll have to get that too then...

---

### Post by blakesmith on 2006-09-20
> **s0undt3ch said:**
> This worked for me, but I get a 800x600(desktop) on a 1280x1024 resolution on the top left of my screen!

How do I solve that part?

I have the exact same problem.

Nvidia GeForce4 MX 440 SE (128mb)

---

### Post by Vinze on 2006-09-21
> **blakesmith said:**
> I have the exact same problem.

Nvidia GeForce4 MX 440 SE (128mb)

Must've missed that post, I got the same problem! Finally, I couldn't find anyone else with this problem or a solution! If still you happen to find anything, please tell me, cause it's the only problem that keeps me from using it!

---

### Post by nwgray on 2006-09-21
I have the same problem on Geforce MX440 (64MBB) - small desktop in the upper left corner and the light-blue startup background over the rest of the screen. The compiz does work though albeit smaller. When I opened the desktop settings, no screen resolution was listed, just "Default". Should the resolution be specified somewhere? When I log back into my regular XFCE4 session, I have 1280x1024, 800x600, and 640x480.

Thx

---

### Post by Vinze on 2006-09-21
> **nwgray said:**
> I have the same problem on Geforce MX440 (64MBB) - small desktop in the upper left corner and the light-blue startup background over the rest of the screen. The compiz does work though albeit smaller. When I opened the desktop settings, no screen resolution was listed, just "Default". Should the resolution be specified somewhere? When I log back into my regular XFCE4 session, I have 1280x1024, 800x600, and 640x480.

Thx

No, default is just 1024x768, at least with me. That's also the case in normal Xfce.

---

### Post by mee.six on 2006-10-11
Oh... did anybody cope with the problem of "small screen inside 1280x1024"? :)

---

### Post by nwgray on 2006-10-12
I just tried it again on a fresh Xubuntu install - same problem. Screen in upper left has compiz and xgl running fine. The rest of the screen is light blue.

---

### Post by mee.six on 2006-10-12
The same with me :( 
but when I saw XGL Demo video first time, that guy used it with Xfce, so... I think it's possible..
(but noone knows how :()

---

### Post by krisbowen on 2006-10-12
Itried alot of these on my Laptop last night.
I keep getting libgl1-mesa not found

anyone got any ideas on this one??

---

### Post by Vinze on 2006-10-13
> **mee.six said:**
> The same with me :( 
but when I saw XGL Demo video first time, that guy used it with Xfce, so... I think it's possible..
(but noone knows how :()

I managed to, I uploaded a video to Google Video if you want to see it :D

Anyway, I used the second howto [here](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome),  though in startxgl.sh I used the following:
```
#!/bin/sh
# Start up Xgl and Xfce
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Xfce
exec xfce4-session
```
Instead of what he mentions there.

---

### Post by mee.six on 2006-10-14
rewriting this post 3d time...


**Thanks a lot!** it worked! :) 
I'm not sure, if this how-to hepled, or new architecture specific kernel, but now everything's great.


except keyboard. Somehow, shift+bkspace kills X :( does anybody know how to fix that? That's the reason of 3d try to write this post... I simply enter "shift+bkspace" to delete a word...and my X restarts :(


anyway, thanks a lot for you help :) xgl rules :)))

---

### Post by Vinze on 2006-10-14
> **mee.six said:**
> rewriting this post 3d time...


**Thanks a lot!** it worked! :) 
I'm not sure, if this how-to hepled, or new architecture specific kernel, but now everything's great.


except keyboard. Somehow, shift+bkspace kills X :( does anybody know how to fix that? That's the reason of 3d try to write this post... I simply enter "shift+bkspace" to delete a word...and my X restarts :(


anyway, thanks a lot for you help :) xgl rules :)))

Unfortunately, I got the same problem... 

**Edit:** I found a thread concerning this, I'll read it now :mrgreen:

**Edit:** OK, this command should do it, replace nl with your country code (e.g. us): ```
xmodmap /usr/share/xmodmap/xmodmap.nl
```
Found [here](http://ubuntuforums.org/showthread.php?t=179004&highlight=shift+backspace+x+server#postcount1031224).

But he also mentioned if you use a startup script you can add it to that, in our case startxgl.sh, like this:
```
$ sudo mousepad /usr/bin/startxgl.sh
```
Then add to it:
```
cgwd & compiz --replace gconf miniwin decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &
```

---

### Post by mee.six on 2006-10-14
can you give me this link too? :))

---

### Post by Vinze on 2006-10-14
> **mee.six said:**
> can you give me this link too? :))

See my previous post, and let me know if it worked because I'm not at my home computer right now.

---

### Post by mee.six on 2006-10-15
no way, i don't have /usr/share/xmodmap :(

---

### Post by Vinze on 2006-10-15
> **mee.six said:**
> no way, i don't have /usr/share/xmodmap :(

Have you tried the code? If you did, then you might have to install xmodmap first ```
$ sudo apt-get install xmodmap
```
If you didn't, do so because I think it will create it if it doesn't exist.

---

### Post by mee.six on 2006-10-15
well... I have xmodmap installed... but I'll try to create this path (and file) by myself

---

### Post by Vinze on 2006-10-15
What do you get when you just execute ```
xmodmap /usr/share/xmodmap/xmodmap.nl
```

---

### Post by mee.six on 2006-10-15
```

unable to open file /usr/share/xmodmpa/xmodmap.nl for reading
1 error encountered, aborting

```

it's not because of permissions, here is just no such directory (and files as well :))

---

### Post by Vinze on 2006-10-15
> **mee.six said:**
> ```

unable to open file /usr/share/xmodmpa/xmodmap.nl for reading
1 error encountered, aborting

```

it's not because of permissions, here is just no such directory (and files as well :))

Right... And nl is your country code? Your profile says you're from Ukraine ;)

---

### Post by mee.six on 2006-10-15
> **Vinze said:**
> Right... And nl is your country code? Your profile says you're from Ukraine ;)

:) I don't have a xmodmap directory inside /usr/share... so there is no files :)

---

### Post by Vinze on 2006-10-15
> **mee.six said:**
> :) I don't have a xmodmap directory inside /usr/share... so there is no files :)

> unable to open file /usr/share/xmodmpa/xmodmap.nl for reading

That's typed wrong ;)

But anyway, have you already tried creating it?

---

### Post by json684 on 2006-10-23
Could any of you please tell me if I can apply this to AIGLX instead of XGL? I really like compiz, and really like XFCE, but need to use AIGLX.

---

### Post by dragomirov on 2006-11-16
> **json684 said:**
> Could any of you please tell me if I can apply this to AIGLX instead of XGL? I really like compiz, and really like XFCE, but need to use AIGLX.

So I made it!! 

First of all I run xubuntu 6.10 on a Dell Inspiron 5160 with a nVidia 5200Go using Twinview function. So my suggestion probably can't fit all of you but...
To install AIGLX I followed this guide made by Felipe [http://pollycoke.wordpress.com/2006/10/10/ubuntu-edgy-aiglx-compiz/]("http://pollycoke.wordpress.com/2006/10/10/ubuntu-edgy-aiglx-compiz/")
Really easy way.

Then I get into xfce desktop, open a terminal and run
```
killall xfwm4 && compiz-tray-icon &
```
To kill the xfce window manager (xfwm4) and substitute with compiz.
[Shot1]("http://ubuntuforums.org/gallery/showphoto.php?photo=4040")
[Shot2]("http://ubuntuforums.org/gallery/showphoto.php?photo=4041")
A pair of shots, just to make it cool ;)

---

### Post by Pogeymanz on 2008-01-10
Hey, this thread is awesome, but I think those links went bad. Can someone post fresh step-by-step instructions on getting compiz with xfce4?

---

### Post by santiagoward2000 on 2008-01-11
> **EmosSuck777 said:**
> Hey, this thread is awesome, but I think those links went bad. Can someone post fresh step-by-step instructions on getting compiz with xfce4?

Hi there!
If you're in Gusty, it's not that hard.
[LIST]
[*]First, go to **Applications/System/Restricted Drivers Manager** and install your video card's drivers.
[*]Then, go to **Applications/System/Synaptic Package Manager**, look for **compiz** in that list and install it.
[*]Install **compiz-plugins**, **compiz-fusion-plugins-main**, **compiz-fusion-plugins-extra**
[*]You should install **compizconfig-settings-manager** too, to customize it's settings.
[*]You can install **emerald** too, to use the windows decorations.
[*]If you have an ATI card you'll need to install the **xserver-xgl** package too.
[*]That should install it. To run it, press Alt+F2 and type: ```
compiz --replace
```
[*]You'll probably have to go to *Applications/Settings/Advanced Desktop Effects Settings* to enable the cube and all other options.
[/LIST]
And that's it!
I hope you find this useful.
Cheers!

---

### Post by Vinze on 2008-01-11
> **EmosSuck777 said:**
> Hey, this thread is awesome, but I think those links went bad. Can someone post fresh step-by-step instructions on getting compiz with xfce4?

Hi, I wrote [a guide for setting up Compiz on Xubuntu 7.10](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/) on my own blog.

---


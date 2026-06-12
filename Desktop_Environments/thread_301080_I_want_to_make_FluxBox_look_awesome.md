---
title: "I want to make FluxBox look awesome"
date: 2006-11-16
forum: Desktop Environments
---

### Post by Velotix on 2006-11-16
The question is, how? I'm running the milla-vanilla FluxBox WM - no customisations except the menu has been changed to stop me from being able to select a different window manager and break the system (like yesterday :-? ) and I've tried out the pre-set themes.

The principal query is: how do I set a desktop wallpaper? I know FluxBox is very heavily customisable, I'm just not sure how to do it.

---

### Post by willca on 2006-11-16
fbsetbg -l locationoffile

e.g.

fbsetbg -l /home/someuser/.fluxbox/wallpaper/mydesktop.png

HTH 
Cheers 
-W

[www.boondoons.com](www.boondoons.com)

---

### Post by kerry_s on 2006-11-16
That's a big area to cover, we'll try to knock out each ? as you ask.

"how do I set a desktop wallpaper?"

Put them in /.fluxbox/backgrounds & use this in your menu to change them with a click.->

 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]

Also you need to add to your init so it loads the last background->
session.screen0.rootCommand:
to
session.screen0.rootCommand:	fbsetbg -l


Here's my menu so you can see how i used it->

```
[begin] (Fluxbox)

[exec] (Files) {emelfm} 

[exec] (Terminal) {xvt} 
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
 [exec] (Prozilla) {xvt -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (Beep Media Player) {beep-media-player}
 [exec] (Wmix) {wmix}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-files) {gksu emelfm /}
 [exec] (Terminal-Root) {gksu xvt}
[end]

[submenu] (Settings)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {fbrun}
[exec] (Keyboard) {xvkbd -no-keypad}

[submenu] (ScreenShots)
 [exec] (Snap) {scrot %T.jpg}
 [exec] (Select) {scrot -s -b %T.jpg}
 [exec] (Wait 5) {scrot -d 5 %T.jpg}
[end]

[separator]
[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]


[separator]
[exec] (Screen Off) {/home/user/.screen-off}
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

```

---

### Post by Velotix on 2006-11-16
Thanks for that, but a more pressing concern came up in the meantime. As this can be solved simply by withdrawing the programs from the menu, I won't ask how to solve the problem, but what I will ask is **why**:

When I ran Nautilus in FluxBox, it worked fine at first, but after I closed I noticed my GNOME wallpaper had loaded (a big giveaway as to how GNOME handles the desktop) and my right-click menu had gone the way of the dodo meaning i couldn't load any programs. Checking on fluxbox.org shows that FluxBox has only partial GNOME support, so which programs are known to break FluxBox?

(I have *ubuntu-*, *kubuntu-*, *xubuntu-desktop* and *FluxBox* installed.)

---

### Post by skymt on 2006-11-16
"Partial Gnome support" means only partial support for using Fluxbox as a replacement for Metacity in the Gnome desktop environment. All Gnome applications should work well in Fluxbox.

To use Nautilus in Fluxbox without it taking over your desktop, add the --no-desktop flag:```
[exec] (Nautilus) {nautilus --no-desktop}
```

---

### Post by paul6 on 2006-11-16
Hey kerry_s can you explain this segment of code:

```

[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]
```

I know this is some sort of menu generator, but I can't get it to work. Thanks.

---

### Post by kerry_s on 2006-11-16
> **paul6 said:**
> Hey kerry_s can you explain this segment of code:

```

[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]
```

I know this is some sort of menu generator, but I can't get it to work. Thanks.

It updates the debian-menu(stock-menu). You just click on Update-menus and then the fluxbox restart and any new app's you installed/removed will adjust.

---

### Post by yabbadabbadont on 2006-11-16
Here are some fluxbox related links that you might find useful:

[http://www.fluxbox.org/](http://www.fluxbox.org/)
[http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)
[http://www.boxwhore.org/modules/news/](http://www.boxwhore.org/modules/news/)
[http://themes.freshmeat.net/browse/962/?topic_id=962](http://themes.freshmeat.net/browse/962/?topic_id=962)
[http://www.tenr.de/](http://www.tenr.de/)
[http://www.dugnet.org/klown/wallpaper/](http://www.dugnet.org/klown/wallpaper/)
[http://www.customize.org/list/fluxbox](http://www.customize.org/list/fluxbox)

---

### Post by paul6 on 2006-11-16
> **kerry_s said:**
> It updates the debian-menu(stock-menu). You just click on Update-menus and then the fluxbox restart and any new app's you installed/removed will adjust.

The problem is, update-menus is not creating a ~/.fluxbox/fluxbox-menu file for me. I browsed there with Nautilus and no such file existed, even after running update-menus multiple times. ](*,)

[Edit] Here is what it looks like from the command line:

```
paul@ubuntu:~$ update-menus -v
update-menus[4006]: Update-menus is run by user.
update-menus[4006]: Dpkg is not locking dpkg status area, good.
update-menus[4006]: Reading installed packages list...
update-menus[4006]: Reading menu-entry files in /home/paul/.menu/.
update-menus[4006]: 0 menu entries found (0 total).
update-menus[4006]: Reading menu-entry files in /etc/menu/.
update-menus[4006]: 0 menu entries found (0 total).
update-menus[4006]: Reading menu-entry files in /usr/lib/menu/.
update-menus[4006]: 2 menu entries found (2 total).
update-menus[4006]: Reading menu-entry files in /usr/share/menu/.
update-menus[4006]: 162 menu entries found (164 total).
update-menus[4006]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[4006]: 0 menu entries found (164 total).
update-menus[4006]: Running menu-methods in /home/paul/.menu-methods/.
update-menus[4006]: Running menu-methods in /etc/menu-methods/.
update-menus[4006]: Running method: /etc/menu-methods/gnome-panel-data
paul@ubuntu:~$ 

```

---

### Post by kerry_s on 2006-11-16
Check to see that you have menu & menu-xdg installed. Other than that it should just work.

---

### Post by yabbadabbadont on 2006-11-17
I think the Ubuntu install of fluxbox defaults to including the menu from /etc/X11/????  (fluxbox maybe, I build it from SVN so I'm not sure).  I believe that you need to use sudo so that update-menus is updating the global menu setup and not your personal one.  (since flux is probably configured to use the global one)

If you run "grep menu ~/.fluxbox/init" from where does it say it is getting your menu?

---

### Post by kerry_s on 2006-11-17
Once you do update-menus it should create the fluxbox-menu & menudefs.hook. But if it's not creating it you can copy the ones in /etc/X11/fluxbox to your ~/.fluxbox. Can you post a copy of your menu?

---

### Post by paul6 on 2006-11-17
> **kerry_s said:**
> Check to see that you have menu & menu-xdg installed. Other than that it should just work.

They weren't installed. But I just installed them just a second ago and it  still isn't working. I think the problem may be that I originally installed fluxbox from source instead of using apt-get, so my fluxbox functions slightly different.

> **yabbadabbadont said:**
> I think the Ubuntu install of fluxbox defaults to including the menu from /etc/X11/????  (fluxbox maybe, I build it from SVN so I'm not sure).  I believe that you need to use sudo so that update-menus is updating the global menu setup and not your personal one.  (since flux is probably configured to use the global one)

If you run "grep menu ~/.fluxbox/init" from where does it say it is getting your menu?

I think you are right, it is an update-menus problem. Here is what happened when I ran the command:

```
paul@ubuntu:~$ grep menu ~/.fluxbox/init
session.screen0.menu.alpha:     255
session.screen0.menuDelayClose: 0
session.screen0.menuDelay:      0
session.screen0.menuMode:       Delay
session.menuFile:       ~/.fluxbox/menu
paul@ubuntu:~$ 

```


> **kerry_s said:**
> Once you do update-menus it should create the fluxbox-menu & menudefs.hook. But if it's not creating it you can copy the ones in /etc/X11/fluxbox to your ~/.fluxbox. Can you post a copy of your menu?

For some reason I do not have an /etc/X11/fluxbox folder. The source version must have a different setup. But here is my menu:

```
# Generated by fluxbox-generate_menu
#
# If you read this it means you want to edit this file manually, so here
# are some useful tips:
#
# - You can add your own menu-entries to ~/.fluxbox/usermenu
#
# - If you miss apps please let me know and I will add them for the next
#   release.
#
# - The -r option prevents removing of empty menu entries and lines which
#   makes things much more readable.
#
# - To prevent any other app from overwriting your menu
#   you can change the menu name in .fluxbox/init to:
#     session.menuFile: /home/you/.fluxbox/my-menu

[begin] (Fluxbox-1.0rc2)

      [exec] (Thunar) {thunar}
      [exec] (Xfce4-terminal) {xfce4-terminal}
      [exec] (Swiftfox) {swiftfox}
      [exec] (Password Safe) {wine "/home/paul/Password Safe/Password Safe.exe"}
      [exec] (Banshee) {banshee}
      [exec] (Audacity) {audacity}
      [exec] (Easytag) {easytag}
      [submenu] (Other)
        [exec] (Nautilus) {nautilus --no-desktop}
        [exec] (Nautilus - root) {gksudo "nautilus --no-desktop /home/paul"}
        [exec] (Bibletime) {bibletime}
        [exec] (Xmms) {xmms}
        [exec] (Gaim) {gaim}
        #[exec] (Gedit) {gedit}
        [exec] (Leafpad) {leafpad}
        #[exec] (Cream) {cream}
        [exec] (Abiword) {abiword}
        [exec] (GRAMPS) {gramps}
        #[exec] (Bonager) {gksudo bonager}
        [exec] (Abcde) {xfce4-terminal -e "abcde -V"}
        #[exec] (Sound Juicer) {sound-juicer}
        #[exec] (Ripperx) {ripperx}
        [exec] (Realplayer) {realplay}
        [end]
      [submenu] (Wine)
        [exec] (uTorrent) {wine "/home/paul/other/utorrent.exe"}
        [exec] (EAC) {wine ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy/EAC.exe}
        [end]
      [submenu] (KDE)
        [exec] (Kate) {kate}
        [exec] (Konqueror) {konqueror}
        [exec] (Krusader) {krusader}
        [exec] (Kopete) {kopete}
        [exec] (DigiKam) {digikam}
        [end]

[submenu] (Debian-menu)
 [exec] (Update-menus) {update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]

[separator]

[submenu] (Settings)
   [submenu] (Backgrounds)
      [wallpapers] (/usr/share/fluxbox/backgrounds)
      [wallpapers] (~/.fluxbox/backgrounds)
      [end]
   [submenu] (Styles)
      [stylesdir] (/usr/local/share/fluxbox/styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
      [end]
   [config] (Configuration)
   [workspaces] (Workspace List)
   [commanddialog] (Fluxbox Command)
   [exec] (Window name) {xprop WM_CLASS|cut -d \" -f 2|xmessage -file - -center}
   [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center}
   #[reconfig] (Reload config)
   [restart] (Restart)
   [end]
[submenu] (ScreenShots)
   [exec] (Snap) {scrot %m-%d-%y\ %H:%M.jpg}
   [exec] (Select) {scrot -s -b %m-%d-%y\ %H:%M.jpg}
   [exec] (Wait 5) {scrot -d 5 %m-%d-%y\ %H:%M.jpg}
   [end]
[submenu] (Edit Fluxbox...)
  [exec] (Menu) {leafpad /home/paul/.fluxbox/menu}
  [exec] (Startup) {leafpad /home/paul/.fluxbox/startup}
  [exec] (Keys) {leafpad /home/paul/.fluxbox/keys}
  [exec] (Init) {leafpad /home/paul/.fluxbox/init}
  [exec] (Apps) {leafpad /home/paul/.fluxbox/apps}
  [exec] (Slitlist) {leafpad /home/paul/.fluxbox/slitlist}
  [end]
[submenu] (GUI configs)
  [exec] (Fluxkeys) {fluxkeys}
  [exec] (Fluxconf) {fluxconf}
  [exec] (Fluxmenu) {fluxmenu}
  [end]
[submenu] (Ubuntu)
  [exec] (Apt Sources) {gksudo "leafpad /etc/apt/sources.list"}
  [exec] (Grub menu) {gksudo "leafpad /boot/grub/menu.lst"}
  [exec] (Abcde conf) {leafpad ~/.abcde.conf}
  [end]

[separator]

[exit] (Logout)
[exec] (Reboot) {gksudo reboot}
[exec] (Shutdown) {gksudo "shutdown -h now"}

[end]
```

Next time I'll definetely use apt-get ](*,) By the way, would you mind posting your keys file, kerry_s? I like your fluxbox ideas (notice I stole some of your menu code and put it in mine :p ), and I wouldn't mind taking a look at your key setup. :D

---

### Post by kerry_s on 2006-11-17
Try typing in terminal->
sudo updatedb
locate fluxbox-menu

My keys->

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :ExecCommand fbrun
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
None F13 :ExecCommand scrot %T.jpg
Mod1 f :ExecCommand firefox
Mod1 g :ExecCommand gaim
Mod1 d :ExecCommand dillo
Mod1 e :ExecCommand emelfm
Mod1 x :ExecCommand xvt
Mod1 s :ExecCommand gksu synaptic


For F13 (print) you have to use a xmod, from my startup->
xmodmap -e "keycode 111 = F13" &

The mod1 key is alt.

---

### Post by paul6 on 2006-11-17
> **kerry_s said:**
> Try typing in terminal->
sudo updatedb
locate fluxbox-menu

It didn't find it. :(  I think I'll just give up on the Debian menu, it's not like I need it that much anyway. :) 

> For F13 (print) you have to use a xmod, from my startup->
xmodmap -e "keycode 111 = F13" &

The mod1 key is alt.

After testing it out, I think *you can* use "Print" instead of mapping F13. 
"None Print :ExecCommand scrot %T.jpg" seems to work. 

What theme are you using?

---

### Post by kerry_s on 2006-11-17
> What theme are you using?

It's a theme from when i used DSL linux, i think it was called fizzure something. I just named it BlueSilver cause those are the colors.Here->


toolbar:			raised gradient vertical
toolbar.color:			#fefefe
toolbar.colorTo:		#a6a6a6
toolbar.justify:		center
toolbar.textcolor:		#000000
toolbar.roundCorners:					TopRight TopLeft BottomRight BottomLeft
toolbar.button:			raised gradient vertical
toolbar.button.color:		#fefefe
toolbar.button.colorTo:		#a6a6a6
toolbar.button.picColor:	#000000
toolbar.button.pressed:		sunken gradient diagonal
toolbar.button.pressed.color:	#a6a6a6
toolbar.button.pressed.colorTo:	#fefefe
toolbar.shaped:						TRUE
toolbar.clock:			sunken gradient vertical
toolbar.clock.color:		#4184de
toolbar.clock.colorTo:		#2152c5
toolbar.clock.textColor:	#fefefe

toolbar.label:			sunken gradient vertical
toolbar.label.color:		#4184de
toolbar.label.colorTo:		#2152c5
toolbar.label.textColor:	#fefefe

toolbar.windowLabel:		sunken gradient vertical
toolbar.windowLabel.color:	#4184de
toolbar.windowLabel.colorTo:	#2152c5
toolbar.windowLabel.textColor:	#fefefe

menu.title:			sunken gradient vertical
menu.title.color:		#4184de
menu.title.colorTo:		#2152c5
menu.title.textColor:		#fefefe
menu.title.justify:		center

menu.frame:			raised gradient vertical
menu.frame.color:		#fefefe
menu.frame.colorTo:		#a6a6a6
menu.frame.textColor:		#000000
menu.frame.justify:		center

menu.hilite:			sunken gradient vertical
menu.hilite.color:		#4184de
menu.hilite.colorTo:		#2152c5
menu.hilite.textColor:		#fefefe
menu.roundCorners:					TopRight TopLeft BottomRight BottomLeft
menu.bullet:			triangle
menu.bullet.position:		right

window.justify:			center

window.title.focus:		raised gradient vertical
window.title.focus.color:	#fefefe
window.title.focus.colorTo:	#a6a6a6
window.title.unfocus:		raised gradient vertical
window.title.unfocus.color:	#fefefe
window.title.unfocus.colorTo:	#a6a6a6

window.label.focus:		sunken gradient vertical
window.label.focus.color:	#4184de
window.label.focus.colorTo:	#2152c5
window.label.focus.textColor:	#fefefe
window.label.unfocus:		parentrelative
window.label.unfocus.color:	#fefefe
window.label.unfocus.colorTo:	#a6a6a6
window.label.unfocus.textColor:	#000000

window.button.focus:		raised gradient vertical
window.button.focus.color:	#fefefe
window.button.focus.colorTo:	#a6a6a6
window.button.focus.picColor:	#000000
window.button.unfocus:		raised gradient vertical
window.button.unfocus.color:	#fefefe
window.button.unfocus.colorTo:	#a6a6a6
window.button.unfocus.picColor:	#000000
window.button.pressed:		sunken gradient diagonal
window.button.pressed.color:	#a6a6a6
window.button.pressed.colorTo:	#fefefe

window.frame.focusColor:	#a6a6a6	
window.frame.unfocusColor:	#a6a6a6

window.handle.focus:		raised gradient vertical
window.handle.focus.color:	#fefefe
window.handle.focus.colorTo:	#a6a6a6
window.handle.unfocus:		raised gradient vertical
window.handle.unfocus.color:	#fefefe
window.handle.unfocus.colorTo:	#a6a6a6

window.grip.focus:		sunken gradient vertical
window.grip.focus.color:	#4184de
window.grip.focus.colorTo:	#2152c5
window.grip.unfocus:		raised gradient vertical
window.grip.unfocus.color:	#fefefe
window.grip.unfocus.colorTo:	#a6a6a6

borderColor:			#a6a6a6

bevelWidth:			2
borderWidth:			1
handleWidth:			5
window.roundCorners:					TopRight TopLeft BottomRight BottomLeft
*Font:                          sans-12

---

### Post by kerry_s on 2006-11-17
> After testing it out, I think you can use "Print" instead of mapping F13.
"None Print :ExecCommand scrot %T.jpg" seems to work.


Hey thanks for that, it works, i think that's what i used a long time ago, but when i changed keyboards it stopped working and i started using the mod. I been doing it so long already, i never bothered changing.LOL :rolleyes:

---


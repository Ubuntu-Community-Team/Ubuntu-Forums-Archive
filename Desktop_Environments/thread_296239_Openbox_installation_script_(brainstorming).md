---
title: "Openbox installation script (brainstorming)"
date: 2006-11-09
forum: Desktop Environments
---

### Post by raublekick on 2006-11-09
I kinda want to get back into Openbox, it's been a while since I used it. But I don't want to just install and configure it the old fashioned way. So I decided that I want to make an installation that will take an Edgy server install and add everything a user needs to get X, Openbox, menus, a panel, and apps. Also some of these will be preconfigured to something decent. 


I've been browsing as many how-to's as I can to get info on what people want as well as some tips 'n' tricks. So here is the list of things that so far I am tossing around:


Display Manager:
GDM or XDM

Panel:
Pypanel

Desktop:
idesk, feh

Text editor:
Gedit or Mousepad, emacs

Terminal:
aterm or xfce4-terminal

Web Browser:
Firefox (sigh... I really wish there were a good replacement cus FF isn't really all that snappy on my system)

Media players:
gxine or totem-xine, xmms

File Manager:
thunar

Sensors:
conky

System software:
gnome-volume-manager, gtk-theme-switch2, menumaker, obconf, obtuner

Office stuff:
Gimp, OpenOffice or Gnome Office or Abiword/Gnumeric

Other:
??? (Stuff like Gnome / XFCE settings apps)



Please add your own suggestions, comments, concerns, questions, etc. One thing I am trying to figure out right now (without using Openbox at the moment) is how one could use a weather panel applet like the ones in XFCE or Gnome without using their panels. 

I am also toying around the idea of adding multimedia codecs, but I think I might just make them an option. 

Basically I just want to make a full Openbox system, so tell me what you would like to see!


No ETA on this by the way, as I am pretty busy with the end of the semester drawing near :)

<edit> I also would like to add some usefull laptop stuff, like a battery monitor, but that kinda goes along with the weather applet issue.

---

### Post by justin whitaker on 2006-11-09
The only thing really missing is some type of office suite (Gnome Office? Open Office?),GIMP, and Mplayer. I pretty much consider those a must on any install.

---

### Post by raublekick on 2006-11-09
good suggestions, i keep forgetting about things! (i edited my original post twice...)

i dunno about mplayer though, i never use it and prefer gxine or totem-xine

---

### Post by fuscia on 2006-11-09
you could try either epiphany or swiftfox if you find ff too slow. i'd also suggest either balsa or sylpheed-claws for a mail client. and, i would leave off the display manager. if you're using a server installation, just think how much cooler 'startx' is.

---

### Post by justin whitaker on 2006-11-09
> **raublekick said:**
> good suggestions, i keep forgetting about things! (i edited my original post twice...)

i dunno about mplayer though, i never use it and prefer gxine or totem-xine

I was thinking about Mplayer as a firefox tie in. I find it works better for things like YouTube, GoogleVideo, etc., when browsing. 
I like it as a stand alone as well, since it can play just about everything.

---

### Post by Kindred on 2006-11-09
I would junk as much gnome stuff as possible, personally.  

I would use slim for a login manager (if you must have one), ivman in place of gnome-volume-manager (again if you must have one, thunar does an excellent job without one, displaying the volume in all the right places etc), for text editor I would use leafpad, for media player I would actually use mplayer but gxine is okay.

For configuring openbox i'd additionally look at nitrogen for wallpaper, and for gtk gtk-chtheme (I never used gtk-theme-switch2, not sure which is best actually).

Usually because i'm using thunar anyway I use the Terminal from xfce and xfce4-panel because I like it, but urxvt is always good, never really  been into pypanel but yeah it's pretty popular.

Sylpheed & Sylpheed-Claws as recommended above are both excellent mail clients, fast too. 

For pdf's I use epdfview (gtk, no gnome deps), calculator is galculator, burning is graveman, irc is irssi.. xchat works.. etc etc.  I have about 2 gnome libs installed....

---

### Post by raublekick on 2006-11-09
> **fuscia said:**
> you could try either epiphany or swiftfox if you find ff too slow. i'd also suggest either balsa or sylpheed-claws for a mail client. and, i would leave off the display manager. if you're using a server installation, just think how much cooler 'startx' is.

well, i want to make this pretty user friendly, so i definitely want a display manager. i will check out those email clients.

---

### Post by raublekick on 2006-11-09
> **Kindred said:**
> I would junk as much gnome stuff as possible, personally.  

I would use slim for a login manager (if you must have one), ivman in place of gnome-volume-manager (again if you must have one, thunar does an excellent job without one, displaying the volume in all the right places etc), for text editor I would use leafpad, for media player I would actually use mplayer but gxine is okay.

For configuring openbox i'd additionally look at nitrogen for wallpaper, and for gtk gtk-chtheme (I never used gtk-theme-switch2, not sure which is best actually).

Usually because i'm using thunar anyway I use the Terminal from xfce and xfce4-panel because I like it, but urxvt is always good, never really  been into pypanel but yeah it's pretty popular.

Sylpheed & Sylpheed-Claws as recommended above are both excellent mail clients, fast too. 

For pdf's I use epdfview (gtk, no gnome deps), calculator is galculator, burning is graveman, irc is irssi.. xchat works.. etc etc.  I have about 2 gnome libs installed....



excellent, excellent, excellent! thank you so much for those suggestions. isn't ivman what KDE uses? i thought i saw that somewhere and i guess i assumed it was riddled with KDE libs (which I want as much as gnome libs)

---

### Post by justin whitaker on 2006-11-09
How hung up are you/we on GUI apps? Because bashburn would be a good alternative to graveman.

---

### Post by raublekick on 2006-11-09
> **justin whitaker said:**
> How hung up are you/we on GUI apps? Because bashburn would be a good alternative to graveman.

here is my real goal for this, sorry i didn't really explain it well earlier:

i want to make somewhat of an intermediate step between xubuntu and, well, a server install. i don't want to get riddled down with lots of extra crap, but i do want to get it as fully GUI featured as possible without losing the focus of the project.

---

### Post by bonzodog on 2006-11-09
hrm...I will have to Push JP to release uwd for other linux distros. 
Uwd is like ivman/gnome-volume-manager, but was written specially for Zenwalk Linux (which openbox is very cool on!)

---

### Post by K.Mandla on 2006-11-09
> **raublekick said:**
> Display Manager:
GDM or XDM
I dropped all my DMs and use the tty login. Editing .bash_profile starts X automatically for me.

> **raublekick said:**
> Panel:
Pypanel
I tried going without a taskbar for a while, and I prefer it now. It's like working on a picture.

> **raublekick said:**
> Desktop:
idesk, feh
I think iDesk can manage desktop wallpaper, but I've never taken the time to figure it out. It would eliminate my need for feh, though.

> **raublekick said:**
> Text editor:
Gedit or Mousepad, emacs
Mousepad for me. Leafpad is good too. nedit is to ugly for my taste.

> **raublekick said:**
> Terminal:
aterm or xfce4-terminal
I'm all about the transparent borderless terminal window. xfce4-terminal for me.

> **raublekick said:**
> Web Browser:
Firefox (sigh... I really wish there were a good replacement cus FF isn't really all that snappy on my system)
Have you tried Iceweasel? It works great for me.

> **raublekick said:**
> Media players:
gxine or totem-xine, xmms
I'm an mplayer fan. I get real kick out of watching movies through the aalib option.

> **raublekick said:**
> File Manager:
thunar
I've moved to XFE, although it's a little bit ugly.

> **raublekick said:**
> Sensors:
conky
Yup. There is none higher.

> **raublekick said:**
> System software:
gnome-volume-manager, gtk-theme-switch2, menumaker, obconf, obtuner
Yup. Although I don't bother with gnome-volume-manager. I also like ObMenu over menumaker, et al. It's a little more intuitive, although it requires Python.

> **raublekick said:**
> Office stuff:
Gimp, OpenOffice or Gnome Office or Abiword/Gnumeric
Gimp-Abiword-Gnumeric is usually good enough for me.

:D

---

### Post by kerry_s on 2006-11-09
Are you going for size? I moved back to fluxbox but this is what i'm using.-> 

login= gdm
panel= xfce4-panel, it comes with thunar so i used it.
desktop= eterm, uses fbsetbg
editor= leafpad, it's the same as mousepad but smaller
terminal= xterm and eterm, xterm most of the time
web browser= firefox & dillo, i use dillo for simple things
media= xmms & mplayer, you only need w32codec and you can watch & hear 99% of stuff.
file manager= thunar, the custom actions makes even better

okay i'm tired of typing

[begin] (Fluxbox)

[exec] (Thunar) {Thunar} 

[submenu] (Terminals)
 [exec] (Xterm) {xterm} 
 [exec] (Eterm) {Eterm --borderless --buttonbar 0 --trans --shade 0 --scrollbar false}
[end]
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
 [exec] (Prozilla) { xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (XMMS) {xmms}
 [exec] (Mplayer) {gmplayer}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Thunar) {gksu Thunar /}
 [exec] (Terminal-Root) {gksu Eterm}
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
[submenu] (ScreenShots)
 [exec] (snap) {scrot %T.jpg}
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


# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (Fluxbox)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

   [submenu] (Apps) {}
      [submenu] (Editors) {}
         [exec] (LeafPad) {/usr/bin/leafpad} </usr/share/pixmaps/leafpad.xpm>
         [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} </usr/share/nano/nano-menu.xpm>
      [end]
      [submenu] (Net) {}
         [exec] (Dillo) {/usr/bin/dillo} <>
         [exec] (Firefox Web Browser) {firefox} </usr/share/pixmaps/firefox.xpm>
         [exec] (Gaim) {/usr/bin/gaim} </usr/share/pixmaps/gaim-menu.xpm>
         [exec] (Prozilla) { x-terminal-emulator -T "Prozilla" -e /usr/bin/dproz} </usr/share/pixmaps/prozilla.xpm>
      [end]
      [submenu] (Programming) {}
         [exec] (Python (v2.4\)) { x-terminal-emulator -T "Python (v2.4)" -e /usr/bin/python2.4} </usr/share/pixmaps/python2.4.xpm>
      [end]
      [submenu] (Shells) {}
         [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login} <>
         [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i} <>
         [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login} <>
      [end]
      [submenu] (Sound) {}
         [exec] (wmXMMS) {/usr/bin/wmxmms} </usr/share/pixmaps/wmxmms_32.xpm>
         [exec] (XMMS) {/usr/bin/xmms} </usr/share/pixmaps/xmms.xpm>
      [end]
      [submenu] (System) {}
         [submenu] (Admin) {}
            [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
         [end]
         [exec] (GDM flexiserver) {gdmflexiserver} </usr/share/pixmaps/gdm.xpm>
         [exec] (GDM flexiserver in Xnest) {gdmflexiserver -n} </usr/share/pixmaps/gdm.xpm>
         [exec] (GDM Photo Setup) {gdmphotosetup} </usr/share/pixmaps/gdm.xpm>
         [exec] (GDM Setup) {gksu gdmsetup} </usr/share/pixmaps/gdm.xpm>
         [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} </usr/share/pixmaps/pstree16.xpm>
         [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} </usr/share/synaptic/pixmaps/synaptic_32x32.xpm>
         [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
         [exec] (xkbd) {/usr/bin/xkbd} <>
         [exec] (xkbd (in monolaunch\)) {/usr/bin/monolaunch -k /usr/share/xkbd/img/kbd.xpmp xkbd /usr/bin/xkbd} <>
         [exec] (X-Terminal as root (GKsu\)) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator} </usr/share/pixmaps/gksu-debian.xpm>
      [end]
      [submenu] (Tools) {}
         [exec] (Conky) { x-terminal-emulator -T "Conky" -e /usr/bin/conky} <>
         [exec] (xvkbd) {/usr/bin/xvkbd} <>
      [end]
      [submenu] (Viewers) {}
         [exec] (Xpdf) {/usr/bin/xpdf} </usr/share/pixmaps/xpdf.xpm>
         [exec] (xzgv Image Viewer) {/usr/bin/xzgv} </usr/share/pixmaps/xzgv.xpm>
      [end]
   [end]
   [submenu] (Help) {}
      [exec] (Info) { x-terminal-emulator -T "Info" -e info} <>
   [end]
   [submenu] (WindowManagers) {}
      [restart] (FluxBox)  {/usr/bin/startfluxbox}
   [end]
   [submenu] (XShells) {}
      [exec] (Eterm) {/usr/bin/Eterm} <>
      [exec] (XTerm) {xterm} <>
      [exec] (XTerm (Unicode\)) {uxterm} <>
   [end]

   [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces)
   [reconfig] (Reconfigure)
   [restart] (Restart)
   [exit] (Exit)

[end]

pics->

---

### Post by skymt on 2006-11-09
For a really lightweight terminal, have you looked into rxvt-unicode? It has anti-aliasing, transparency, and all the standard terminal eye candy, but unlike the rest, it loads *instantly*.

For a file manager, I prefer Rox, but Thunar is nice too. If you choose Rox, you won't need a separate program to handle the desktop (picture and icons).

Pypanel is really, really bad. By bad, I mean unfriendly. I'd go with xfce4-panel, personally.

---

### Post by raublekick on 2006-11-09
yes i am gonna be testing tons of stuff out over the next few weeks to really decide what i want to add in here. 

as far as rox and thunar go, i think thunar is a much better file manager, but rox has the desktop stuff with it too (i just really, really hate rox as a filemanger) so i don't know which i will choose.

---

### Post by K.Mandla on 2006-12-29
Did you ever decide on any of this?

---

### Post by raublekick on 2006-12-29
> **K.Mandla said:**
> Did you ever decide on any of this?

nope, my winter break became much, much busier than i anticipated...

i did just get an old 700MHz machine from my grandparents though, so perhaps I should work on it!

---

### Post by ynnhoj on 2007-01-06
yes, you should work on this rauble.

i was thinking yesterday that i'd like to fiddle with openbox again, and today i stumbled upon this thread while doing some searches.. i was hoping you had already finished off the installation script :(


..so get to work already!

---

### Post by ynnhoj on 2007-01-07
one thing you've left open in your list of apps (unless i'm not looking close enough..) is an im program; i'd probably go with gaim.  i would be able to get away with amsn, i'm sure, because i hardly ever log on to aim anymore, but i really don't like amsn, so it'd be gaim for me.

how about a torrent app?  i'm fond of rtorrent, but i suppose you'd prefer something with a gui. :-#

also, if you end up using xdm, here's something in the gentoo wiki that could be useful: [xdm login screen customization](http://gentoo-wiki.com/TIP_XDM_Login_Screen_Customization).

---

### Post by Extreme Coder on 2007-01-14
Hey Rauble,
Why not use perlpanel instead of pypanel?It's MUCH better, it has a gui customization dialog, and it works better with openbox anyway.
And, if you really want something like Thunar, use PCManFM. Looks very much like Thunar, but without the Xfce bindings. And it puts the icons of the Desktop folder on the Desktop, and a bg too :D
Let me know how this script works out :D

---

### Post by raublekick on 2007-01-15
thanks for the suggestions, dudes. 

ynnhoj, yeah i noticed you don't get on aim much!

---


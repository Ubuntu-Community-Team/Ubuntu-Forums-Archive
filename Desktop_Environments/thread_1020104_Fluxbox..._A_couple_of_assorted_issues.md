---
title: "Fluxbox... A couple of assorted issues"
date: 2008-12-23
forum: Desktop Environments
---

### Post by Wisp558 on 2008-12-23
Well, I'm trying to use Fluxbox as my secondary window manager, for use with gaming, as it tends to have much less overhead then GNOME, KDE, or even XFCE. So I have it installed, running, and using almost no resources. Great. I even have icons, now that I have fbdesk installed. I have even installed feh and gotten transparency. I have one or two questions about fluxbox, and a suggestion. Questions first!

1)As I got my icons working, I made my firefox icon's picture the firefox icon from /usr/share/pixmaps. However, it (the icon) is far too big. How may I get my icons to all stay a standard size?

2)I can set my background using fbsetbg -f /wallpaperfile It works great, even. However, how can I get the change to stick through sessions? --solved

3) How can I set commands to run at login? --solved

4) I use wicd as my net manager. Do I have to run wicd-client to get it started, or will it run invisibly on startup? --solved

5)I need a good way to edit the menu. To this end I have fme installed. Great! I can add things to the menu. However, the first entry is an include file, to include the default menu. That menu file has a big fat [DO NOT EDIT] sign on it. How can I change my menus without breaking them?

6) What is the keyboard command (if any) to change workspaces? -- solved

7) How might I display system usage statistics on my desktop??? --solved


Whew! I do like fluxbox a lot, from what I've seen! I hope I can get some closure for these issues and continue on with my super light desktop. After all, if I wanted that, I could have installed Vista, no?


And as for my suggestion, maybe we could have a flux n00b guide stickied to the top of the the Desktop Environment page! To help the others like me who aren't linux gurus but still want a speedy and responsive environment. =)

Even if you only have guesses or half-formed ideas, I'd still like to hear them!

Thanks in advance, 
~Wisp

---

### Post by eriqjaffe on 2008-12-23
> **Wisp558 said:**
> 2)I can set my background using fbsetbg -f /wallpaperfile It works great, even. However, how can I get the change to stick through sessions?

3) How can I set commands to run at login?[http://fluxbox-wiki.org/index.php?title=Editing_the_startup_file](http://fluxbox-wiki.org/index.php?title=Editing_the_startup_file)

There's a text file you can edit to have things run when fluxbox starts.

> **Wisp558 said:**
> 4) I use wicd as my net manager. Do I have to run wicd-client to get it started, or will it run invisibly on startup?wicd runs as a daemon.  As long as the network configuration stays the same, you should be alright without running the gui.

> **Wisp558 said:**
> 7) How might I display system usage statistics on my desktop???[Conky](http://conky.sourceforge.net/) is a good way to do that.

---

### Post by Wisp558 on 2008-12-24
Thanks, that solves 2, 3, 4, and 7...

Also, I found out about the ~/.fluxbox/keys file, so I know the answer to that one, and I have <ctrl> <alt> left/right switching workspaces...

---

### Post by Wisp558 on 2008-12-24
...bump?

---

### Post by Wisp558 on 2008-12-24
Bump.

---

### Post by .arean on 2008-12-24
> **Wisp558 said:**
> 5)I need a good way to edit the menu. To this end I have fme installed. Great! I can add things to the menu. However, the first entry is an include file, to include the default menu. That menu file has a big fat [DO NOT EDIT] sign on it. How can I change my menus without breaking them?

I find it easier to just use a text editor to edit the menu file by hand.

Open up you menu file in .fluxbox and either delete or comment out the default menu entry. Then open up the fluxbox-menu file (/etc/x11/fluxbox/fluxbox-menu) and copy/paste the items you want from there into the menu file in .fluxbox, adding submenus when needed. It's a little time consuming but pretty simple overall. You could also leave the menu file in .fluxbox alone and edit fluxbox-menu instead, but I like to leave that file alone so I can use it as a reference.

[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox) is a nice little guide to getting things set up.

Edit: Here's my menu file as an example:

```
[begin] () {} <>
    [submenu] (Accessories) {} <>
        [exec] (Calculator) {/usr/bin/gcalctool} <>
		[exec] (Character map) {/usr/bin/gucharmap} <>
        [exec] (Gedit) {gedit} <>
        [exec] (XTerm) {xterm -foreground dimgray -background gainsboro} <>
        [exec] (Screenshot) {gnome-screenshot --interactive} <>
    [end]
    [submenu] (Drives) {} <>
        [exec] (Home) {nautilus --no-desktop} <>
		[exec] (Storage) {nautilus /media/Storage --no-desktop}
		[exec] (Windows) {nautilus /media/Windows --no-desktop}
    [end]
    [submenu] (Flux Tools) {} <>
        [exec] (fluxconf) {/usr/bin/fluxconf} <>
        [exec] (fluxkeys) {/usr/bin/fluxkeys} <>
        [exec] (fluxmenu) {/usr/bin/fluxmenu} <>
    [end]
    [submenu] (Games) {} <>
        [exec] (ePSXe) {xterm ~/Games/epsxe/epsxe} <>
        [exec] (Gnometris) {/usr/games/gnometris} <>
        [exec] (Mahjongg) {/usr/games/mahjongg} <>
        [exec] (Solitaire) {/usr/games/sol} <>
    [end]
    [submenu] (Graphics) {} <>
        [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} <>
        [exec] (GIMP) {/usr/bin/gimp} <>
    [end]
    [submenu] (Internet) {} <>
        [exec] (Elinks) {xterm /usr/bin/elinks} <>
        [exec] (Firefox) {firefox} <>
        [exec] (Gnome ppp) {sudo /usr/bin/gnome-ppp} <>
        [exec] (Gwget) {/usr/bin/gwget} <>
        [exec] (Pidgin) {pidgin} <>
        [exec] (Transmission) {/usr/bin/transmission} <>
    [end]
    [submenu] (Office) {} <>
        [exec] (OpenOffice.org Calc) {/usr/bin/oocalc} <>
        [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} <>
        [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} <>
    [end]
    [submenu] (Sound) {} <>
        [exec] (Brasero) {/usr/bin/brasero} <>
        [exec] (Recorder) {/usr/bin/gnome-sound-recorder} <>
        [exec] (Rhythmbox) {/usr/bin/rhythmbox} <>
    [end]
    [submenu] (Styles) {} <>
        [exec] (GTK Switcher) {switch2} <>
        [stylesdir] (~/.fluxbox/styles) {} <>
    [end]
    [submenu] (System) {} <>
		[exec] (Conky) {conky} <>
        [exec] (Control Center) {/usr/bin/gnome-control-center} <>
        [exec] (Startup-Manager) {su-to-root -X -c /usr/sbin/startupmanager} <>
        [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} <>
    [end]
    [submenu] (Video) {} <>
        [exec] (Totem) {/usr/bin/totem-gstreamer} <>
        [exec] (VLC) {/usr/bin/qvlc} <>
    [end]
    [restart] (Restart) {} <>
    [exit] (Exit) {} <>
[end]
```

---


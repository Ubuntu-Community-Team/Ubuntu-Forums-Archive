---
title: "fluxbox // gnome setting manager problem"
date: 2008-08-02
forum: Desktop Environments
---

### Post by jaskah on 2008-08-02
hello

i am trying to set the keyboard layout in fluxbox by using the gnome control center / keyboard preferences (i already had the gnome desktop installed but would now like to use fluxbox).

when i try to start keyboard preferences i get the following message:

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

then keyboard preferences opens but none of the changes i make take effect.

does anyone know a solution for this?

hardy heron
lenovo t 61
fluxbox 1.0.0.3

thanks in advance for any help!

---

### Post by DocYoung on 2008-08-03
fluxbox doesnt start the gnome-settings-daemon by default. When I switched from gnome to fluxbox I lost alot of features like audio, audio controls, screen brightness controls, etc, etc. All of these worked fine in gnome. My solution was to put the gnome-settings-daemon in my startup.

This brought another problem where gnome took over the desktop. I worked around things by using the gconf-editor. Now I get the benefits of gnome settings while in fluxbox.

If you happen to try this PLEASE .... PLEASE make backups first. If not you will regret it later.


Sorry if that didnt help much but I tried ...:)

---

### Post by jaskah on 2008-08-03
hi

thanks for your reply.

> **DocYoung said:**
> fluxbox doesnt start the gnome-settings-daemon by default. When I switched from gnome to fluxbox I lost alot of features like audio, audio controls, screen brightness controls, etc, etc. All of these worked fine in gnome. My solution was to put the gnome-settings-daemon in my startup.

yes, i had this same problem. i tried to put the gnome-settings-daemon in my flux startup script but this didn't seem to make a difference.

here is my startup file, by the way:

GSDPID=`pidof gnome-settings-daemon`
if [  "x$GSDPID" == "x" ]; then
gnome-settings-daemon &
fi

# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/jason/pictures/wallpaper.png
#
# This sets a black background

/usr/bin/fbsetroot -solid black

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
# xset -b
#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp /home/jason/.fonts
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap /home/jason/.Xmodmap

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

gnome-settings-daemon &
nm-applet &
nautilus --no-desktop &
exec /usr/bin/fluxbox

# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/jason/.fluxbox/log"

> This brought another problem where gnome took over the desktop. I worked around things by using the gconf-editor. Now I get the benefits of gnome settings while in fluxbox.

can you please tell me what you did here, which way you used the gcon-editor to re-activate all these gnome settings?

> If you happen to try this PLEASE .... PLEASE make backups first. If not you will regret it later.

how are you making your back-ups?


> Sorry if that didnt help much but I tried ...:)

i appreciate your help. thanks!

---

### Post by billgoldberg on 2008-08-03
You are going to have do to it manually.

You'll have to edit xorg.conf

sudo mousepad /etc/X11/xorg.conf

*(presuming you use mousepad (I do in fluxbox), if not, change to the editor of your liking)*

In the first block of text you'll see:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"

You would change the last one to the keyboard layout you would like.

Mine is now '"be" (azerty), so change that to yours.

You can put more that one.

You could set

	Option		"XkbLayout"	"be,en"

You could then switch between layouts by using the command

```
setxkbmap be
```

or 

```
setxkbmap en
```

The first command would set your keyboard layout to azerty (be).

the second one to qwerty (us).

--

Now, you could add those commands to your menu by editing your menu file.

```
sudo mousepad /home/username/.fluxbox/menu
```

You would use the following to add those:

[exec] (azerty) {setxkbmap be}
[exec] (qwerty) {setxkbmap en}

But it would be best to add a submenu for changing keyboard layouts.

[submenu] (Layouts)
[exec] (azerty) {setxkbmap be}
[exec] (qwerty) {setxkbmap en}
[end]

Then when you right-click your desktop, a mentioning of "Layouts" will be there, with the options to load the "azerty" or "qwerty" keyboard layouts.

--

Hope this helped.

---

### Post by jaskah on 2008-08-03
hello

thanks so much for your reply. i will give this a try.

one other question: would this also solve the problem of losing all my function keys (audio controls, screen brightness controls, etc, etc.) in fluxbox, which i normally have in gnome?

---

### Post by billgoldberg on 2008-08-03
> **jaskah said:**
> hello

thanks so much for your reply. i will give this a try.

one other question: would this also solve the problem of losing all my function keys (audio controls, screen brightness controls, etc, etc.) in fluxbox, which i normally have in gnome?

No.

You can specify all your keys in /home/username/.fluxbox/keys

In my signature I have a link called "fluxbox".

It should help you setting some of your special keys.

---

### Post by billgoldberg on 2008-08-03
I made an error in my post.

"en" isn't a valid layout, it should be "us".

---

### Post by spupy on 2008-08-03
> **billgoldberg said:**
> 
You could then switch between layouts by using the command

```
setxkbmap be
```

or 

```
setxkbmap en
```

The first command would set your keyboard layout to azerty (be).

the second one to qwerty (us).
You would use the following to add those:

[exec] (azerty) {setxkbmap be}
[exec] (qwerty) {setxkbmap en}

But it would be best to add a submenu for changing keyboard layouts.

[submenu] (Layouts)
[exec] (azerty) {setxkbmap be}
[exec] (qwerty) {setxkbmap en}
[end]

Instead of a menu entry, you can have a keyboard shortcut for changing the layouts:
```
setxkbmap de,en_US ,  grp:alt_shift_toggle,grp_led:scroll
```
Put this command into your fluxbox startup file. Now you can switch layouts with Alt+Shift.

---

### Post by billgoldberg on 2008-08-03
> **spupy said:**
> Instead of a menu entry, you can have a keyboard shortcut for changing the layouts:
```
setxkbmap de,en_US ,  grp:alt_shift_toggle,grp_led:scroll
```
Put this command into your fluxbox startup file. Now you can switch layouts with Alt+Shift.

Wouldn't it make more sense to put the shortcut in the keys file?

Using 

```
Mod1 F1 :Exec setxkbmap us
Mod1 F2 :Exec setxkbmap be
```

---

### Post by jaskah on 2008-08-03
thanks so much again for your help.
i will give all this a try!

---

### Post by DocYoung on 2008-08-03
> **jaskah said:**
> hi ...

here is my menu, some of it is redundant but its still a work in progress.

```


# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (odinware)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

   [exec] (Firefox) {/usr/bin/firefox-3.0} <>
[separator]
   [exec] (mrxvt) {mrxvt} <>
[separator]
   [exec] (Amarok) {amarok} <>
[separator]
   [exec] (Thunar) {Thunar} <>
[separator]
   [submenu] (Office) {}
      [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} <>
[separator]
      [exec] (OpenOffice.org Calc) {/usr/bin/oocalc} <>
      [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} <>
      [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} <>
   [end]
[separator]
   [submenu] (Applications) {}
      [submenu] (Accessibility) {}
         [exec] (Xmag) {xmag} <>
      [end]
      [submenu] (Data Management) {}
         [exec] (Seamonkey Addressbook) {/usr/bin/seamonkey -addressbook} <>
         [exec] (Tomboy) {/usr/bin/tomboy} <>
      [end]
      [submenu] (Editors) {}
         [exec] (Gedit) {/usr/bin/gedit} <>
         [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} <>
         [exec] (Xedit) {xedit} <>
      [end]
      [submenu] (File Management) {}
         [exec] (Baobab) {/usr/bin/baobab} <>
         [exec] (Brasero) {/usr/bin/brasero} <>
         [exec] (GNOME Search Tool) {/usr/bin/gnome-search-tool} <>
         [exec] (Nautilus) {nautilus --no-desktop} <>
         [exec] (Tracker Search Tool) {/usr/bin/tracker-search-tool} <>
      [end]
      [submenu] (Graphics) {}
         [exec] (GNOME Screenshot Tool) {/usr/bin/gnome-panel-screenshot} <>
         [exec] (ImageMagick) {/usr/bin/display logo:} <>
         [exec] (Kino) {/usr/bin/kino} <>
         [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} <>
         [exec] (The GIMP) {/usr/bin/gimp} <>
         [exec] (XSane) {/usr/bin/xsane} <>
         [exec] (X Window Snapshot) {xwd | xwud} <>
      [end]
      [submenu] (Net) {}
         [exec] (X-Chat) {xchat} <>
         [exec] (Epiphany web browser (Gecko\)) {/usr/bin/epiphany-gecko} <>
         [exec] (Firefox 3 Browser) {/usr/bin/firefox-3.0} <>
         [exec] (kazehakase) {/usr/bin/kazehakase} <>
         [exec] (Netsurf Web Browser) {/usr/bin/netsurf} <>
         [exec] (Seamonkey Browser) {/usr/bin/seamonkey} <>
      [end]
      [submenu] (Network) {}
         [submenu] (Communication) {}
            [exec] (Ekiga) {/usr/bin/ekiga} <>
            [exec] (Pidgin) {/usr/bin/pidgin} <>
            [exec] (Seamonkey Mail Composer) {/usr/bin/seamonkey -compose} <>
            [exec] (Seamonkey Mail & Newsgroups) {/usr/bin/seamonkey -mail} <>
            [exec] (Terminal Server Client) {/usr/bin/tsclient -f} <>
            [exec] (Xbiff) {xbiff} <>
         [end]
         [exec] (Evolution) {/usr/bin/evolution} <>
         [submenu] (File Transfer) {}
            [exec] (Transmission BitTorrent Client) {/usr/bin/transmission} <>
         [end]
         [exec] (Telnet) { x-terminal-emulator -T "Telnet" -e /usr/bin/telnet} <>
         [exec] (w3m) { x-terminal-emulator -T "w3m" -e /usr/bin/w3m /usr/share/doc/w3m/MANUAL.html} <>
      [end]
      [submenu] (Office) {}
         [exec] (HPLIP Fax address book) {/usr/bin/hp-fab} <>
         [exec] (HPLIP Fax utility) {/usr/bin/hp-sendfax} <>
         [exec] (OpenOffice.org Calc) {/usr/bin/oocalc} <>
         [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} <>
         [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} <>
      [end]
      [submenu] (Programming) {}
         [exec] (GDB) { x-terminal-emulator -T "GDB" -e /usr/bin/gdb} <>
         [exec] (Python (v2.5\)) { x-terminal-emulator -T "Python (v2.5)" -e /usr/bin/python2.5} <>
         [exec] (Tclsh8.4) { x-terminal-emulator -T "Tclsh8.4" -e /usr/bin/tclsh8.4} <>
      [end]
      [submenu] (Science) {}
         [submenu] (Mathematics) {}
            [exec] (Bc) { x-terminal-emulator -T "Bc" -e /usr/bin/bc} <>
            [exec] (Dc) { x-terminal-emulator -T "Dc" -e /usr/bin/dc} <>
            [exec] (GCalcTool) {/usr/bin/gcalctool} <>
            [exec] (Xcalc) {xcalc} <>
         [end]
      [end]
      [submenu] (Shells) {}
         [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login} <>
         [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i} <>
         [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login} <>
      [end]
      [submenu] (Sound) {}
         [exec] (gmix (Gnome 2.0 Mixer\)) {/usr/bin/gnome-volume-control} <>
         [exec] (grecord (GNOME 2.0 Recorder\)) {/usr/bin/gnome-sound-recorder} <>
         [exec] (gtkpod) {/usr/bin/gtkpod} <>
         [exec] (Rhythmbox) {/usr/bin/rhythmbox} <>
         [exec] (Sonata) {/usr/bin/sonata} <>
         [exec] (Sound Juicer) {/usr/bin/sound-juicer} <>
         [exec] (vumeter (Gnome 2.0 Volume Meter\)) {/usr/bin/vumeter} <>
      [end]
      [submenu] (System) {}
         [submenu] (Administration) {}
            [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
            [exec] (Aptitude) { x-terminal-emulator -T "Aptitude" -e /usr/bin/aptitude} <>
            [exec] (Debian Task selector) { x-terminal-emulator -T "Debian Task selector" -e su-to-root -c tasksel} <>
            [exec] (DSL/PPPoE configuration tool) { x-terminal-emulator -T "DSL/PPPoE configuration tool" -e /usr/sbin/pppoeconf} <>
            [exec] (Editres) {editres} <>
            [exec] (GDM flexiserver) {gdmflexiserver} <>
            [exec] (GDM flexiserver in Xnest) {gdmflexiserver -n} <>
            [exec] (GDM Photo Setup) {gdmphotosetup} <>
            [exec] (GDM Setup) {su-to-root -X -p root -c /usr/sbin/gdmsetup} <>
            [exec] (HPLIP File printing) {/usr/bin/hp-print} <>
            [exec] (Openbox Configuration Manager) {/usr/bin/obconf} <>
            [exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e su-to-root -p root -c /usr/sbin/pppconfig} <>
            [exec] (Startup-Manager) {su-to-root -X -c /usr/sbin/startupmanager} <>
            [exec] (Xclipboard) {xclipboard} <>
            [exec] (Xfontsel) {xfontsel} <>
            [exec] (Xkill) {xkill} <>
            [exec] (Xrefresh) {xrefresh} <>
         [end]
         [submenu] (Help) {}
            [exec] (Info) { x-terminal-emulator -T "Info" -e info} <>
            [exec] (Xman) {xman} <>
            [exec] (yelp) {/usr/bin/yelp} <>
         [end]
         [submenu] (Gnome) {}
            [exec] (Gnome Control Center) {/usr/bin/gnome-control-center} <>
         [end]
         [exec] (GNOME Network Tool) {/usr/bin/gnome-nettool} <>
         [exec] (GNOME system monitor) {/usr/bin/gnome-system-monitor} <>
         [submenu] (Hardware) {}
            [exec] (GNOME Floppy Formatter) {/usr/bin/gfloppy} <>
            [exec] (HPLIP Toolbox) {/usr/bin/hp-toolbox} <>
            [exec] (Xvidtune) {xvidtune} <>
         [end]
         [submenu] (Monitoring) {}
            [exec] (Conky) { x-terminal-emulator -T "Conky" -e /usr/bin/conky} <>
            [exec] (GNOME Log Viewer) {/usr/bin/gnome-system-log} <>
            [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} <>
            [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
            [exec] (Xconsole) {xconsole -file /dev/xconsole} <>
            [exec] (Xev) {x-terminal-emulator -e xev} <>
            [exec] (Xload) {xload} <>
         [end]
         [exec] (Network Admin) {/usr/bin/network-admin} <>
         [submenu] (Package Management) {}
            [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} <>
         [end]
         [submenu] (Security) {}
            [exec] (Ophcrack) {/usr/bin/ophcrack} <>
            [exec] (Seahorse) {/usr/bin/seahorse} <>
         [end]
         [exec] (Services Admin) {/usr/bin/services-admin} <>
         [exec] (Shares Admin) {/usr/bin/shares-admin} <>
         [exec] (Time Admin) {/usr/bin/time-admin} <>
         [exec] (User accounts Admin) {/usr/bin/users-admin} <>
      [end]
      [submenu] (Terminal Emulators) {}
         [exec] (mrxvt) {mrxvt} <>
         [exec] (Gnome Terminal) {/usr/bin/gnome-terminal} <>
         [exec] (aTerm) {aterm} <>
         [exec] (XTerm) {xterm} <>
         [exec] (X-Terminal as root (GKsu\)) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator} <>
         [exec] (XTerm (Unicode\)) {uxterm} <>
      [end]
      [submenu] (Text) {}
         [exec] (Character map) {/usr/bin/gucharmap} <>
         [exec] (Fortune) {sh -c 'while /usr/games/fortune | col -x | xmessage -center -buttons OK:1,Another:0 -default OK -file - ; do :; done'} <>
         [exec] (GNOME Dictionary) {/usr/bin/gnome-dictionary} <>
      [end]
      [submenu] (Tools) {}
         [exec] (File-Roller) {/usr/bin/file-roller} <>
      [end]
      [submenu] (Video) {}
         [exec] (totem (GStreamer\)) {/usr/bin/totem-gstreamer} <>
      [end]
      [submenu] (Viewers) {}
         [exec] (Evince) {/usr/bin/evince} <>
         [exec] (Eye of GNOME) {/usr/bin/eog} <>
         [exec] (F-Spot) {/usr/bin/f-spot} <>
         [exec] (Xditview) {xditview} <>
      [end]
      [submenu] (Web Development) {}
         [exec] (Seamonkey Composer) {/usr/bin/seamonkey -edit} <>
      [end]
   [end]
   [submenu] (Games) {}
      [submenu] (Action) {}
         [exec] (Gnibbles) {/usr/games/gnibbles} <>
         [exec] (Wing) {/usr/games/wing} <>
      [end]
      [submenu] (Blocks) {}
         [exec] (Gnometris) {/usr/games/gnometris} <>
      [end]
      [submenu] (Board) {}
         [exec] (Four-in-a-row) {/usr/games/gnect} <>
         [exec] (GL Chess) {/usr/games/glchess} <>
         [exec] (Gnome GYahtzee) {/usr/games/gtali} <>
         [exec] (Gnome Iagno) {/usr/games/iagno} <>
         [exec] (Gnome Lines) {/usr/games/glines} <>
         [exec] (Gnome Mahjongg) {/usr/games/mahjongg} <>
      [end]
      [submenu] (Card) {}
         [exec] (Gnome Blackjack) {/usr/games/blackjack} <>
         [exec] (Gnome FreeCell) {/usr/games/sol --variation freecell} <>
         [exec] (Gnome Solitaire Games) {/usr/games/sol} <>
      [end]
      [submenu] (Puzzles) {}
         [exec] (Gnome Klotski) {/usr/games/gnotski} <>
         [exec] (Gnome Robots) {/usr/games/gnobots2} <>
         [exec] (Gnome Sudoku) {/usr/games/gnome-sudoku} <>
         [exec] (Gnome Tetravex) {/usr/games/gnotravex} <>
         [exec] (Gnomine) {/usr/games/gnomine} <>
         [exec] (Same Gnome) {/usr/games/same-gnome} <>
      [end]
      [submenu] (Toys) {}
         [exec] (Oclock) {oclock} <>
         [exec] (Xclock (analog\)) {xclock -analog} <>
         [exec] (Xclock (digital\)) {xclock -digital -update 1} <>
         [exec] (Xeyes) {xeyes} <>
         [exec] (Xlogo) {xlogo} <>
      [end]
   [end]
[separator]
   [submenu] (Fluxbox)
     [submenu] (Backgrounds)
       [wallpapers] (/usr/share/fluxbox/backgrounds)
       [wallpapers] (~/.fluxbox/backgrounds)
     [end]
     [config] (Configuration)
     [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
      [end]
     [reconfig] (Reconfigure)
     [restart] (Restart)
     [end]
[separator]
   [exec] (Xkill) {xkill}
[separator]
   [workspaces] (Workspaces)
[separator]
   [exit] (Exit)
   [exec] (Reboot) {sudo shutdown -r now}
   [exec] (Shutdown) {sudo shutdown -h now}

[end]


```

> **jaskah said:**
> 
can you please tell me what you did here, which way you used the gcon-editor to re-activate all these gnome settings?

run gconf-editor.

> **jaskah said:**
> how are you making your back-ups?

remastersys. 

> **jaskah said:**
> i appreciate your help. thanks!

Again this isnt the only option, may not be the best option, its just what worked for me.

---

### Post by billgoldberg on 2008-08-03
> **DocYoung said:**
> here is my menu, some of it is redundant but its still a work in progress.

```


# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (odinware)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

   [exec] (Firefox) {/usr/bin/firefox-3.0} <>
[separator]
   [exec] (mrxvt) {mrxvt} <>
[separator]
   [exec] (Amarok) {amarok} <>
[separator]
   [exec] (Thunar) {Thunar} <>
[separator]
   [submenu] (Office) {}
      [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} <>
[separator]
      [exec] (OpenOffice.org Calc) {/usr/bin/oocalc} <>
      [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} <>
      [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} <>
   [end]
[separator]
   [submenu] (Applications) {}
      [submenu] (Accessibility) {}
         [exec] (Xmag) {xmag} <>
      [end]
      [submenu] (Data Management) {}
         [exec] (Seamonkey Addressbook) {/usr/bin/seamonkey -addressbook} <>
         [exec] (Tomboy) {/usr/bin/tomboy} <>
      [end]
      [submenu] (Editors) {}
         [exec] (Gedit) {/usr/bin/gedit} <>
         [exec] (Nano) { x-terminal-emulator -T "Nano" -e /bin/nano} <>
         [exec] (Xedit) {xedit} <>
      [end]
      [submenu] (File Management) {}
         [exec] (Baobab) {/usr/bin/baobab} <>
         [exec] (Brasero) {/usr/bin/brasero} <>
         [exec] (GNOME Search Tool) {/usr/bin/gnome-search-tool} <>
         [exec] (Nautilus) {nautilus --no-desktop} <>
         [exec] (Tracker Search Tool) {/usr/bin/tracker-search-tool} <>
      [end]
      [submenu] (Graphics) {}
         [exec] (GNOME Screenshot Tool) {/usr/bin/gnome-panel-screenshot} <>
         [exec] (ImageMagick) {/usr/bin/display logo:} <>
         [exec] (Kino) {/usr/bin/kino} <>
         [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} <>
         [exec] (The GIMP) {/usr/bin/gimp} <>
         [exec] (XSane) {/usr/bin/xsane} <>
         [exec] (X Window Snapshot) {xwd | xwud} <>
      [end]
      [submenu] (Net) {}
         [exec] (X-Chat) {xchat} <>
         [exec] (Epiphany web browser (Gecko\)) {/usr/bin/epiphany-gecko} <>
         [exec] (Firefox 3 Browser) {/usr/bin/firefox-3.0} <>
         [exec] (kazehakase) {/usr/bin/kazehakase} <>
         [exec] (Netsurf Web Browser) {/usr/bin/netsurf} <>
         [exec] (Seamonkey Browser) {/usr/bin/seamonkey} <>
      [end]
      [submenu] (Network) {}
         [submenu] (Communication) {}
            [exec] (Ekiga) {/usr/bin/ekiga} <>
            [exec] (Pidgin) {/usr/bin/pidgin} <>
            [exec] (Seamonkey Mail Composer) {/usr/bin/seamonkey -compose} <>
            [exec] (Seamonkey Mail & Newsgroups) {/usr/bin/seamonkey -mail} <>
            [exec] (Terminal Server Client) {/usr/bin/tsclient -f} <>
            [exec] (Xbiff) {xbiff} <>
         [end]
         [exec] (Evolution) {/usr/bin/evolution} <>
         [submenu] (File Transfer) {}
            [exec] (Transmission BitTorrent Client) {/usr/bin/transmission} <>
         [end]
         [exec] (Telnet) { x-terminal-emulator -T "Telnet" -e /usr/bin/telnet} <>
         [exec] (w3m) { x-terminal-emulator -T "w3m" -e /usr/bin/w3m /usr/share/doc/w3m/MANUAL.html} <>
      [end]
      [submenu] (Office) {}
         [exec] (HPLIP Fax address book) {/usr/bin/hp-fab} <>
         [exec] (HPLIP Fax utility) {/usr/bin/hp-sendfax} <>
         [exec] (OpenOffice.org Calc) {/usr/bin/oocalc} <>
         [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} <>
         [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} <>
      [end]
      [submenu] (Programming) {}
         [exec] (GDB) { x-terminal-emulator -T "GDB" -e /usr/bin/gdb} <>
         [exec] (Python (v2.5\)) { x-terminal-emulator -T "Python (v2.5)" -e /usr/bin/python2.5} <>
         [exec] (Tclsh8.4) { x-terminal-emulator -T "Tclsh8.4" -e /usr/bin/tclsh8.4} <>
      [end]
      [submenu] (Science) {}
         [submenu] (Mathematics) {}
            [exec] (Bc) { x-terminal-emulator -T "Bc" -e /usr/bin/bc} <>
            [exec] (Dc) { x-terminal-emulator -T "Dc" -e /usr/bin/dc} <>
            [exec] (GCalcTool) {/usr/bin/gcalctool} <>
            [exec] (Xcalc) {xcalc} <>
         [end]
      [end]
      [submenu] (Shells) {}
         [exec] (Bash) { x-terminal-emulator -T "Bash" -e /bin/bash --login} <>
         [exec] (Dash) { x-terminal-emulator -T "Dash" -e /bin/dash -i} <>
         [exec] (Sh) { x-terminal-emulator -T "Sh" -e /bin/sh --login} <>
      [end]
      [submenu] (Sound) {}
         [exec] (gmix (Gnome 2.0 Mixer\)) {/usr/bin/gnome-volume-control} <>
         [exec] (grecord (GNOME 2.0 Recorder\)) {/usr/bin/gnome-sound-recorder} <>
         [exec] (gtkpod) {/usr/bin/gtkpod} <>
         [exec] (Rhythmbox) {/usr/bin/rhythmbox} <>
         [exec] (Sonata) {/usr/bin/sonata} <>
         [exec] (Sound Juicer) {/usr/bin/sound-juicer} <>
         [exec] (vumeter (Gnome 2.0 Volume Meter\)) {/usr/bin/vumeter} <>
      [end]
      [submenu] (System) {}
         [submenu] (Administration) {}
            [exec] (alsaconf) { x-terminal-emulator -T "alsaconf" -e su-to-root -p root -c /usr/sbin/alsaconf} <>
            [exec] (Aptitude) { x-terminal-emulator -T "Aptitude" -e /usr/bin/aptitude} <>
            [exec] (Debian Task selector) { x-terminal-emulator -T "Debian Task selector" -e su-to-root -c tasksel} <>
            [exec] (DSL/PPPoE configuration tool) { x-terminal-emulator -T "DSL/PPPoE configuration tool" -e /usr/sbin/pppoeconf} <>
            [exec] (Editres) {editres} <>
            [exec] (GDM flexiserver) {gdmflexiserver} <>
            [exec] (GDM flexiserver in Xnest) {gdmflexiserver -n} <>
            [exec] (GDM Photo Setup) {gdmphotosetup} <>
            [exec] (GDM Setup) {su-to-root -X -p root -c /usr/sbin/gdmsetup} <>
            [exec] (HPLIP File printing) {/usr/bin/hp-print} <>
            [exec] (Openbox Configuration Manager) {/usr/bin/obconf} <>
            [exec] (pppconfig) { x-terminal-emulator -T "pppconfig" -e su-to-root -p root -c /usr/sbin/pppconfig} <>
            [exec] (Startup-Manager) {su-to-root -X -c /usr/sbin/startupmanager} <>
            [exec] (Xclipboard) {xclipboard} <>
            [exec] (Xfontsel) {xfontsel} <>
            [exec] (Xkill) {xkill} <>
            [exec] (Xrefresh) {xrefresh} <>
         [end]
         [submenu] (Help) {}
            [exec] (Info) { x-terminal-emulator -T "Info" -e info} <>
            [exec] (Xman) {xman} <>
            [exec] (yelp) {/usr/bin/yelp} <>
         [end]
         [submenu] (Gnome) {}
            [exec] (Gnome Control Center) {/usr/bin/gnome-control-center} <>
         [end]
         [exec] (GNOME Network Tool) {/usr/bin/gnome-nettool} <>
         [exec] (GNOME system monitor) {/usr/bin/gnome-system-monitor} <>
         [submenu] (Hardware) {}
            [exec] (GNOME Floppy Formatter) {/usr/bin/gfloppy} <>
            [exec] (HPLIP Toolbox) {/usr/bin/hp-toolbox} <>
            [exec] (Xvidtune) {xvidtune} <>
         [end]
         [submenu] (Monitoring) {}
            [exec] (Conky) { x-terminal-emulator -T "Conky" -e /usr/bin/conky} <>
            [exec] (GNOME Log Viewer) {/usr/bin/gnome-system-log} <>
            [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} <>
            [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
            [exec] (Xconsole) {xconsole -file /dev/xconsole} <>
            [exec] (Xev) {x-terminal-emulator -e xev} <>
            [exec] (Xload) {xload} <>
         [end]
         [exec] (Network Admin) {/usr/bin/network-admin} <>
         [submenu] (Package Management) {}
            [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} <>
         [end]
         [submenu] (Security) {}
            [exec] (Ophcrack) {/usr/bin/ophcrack} <>
            [exec] (Seahorse) {/usr/bin/seahorse} <>
         [end]
         [exec] (Services Admin) {/usr/bin/services-admin} <>
         [exec] (Shares Admin) {/usr/bin/shares-admin} <>
         [exec] (Time Admin) {/usr/bin/time-admin} <>
         [exec] (User accounts Admin) {/usr/bin/users-admin} <>
      [end]
      [submenu] (Terminal Emulators) {}
         [exec] (mrxvt) {mrxvt} <>
         [exec] (Gnome Terminal) {/usr/bin/gnome-terminal} <>
         [exec] (aTerm) {aterm} <>
         [exec] (XTerm) {xterm} <>
         [exec] (X-Terminal as root (GKsu\)) {/usr/bin/gksu -u root /usr/bin/x-terminal-emulator} <>
         [exec] (XTerm (Unicode\)) {uxterm} <>
      [end]
      [submenu] (Text) {}
         [exec] (Character map) {/usr/bin/gucharmap} <>
         [exec] (Fortune) {sh -c 'while /usr/games/fortune | col -x | xmessage -center -buttons OK:1,Another:0 -default OK -file - ; do :; done'} <>
         [exec] (GNOME Dictionary) {/usr/bin/gnome-dictionary} <>
      [end]
      [submenu] (Tools) {}
         [exec] (File-Roller) {/usr/bin/file-roller} <>
      [end]
      [submenu] (Video) {}
         [exec] (totem (GStreamer\)) {/usr/bin/totem-gstreamer} <>
      [end]
      [submenu] (Viewers) {}
         [exec] (Evince) {/usr/bin/evince} <>
         [exec] (Eye of GNOME) {/usr/bin/eog} <>
         [exec] (F-Spot) {/usr/bin/f-spot} <>
         [exec] (Xditview) {xditview} <>
      [end]
      [submenu] (Web Development) {}
         [exec] (Seamonkey Composer) {/usr/bin/seamonkey -edit} <>
      [end]
   [end]
   [submenu] (Games) {}
      [submenu] (Action) {}
         [exec] (Gnibbles) {/usr/games/gnibbles} <>
         [exec] (Wing) {/usr/games/wing} <>
      [end]
      [submenu] (Blocks) {}
         [exec] (Gnometris) {/usr/games/gnometris} <>
      [end]
      [submenu] (Board) {}
         [exec] (Four-in-a-row) {/usr/games/gnect} <>
         [exec] (GL Chess) {/usr/games/glchess} <>
         [exec] (Gnome GYahtzee) {/usr/games/gtali} <>
         [exec] (Gnome Iagno) {/usr/games/iagno} <>
         [exec] (Gnome Lines) {/usr/games/glines} <>
         [exec] (Gnome Mahjongg) {/usr/games/mahjongg} <>
      [end]
      [submenu] (Card) {}
         [exec] (Gnome Blackjack) {/usr/games/blackjack} <>
         [exec] (Gnome FreeCell) {/usr/games/sol --variation freecell} <>
         [exec] (Gnome Solitaire Games) {/usr/games/sol} <>
      [end]
      [submenu] (Puzzles) {}
         [exec] (Gnome Klotski) {/usr/games/gnotski} <>
         [exec] (Gnome Robots) {/usr/games/gnobots2} <>
         [exec] (Gnome Sudoku) {/usr/games/gnome-sudoku} <>
         [exec] (Gnome Tetravex) {/usr/games/gnotravex} <>
         [exec] (Gnomine) {/usr/games/gnomine} <>
         [exec] (Same Gnome) {/usr/games/same-gnome} <>
      [end]
      [submenu] (Toys) {}
         [exec] (Oclock) {oclock} <>
         [exec] (Xclock (analog\)) {xclock -analog} <>
         [exec] (Xclock (digital\)) {xclock -digital -update 1} <>
         [exec] (Xeyes) {xeyes} <>
         [exec] (Xlogo) {xlogo} <>
      [end]
   [end]
[separator]
   [submenu] (Fluxbox)
     [submenu] (Backgrounds)
       [wallpapers] (/usr/share/fluxbox/backgrounds)
       [wallpapers] (~/.fluxbox/backgrounds)
     [end]
     [config] (Configuration)
     [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
      [end]
     [reconfig] (Reconfigure)
     [restart] (Restart)
     [end]
[separator]
   [exec] (Xkill) {xkill}
[separator]
   [workspaces] (Workspaces)
[separator]
   [exit] (Exit)
   [exec] (Reboot) {sudo shutdown -r now}
   [exec] (Shutdown) {sudo shutdown -h now}

[end]


```



run gconf-editor.



remastersys. 



Again this isnt the only option, may not be the best option, its just what worked for me.

Haha, my menu seems redicilous compared to yours. 

But then I never use it anyway.

I'm only using my keyboard shortcuts or alt+f2 (fbrun) or F12 (xterm)..

> [begin] (Fluxbox)
[exec] (Xterm) {xterm}
[separator]
[submenu] (Tools)
[exec] (File Roller) {file-roller}
[exec] (Feh Image Viewer) {feh}
[exec] (Synaptic) {gksu synaptic}
[end]
[submenu] (Internet)
[exec] (Firefox) {firefox}
[exec] (Emesene) {emesene}
[exec] (Transmission) {transmission}
[exec] (Xchat) {xchat}
[exec] (Frostwire) {frostwire}
[exec] (Nicotine Plus) {nicotine}
[end]
[submenu] (Editors)
[exec] (Mousepad) {mousepad}
[exec] (Abiword) {abiword}
[exec] (Gnumeric) {gnumeric}
[end]
[submenu] (Multimedia)
[exec] (VLC Media Player) {vlc}
[exec] (Sonata) {sonata}
[exec] (Brasero) {brasero}
[exec] (Audio Tag Tool) {tagtool}
[exec] (Avidemux) {avidemux}
[end]
[submenu] (Graphics)
[exec] (Gimp) {gimp}
[exec] (Xpdf) {xpdf}
[end]
[separator]
[submenu] (Fluxbox Menu)
[config] (Configure)
[submenu] (Styles) {Choose a Style…}
[stylesdir] (/usr/X11R6/share/fluxbox/styles)
[end]
[workspaces] (Workspace List)
[submenu] (Tools)
[exec] (Window name) {xprop WM_CLASS|cut -d \” -f 2|xmessage -file - -center}
[end]
[commanddialog] (Fluxbox Command)
[reconfig] (Reload config)
[restart] (Restart Fluxbox)
[exec] (About) {fluxbox -v 2>/dev/null | head -n1 | xmessage -file - -center}
[exit] (Exit Fluxbox)
[separator]
[exec] (Reboot) {shutdown -r now}
[exec] (Shutdown) {shutdown -p now}
[end]
[end]

---

### Post by jaskah on 2008-08-03
> run gconf-editor..

yes, but what did you *do* in the editor. which settings did you change?

thanks.



> remastersys.

thanks again!

---


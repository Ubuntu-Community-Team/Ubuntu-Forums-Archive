---
title: "How to get nm-applet to appear and show available wireless networks in OpenBox"
date: 2008-12-10
forum: General Help
---

### Post by |{urse on 2008-12-10
mk hi ):P

So I've turned into a real openbox junkie in the past year, this walkthrough assumes that you have openbox all set up and that you are usinga regular non .xsession script to load all your panels and goodies etc. (if you like having things automatically load, feel free to do it however you like it)

The only thing so far that has really bothered me about openbox is the lack of a system tray, and anyone using openbox w/ a wireless connection knows its a pain in the butt to run NetworkManager everytime you lose signal.

Okay, now this first thing you need to do is download and install stalonetray

```
sudo apt-get install stalonetray
```

alright easy enough, you can pimp stalonetray as you see fit. Here's my .stalonetrayrc (located @ $HOME/.stalonetrayrc)

> 

# background <color>         # color can be specified as an HTML hex triplet or
                             # as a name from rgb.txt, note that '#' must be quoted
background "#777777"

# decorations <decspec>      # set trays window decorations; possible values for
                             # decspec are: all, title, border, none
decorations none

# display <display name>     # as usual

# dbg_level <int>            # controls the amount of debug info (for this setting to
                             # have effect, stalonetray sources must have been
                             # configured and compiled with --enable-debug)
# dbg_level 0

# fuzzy_edges [<level>]      # enable fuzzy edges and set fuzziness level. level
                             # can be from 0 (disabled) to 3; this setting works
                             # with tinting and/or transparent and/or pixmap
                             # backgrounds (NEW in 0.7)
fuzzy_edges 3

# geometry <geometry>        # tray's geometry in standard X notation
geometry 124x24+0-0

# grow_gravity <gravity>     # one of N, S, E, W, NW, NE, SW, SE; tray will grow
                             # in the direction opposite to one specified by
                             # grow_gravity; if horizontal or vertical
                             # direction is not specified, tray will not grow in
                             # that direction
grow_gravity NW

# icon_gravity <gravity>     # icon placement gravity, one of NW, NE, SW, SE
icon_gravity NW

# icon_size <int>            # specifies dimensions of typical icon slot
icon_size 18

# ignore_icon_resize [<bool>] # ignore icon attempts to resize their windows
                             # (NEW in 0.7)
ignore_icon_resize false

# max_width <int>            # specifies maximal tray's width (0 = no limit)
max_width 0

# max_height <int>           # specifies maximal tray's height (0 = no limit)
max_height 28

# no_shrink [<bool>]         # disables shrink-back mode (NEW in 0.7)
no_shrink false

# parent_bg [<bool>]         # whether to use pseudo-transparency 
                             # (looks better when reparented into smth like FvwmButtons)
parent_bg false

# pixmap_bg <path_to_xpm>    # use pixmap from specified xpm file for (tiled) background
# pixmap_bg /home/user/.stalonetraybg.xpm

# respect_icon_hints [<bool>] # try to respect icon hints (NEW in 0.7)
respect_icon_hints false

# skip_taskbar [<bool>]      # hide tray`s window from the taskbar
skip_taskbar true

# sticky [<bool>]            # make a tray`s window sticky across the
                             # desktops/pages
sticky true

# tint_color <color>         # set tinting color (NEW in 0.7)
tint_color black

# tint_level <level>         # set tinting level; level ranges from 0 (disabled)
                             # to 255 (NEW in 0.7)
tint_level 200 

# transparent [<bool>]       # whether to use root-transparency (background
                             # image must be set with Esetroot or compatible utility)
transparent true

# vertical [<bool>]          # whether to use vertical layout (horisontal layout
                             # is used by default)
vertical false

# window_layer <layer>       # set the EWMH-compatible window layer; one of:
                             # bootom, normal, top
window_layer bottom

# window_type <type>         # set the EWMH-compatible window type; one of:
                             # dock, normal, toolbar, utility
window_type dock 

# withdrawn [<bool>]         # start withdrawn (NEW in 0.7, prior to that
                             # withdrawn mode was default!)
withdrawn false 

# xsync [<bool>]             # whether to operate on X server synchronously (SLOOOOW)
xsync false


It is also necessary to point out that with this .stalonetrayrc the tray is going to appear wherever the dock is, set this with obconf of course.

simple =) now the last important thing to do make sure your scripts are set to run nm-applet when starting up OpenBox.  As i mentioned before i dont use an .xsession script, i launch mine by hand if i need the desktop. Feel free to add nm-applet to your .xsession script somewhere AFTER stalonetray in the script.

Heres mine

```
#!/bin/bash
#xcompmgr -c -r 6 -o 0.45 -l -9 -t -7 &
gksudo network-admin &
gnome-volume-manager & 
gnome-appearance-properties %F  #because feh is buggy on my box 
tint &
stalonetray &
nm-applet &
wbar -vbar -pos left -nanim 1 &
cd Desktop
./Conkyy
```

Now, in order to get the nice list of available wireless connections you need to edit /etc/network/interfaces

```
sudo gedit /etc/network/interfaces
```

Now comment out everything except the loopback stuff (don't ask me why this is necesssary but you need to do it or you wont get a list of available wireless connections)

heres my working /etc/network/interfaces

> auto lo
iface lo inet loopback

#iface ath0 inet dhcp
#wireless-essid myhomenetwork


now you should have a nice functional system tray running on openbox along with a much needed network applet.

:p

---

### Post by Dark Hornet on 2008-12-12
Thanks for the how-to...I saw your screenshot and fell in love with it.  I currently run #! (an openbox ubuntu based distro) on an extra old box I have laying around.  For this box, I am experimenting with Openbox, Conky, etc and just having a bit of fun without messing up my production machine -- see sig below -- at any rate, your .stalonetray caught my eye so I copied your .stalonetrayrc file and gave it a go.  I keep getting an error that I was wondering if you could help me with.

**stalonetrayrc:23: unrecognized rc file keyword "124x24+3-3"**.  I have tried to change those values, and no matter what I seem to do I keep getting the same thing.  Any thoughts?  I have searched, and am currently searching google for info, but stalonetray seems to be limited on its documentation.

Thanks in advance for any help you can provide...

Darkhornet

---

### Post by |{urse on 2008-12-12
OH! 124x24+3-3.. lol It's supposed to be "geometry 124x24+0-0" (sans quotes) in X notation geometry. Thanks for the mention =) I'm still stuck on that current desktop and looking for something like the beryl cube and totally forgot about 3ddesktop

```
sudo apt-get install 3ddesktop
```

for max viewing pleasure run 

> 3ddesk --acquire

the first time =)

all subsequent runs are simply

> 3ddesk --mode=cylinder

in a script or from the terminal. This app is so simple and cool, it makes me wonder why i cared about beryl/compiz in the first place :p

If anyone has any ideas on how to make openbox cooler/functional(er) while still keeping resource hoggery at a minimum pls drop a reply =)

---


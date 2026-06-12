---
title: "Panels and AWN"
date: 2008-08-06
forum: Desktop Environments
---

### Post by Graelb on 2008-08-06
Hi there,

I'm trying to just run ubuntu without using the gnome panels... I'd like to get rid of the panel, and just run AWN, with some kind of floating system tray. Ideally, i'd like the panel to be small and on the right hand side of the screen, but i can't get rid of the little gray blocks on the outside edges of the mini-panel. I could actually live with the panel being there, if i could just get rid of the little gray boxes.... 

Any ideas?

---

### Post by sayakb on 2008-08-06
You may completely delete the panel. I'm not sure how you can remove the gray bars from the panel borders. If you wish to remove it completely, goto **System->Preferences->Sessions**, click on **Current Session** tab and change the style of gnome-panel to **Trash**. Don't close the window. Now at a terminal, type:
```
killall gnome-panel
```
Now again at the session properties window, click the **Session Options** tab and **check** the *Automatically remember... *checkbox. Now restart X (Ctrl+Alt+Backspace).

---

### Post by Graelb on 2008-08-06
Beautiful! that does exactly what i want...  now is there a replacement system tray applet or program?

---

### Post by Pogeymanz on 2008-08-06
You can try stalonetray. Here is a screenshot of my desktop with stalonetray in the bottom-left corner with a transparent background.

Here is the .stalonetrayrc file I use:
```
# vim:filetype=config:tw=80:et
# 
# This is sample ~/.stalonetrayrc, resembling default configuration.
# Remember: command line parameters take precedence.
#
# Directives introduced in 0.7.6 are marked with "NEW in 0.7.6"
#
####################################################################
# 
# stalonetray understands following directives
#
####################################################################

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
fuzzy_edges 0

# geometry <geometry>        # tray's geometry in standard X notation
geometry 120x24+0-0

# grow_gravity <gravity>     # one of N, S, E, W, NW, NE, SW, SE; tray will grow
                             # in the direction opposite to one specified by
							 # grow_gravity; if horizontal or vertical
							 # direction is not specified, tray will not grow in
							 # that direction
grow_gravity NW

# icon_gravity <gravity>     # icon placement gravity, one of NW, NE, SW, SE
icon_gravity NW

# icon_size <int>            # specifies dimensions of typical icon slot
icon_size 24

# ignore_icon_resize [<bool>] # ignore icon attempts to resize their windows
                             # (NEW in 0.7)
ignore_icon_resize false

# max_width <int>            # specifies maximal tray's width (0 = no limit)
max_width 0

# max_height <int>           # specifies maximal tray's height (0 = no limit)
max_height 24

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
tint_level 0 

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

```

---

### Post by Graelb on 2008-08-07
lol, ok, panels done away with has caused unforseen side effects... i now cannot do the alt+F2 to get the run dialog... is that common?

---

### Post by Graelb on 2008-08-07
OR... how about a way to run a command in a terminal, but not have it stay in the terminal... for example... if i run "avant-window-navigator" in a terminal, it shows a bunch of output from the application, is there a --noattach option or something for all commands so it doesn't keep outputting to the terminal, and puts me back at a prompt?

---

### Post by 987poiuytrewq on 2008-12-17
If you put an ampersand at the end of any command, it will not close when you close the terminal, e.g.
```
avant-window-navigator&
```
will run awn separate to the terminal, so you can safely close it and keep awn running.

---


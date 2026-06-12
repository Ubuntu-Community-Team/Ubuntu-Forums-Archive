---
title: "Fluxbox menu/command question"
date: 2007-01-19
forum: Desktop Environments
---

### Post by WetWired on 2007-01-19
I'm wondering, is it possible to add Synaptic to the menu in fluxbox and have it start in root? Or at least prompt you for a password in root? If so, I'd love to know how.

---

### Post by kerry_s on 2007-01-19
[exec] (Synaptic) {gksu synaptic}

Don't you have the debian menu?

```
[begin] (Fluxbox)

[exec] (Thunar) {Thunar} 

[exec] (Terminal) {xfce4-terminal} 
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
 [exec] (Prozilla) {xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (Gxine) {gxine}
 [exec] (VLC) {wxvlc}
 [exec] (Mplayer) {gmplayer}
 [exec] (Wmix) {wmix}
 [exec] (Kill-Wmix) {killall wmix}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {gksu synaptic}
 [exec] (Root-Thunar) {gksu Thunar /}
 [exec] (Terminal-Root) {gksu xterm}
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
[exec] (Run Program) {xfrun4}

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


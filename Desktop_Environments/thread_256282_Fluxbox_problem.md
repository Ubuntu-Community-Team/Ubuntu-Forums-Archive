---
title: "Fluxbox problem"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Cloudy on 2006-09-12
I can't do anything in Fluxbox.

I'm not sure why.. I installed Fluxbox along with XFCE and Enlightenment a few days ago. XFCE & Enlightenment work fine, but when I use Fluxbox - you know you right click to get a menu? Yeah. I think that's it. Anyway, when I right click there's nothing on the menu? Am I doing something wrong, did I miss something obvious.. am I having problems with Fluxbox? There are no listings at all in the menu.

---

### Post by statue on 2006-09-12
Well,yes, something is wrong. It should be rightclick>menu....perhaps your menu list is corrupted?

---

### Post by kerry_s on 2006-09-12
Try this, go to .fluxbox(hidden file)/menu change the include line to this-> 
[include] (~/.fluxbox/fluxbox-menu)
then in terminal do->
update-menus

that should get you a stock menu.
or you can create one yourself, here's mine you can change around to what ever you have installed->
```
[begin] (Fluxbox)
 
[exec] (ROX) {rox} 

[submenu] (Terminals)
 [exec] (Xterm) {xterm}
 [exec] (Eterm) {Eterm --borderless --buttonbar 0 --trans --shade 0 --scrollbar false}
[end]
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
[end]

[submenu] (Office)
 [exec] (Gimp) {gimp}
 #[exec] (Xpad) {xpad}
 [exec] (Xcalc) {xcalc}
 #[exec] (Abiword) {abiword}
[end]

#[submenu] (Sound)
 #[exec] (XMMS) {xmms}
 #[exec] (Mplayer) {gmplayer}
#[end]

[submenu] (Admin)
 [exec] (Synaptic) {sudo synaptic}
 [exec] (Root-Rox) {sudo rox /}
 [exec] (Terminal-Root) {sudo Eterm}
 #[exec] (Run-Root) {gksuexec}
[end]

[submenu] (Fluxbox)
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
[submenu] (Tools)
 [exec] (Kill) {xkill}
 #[exec] (Xfburn) {xfburn}
 #[exec] (Printer) {gnome-cups-manager}
[end]

[separator]
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}


[separator]
[submenu] (Original)
 [begin] (fluxbox)
 [include] (~/.fluxbox/fluxbox-menu)
[end]

```

---

### Post by Cloudy on 2006-09-14
Thanks, I'll do that.

---


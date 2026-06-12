---
title: "[SOLVED] Fluxbox Background Trouble"
date: 2006-09-18
forum: Desktop Environments
---

### Post by shinkaide on 2006-09-18
Hi, I've been trying to customize my fluxbox installation's background as per the [wiki instructions]("https://help.ubuntu.com/community/Fluxbox"), in the customization section. I've done what it said I should do with the init and startup files, but I still can't get the wallpaper to override the style. 

The wallpaper displays for a short while during the fluxbox startup, then gets covered by whatever color/gradient the style defines. Help, please.

---

### Post by Ramses de Norre on 2006-09-18
```
vi .fluxbox/init
```
Type /root to find the appropriate line quickly, this will bring you to 
session.screen0.rootCommand:
Change it to: ```
session.screen0.rootCommand:    fbsetbg -l

```
Press esc, shift + q, wq.

---

### Post by shinkaide on 2006-09-18
Yes, I have done that already; it doesn't solve the problem.

---

### Post by Ramses de Norre on 2006-09-18
That's the only command on that line, right?
And is there anything about wallpapers in .fluxbox/startup ?

---

### Post by kerry_s on 2006-09-18
Make sure you also comment out the line in /.fluxbox/startup that sets a background ( #/usr/bin/fbsetroot -solid black )

You can change your "styles" file to load the background you want,look for a line like this->
rootCommand: fbsetbg ~/.fluxbox/backgrounds/open.jpg
change it to point to your background.

If you added the line in /.flubox/init ( session.screen0.rootCommand:	fbsetbg -l ). I have a menu entry that lets me change the background on the fly and i never have to edit anything. It looks like this->

```
 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]
```

I don't no if you know how to edit your own menu, i always make my own->

```
[begin] (Fluxbox)

[exec] (ROX) {rox} 

[submenu] (Terminals)
 [exec] (Eterm) {Eterm --borderless --buttonbar 0 --trans --shade 0 --scrollbar false}
[end]
 
[submenu] (Net)
 [exec] (Firefox) {firefox}
 [exec] (Dillo) {dillo}
 [exec] (Gaim) {gaim}
[end]

[submenu] (Office)
 [exec] (Gimp) {gimp}
 [exec] (Xpad) {xpad}
 [exec] (Xcalc) {xcalc}
 [exec] (Abiword) {abiword}
[end]

[submenu] (Sound)
 [exec] (XMMS) {xmms}
 [exec] (Mplayer) {gmplayer}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {sudo synaptic}
 [exec] (Root-Rox) {sudo rox /}
 [exec] (Terminal-Root) {sudo Eterm}
 [exec] (Run-Root) {gksuexec}
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
 [exec] (Xfburn) {xfburn}
 [exec] (Printer) {gnome-cups-manager}
[end]

[separator]
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]

```

---

### Post by Ramses de Norre on 2006-09-18
What I did to make wallpaper changing easier is making a nautilus script.
I don't know if you use nautilus but if you do this makes life easier:
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
for I in "$*"
do
    fbsetbg -f $I
    exit 0
done

```
Copy it to .gnome2/nautilus-scripts/fbsetbg and make it executable.

---

### Post by shinkaide on 2006-09-22
Thanks guys, I've solved it!

---


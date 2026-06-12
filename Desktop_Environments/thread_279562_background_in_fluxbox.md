---
title: "background in fluxbox"
date: 2006-10-18
forum: Desktop Environments
---

### Post by 25an on 2006-10-18
Hi!
I have installed fluxbox and it works with no problems.
But was wondering how I change the background so it covers the entire desktop. As it is now when I run

fbsetbg -f /home/mans/Share/Apperance/35826-stormy.jpg

It don't cover the entire desktop.

Any ideas?

---

### Post by kerry_s on 2006-10-18
Try using some of the other settings->

-f file 
 Set fullscreen wallpaper. 
-c file 
 Set centered wallpaper. 
-t file 
 Set tiled wallpaper. 
-a file 
 Set maximized wallpaper, preserving aspect (if your bgsetter doesn't support this option fbsetbg falls back to -f ).


I used fbsetbg -l because i use a menu entry to change my background when ever i want with out having to edit anything.

Just in case you want to do that here's how->

First go to ~.fluxbox/init and open it with your editor
look for-> session.screen0.rootCommand:
change to
session.screen0.rootCommand:	fbsetbg -l

Now go to .fluxbox/menu and open it with your editor
Add this line to the menu->

[submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]


That's it you should be able to select your backgrounds from the menu as long as you put them in ./fluxbox/backgrounds

---

### Post by 25an on 2006-10-18
Thanks for your quick response.

> 
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[submenu] (Backgrounds)
[Wallpapers] (/usr/share/fluxbox/backgrounds)
[Wallpapers] (~/.fluxbox/backgrounds)
[end]
[end]


I don't get any wallpapers under the background submenu,
and when i run the commands that you gave me the background  never stretches?
If I run  fbsetbg -i I get following
> 
display doesn't set the wallpaper properly. Transparency for fluxbox and apps like aterm and xchat won't work right with it. Consider installing feh, wmsetbg (from windowmaker) or Esetroot (from Eterm) and I'll use them instead.


Is this the problem?

---

### Post by kerry_s on 2006-10-18
> If I run fbsetbg -i I get following

That's suppose to be a small "l" as in last
What are you using to set the background? 
I use eterm for mine. Also i noticed in your first post your path->
 "/home/mans/Share/Apperance/35826-stormy.jpg" instead of the background folder. You can move them to the background folder or put that path to the menu.

[begin] (fluxbox)
 [include] (/etc/X11/fluxbox/fluxbox-menu)
 [submenu] (Backgrounds)
 [Wallpapers] (/usr/share/fluxbox/backgrounds)
 [Wallpapers] (~/.fluxbox/backgrounds)
 [Wallpapers] (/home/mans/Share/Apperance)
 [end]
 [end]

Here's a pic of what it should look like->

---

### Post by kerry_s on 2006-10-18
Here's my menu just in case, you can adapt it to your programs.

[begin] (Fluxbox)

[exec] (Rox) {rox} 

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
[submenu] (Debian-menu)
 [begin] (fluxbox)
  [exec] (Update-Menus) {update-menus}
  [include] (~/.fluxbox/fluxbox-menu)
[end]


[separator]
[exit] (Exit)
[exec] (Reboot) {sudo shutdown now -r -f}
[exec] (Shutdown) {sudo shutdown now -h}
[end]


For shutdown visudo and add this->
user ALL=(root) NOPASSWD: /sbin/shutdown

---

### Post by macewan on 2006-11-27
nitrogen works well if you'd like to see the pictures before you apply the change

---

### Post by steevk on 2006-11-27
Here's the deal: When you run 'fbsetbg -i' it'll tell you that 'oh, I don't like this program, try one of these others:'. Apt-get one of those, and it'll work like a charm.

---


---
title: "Please help to fix a bug in the theme"
date: 2015-08-22
forum: Desktop Environments
---

### Post by tamir2 on 2015-08-22
We launch the audio/video programs from the tray, or rather of the applet where all the sound settings (screenshot attached).
Menus when you run more than two programs becomes very narrow, so that access to the audio settings from the menus of the very difficult (you need to click on the navigation arrows). There is no option to make these broader limiting the scope of sound menus? Maybe config theme can be configured?


OS - Xubuntu 14.04 with xfce 4.12.

---

### Post by CantankRus on 2015-08-22
Does the same for me in Ubuntu but letting the window close, then clicking
on the sound icon again draws with a wider window.

---

### Post by Dennis N on 2015-08-23
I don't think the up and down arrows should be there. I could not get them no matter how hard I tried. My sound menu always appears the same size with the sound settings option visible. Image attached.

Edit: A different experience with 3 music applications in the menu. See post #4

It's possible to remove the other player (gmusicbrowser) from the menu, but I don't recall exactly how. That might help. I will see if I can find directions.

Edit: Directions for removing in Post #7

---

### Post by Dennis N on 2015-08-23
@tamir2,

Confirmed your observations with 3 audio players in the sound menu. I installed VLC and it has now parked itself permanently in the menu along with the other two. With 3, first menu opening there are scroll arrows top and bottom - Second opening, the lower panel is overlapped by the menu. Third open, no arrows, no overlap, with sound menu visible - which is what I want. Irregularly, the menu now appeared higher up as well. The menu needs some work.

Now, how to display only two of the three.

---

### Post by tamir2 on 2015-08-23
I tried to find a solution to this problem and I thought this is due only to the theme of design, but it turns out it is not. In particular, it proves two bug report on this subject:
[https://bugzilla.gnome.org/show_bug.cgi?id=726030](https://bugzilla.gnome.org/show_bug.cgi?id=726030)[URL="https://bugzilla.gnome.org/show_bug.cgi?id=726030"]
[/URL][https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965953](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/965953)
 Alas how to solve this problem, I did not understand ... it would be appropriate to attract the attention of developers to this point.

---

### Post by tamir2 on 2015-08-24
Strangely, with the theme of Gnome-Cupertino-2.1.5 (attached) these limits do not appear (but distorts the theme color of some elements of the panel). .. I'm in complete confusion ..

Gnome-Cupertino-2.1. -[http://gnome-look.org/content/show.php?content=147061](http://gnome-look.org/content/show.php?content=147061)

A theme that I use (Mint-X-Aqua attached) these limits there (but all the elements the panel looks fine)

---

### Post by Dennis N on 2015-08-24
I got rid of unwanted players from the sound menu. That eliminates the arrows at top and bottom from appearing. 

For anyone interested:

Install dconf-editor (if not already installed). Expand the tree on the left to reach com> cannonical > indicator > sound
Then edit to remove unwanted players from 'interested-media-players'. I tried 'blacklist' first, but it did not work. I only left 'audacious' in my list. I also set 'preferred-media-players' to 'audacious'. Removed players can reappear if you start them up.

Those themes look good. If you use Mint-X-Aqua, are you using the matching Mint-X-Aqua icon theme? I use the Blue variety in MATE.

---

### Post by tamir2 on 2015-08-24
[URL="http://ubuntuforums.org/member.php?u=321222"][B][COLOR=#000000]Dennis N,
[/COLOR][/B][COLOR=#000000]thanks for the advice. [/COLOR][B][COLOR=#000000]
[/COLOR][/B][/URL]Yes, of course I picked the color theme set of icons (self collected).
The only thing that I wanted to fix it minimized windows on the panel does not dimmed, but would remain bright (attached)

---


---
title: "Maximus"
date: 2010-08-04
forum: Desktop Environments
---

### Post by orc_dragoon on 2010-08-04
Instead of using UNR for my netbook, I decided to use the normal desktop version because I dont like UNR launcher. My question is "Is there a better way to integrate maximus into gnome". Im asking this question, because of right now it doesn't feel as good as it did in UNR...the maximized apps don't even have an X next to there names like UNR. So, Im looking for someone who is experienced in this part...to help configure maximus to work better in gnome.

---

### Post by kerry_s on 2010-08-04
yes
press-> alt+f2
type-> gconf-editor
go to-> apps-> maximus
uncheck "undecorate"

also you can use window picker applet in gnome.

---

### Post by kerry_s on 2010-08-06
here's another idea.
you can create your own buttons using launchers & you can keep the normal taskbar.

you just need to install "wmctrl", here are the commands.

```
close active window:
wmctrl -c :ACTIVE:

for minimize will use the showdesktop, cause it only works that way:
wmctrl -k on

unmaximize & maximize:
wmctrl -r :ACTIVE: -b toggle,maximized_horz,maximized_vert
```

here's how yours can look like, except i'm using xfce4-panel instead of gnome-panel. my buttons are on the left.

---

### Post by kernst on 2011-10-04
> **orc_dragoon said:**
> Instead of using UNR for my netbook, I decided to use the normal desktop version because I dont like UNR launcher. My question is "Is there a better way to integrate maximus into gnome".

Sadly, everyone seems to have moved on with all the hype surrounding GNOME 3 and Unity. If there are any 10.04 + UNE holdouts out there, you may find this guide useful:

[http://www.webupd8.org/2010/06/how-to-get-most-out-of-ubuntu-netbook.html](http://www.webupd8.org/2010/06/how-to-get-most-out-of-ubuntu-netbook.html)

Even though the guide is geared towards netbooks, that's basically how I set up my full-scale desktop environment as well (on a 1600x1050 px monitor, even). I allow Maximus to maximize all windows, but use ichneumon's ["Maximus Manager" script]("http://ubuntuforums.org/showthread.php?t=1483946") to make it easier to exclude specific windows from being maximized. It takes about a week of use to get things "just right." It's this script, bound to a hotkey, that makes using Maximus even tolerable.

I could have gone the other way and set [FONT="Courier New"]/apps/maximus/no_maximize[/FONT] as the instructions above suggest, then used the Compiz "Window Rules" plugin (from the 'compiz-plugins-extra' package, I believe) to specify *just* the applications/window classes I wanted to run maximized. Maybe that would be less work in the end. I'm mostly okay with most everything running full-screen, except Vim, and multi-window apps like Thunderbird or Inkscape.

To round out the Zen-like desktop experience, I make four horizonally-oriented virtual desktops (Alt + 1/2/3/4 set up as hotkeys in the "Viewport Switcher" Compiz plugin), set the Compiz "Scale" plugin to activate with the upper-right hot corner, and "Show Desktop" with the lower-left. I have the Workspace Switcher and DockbarX applets in a bottom panel, as shown in the attached screenshot. The Window Buttons and Global Menu applets in the top panel come from the PPAs mentioned in the guide above. I find that this pretty much incorporates the best of all three major OSes: Windows' super-bar (whatever they call it), Mac OS's global menu and Exposé (turn on the Compiz "Scale Window Title Filter" for a better Exposé than Exposé), and Compiz's slick plugins and tweakability.

It ain't perfect. The GNOME Global Menu applet seems to be a [dead project]("https://github.com/gnome-globalmenu/gnome-globalmenu/commits/master"), so it lacks support for Firefox, Thunderbird, or Open/LibreOffice (or they lack support for it, whatever the case may be). Some windows from excluded applications remember that they want to be maximized on startup, but Maximus doesn't undecorate them properly (*i.e.*, remove the title bar and borders) until you restore/re-maximize them. Still beats the crap out of Windows with [VirtuaWin]("http://virtuawin.sourceforge.net/") or Mac OS X's Spaces (which is full of bugs, at least on 10.5).

---

### Post by M7S on 2011-10-04
Why do you still use globalmenu instead of the better supported pane applet "applicationmenu for panelindicator" (free translation from swedish)  that comes with Ubuntu 11.04? With that one you can get global menus for  Firefox, Thunderbird, or Open/LibreOffice.

---

### Post by kernst on 2011-10-05
> **M7S said:**
> Why do you still use globalmenu instead of the better supported pane applet "applicationmenu for panelindicator" (free translation from swedish)  that comes with Ubuntu 11.04? With that one you can get global menus for  Firefox, Thunderbird, or Open/LibreOffice.

10.04 LTS is why.

---


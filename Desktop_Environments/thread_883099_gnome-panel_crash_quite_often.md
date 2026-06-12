---
title: "gnome-panel crash quite often"
date: 2008-08-07
forum: Desktop Environments
---

### Post by lnthai2002 on 2008-08-07
Has anyone experience gnome_panel freeze randomly recently? I have it freeze 4 times today. Any idea?

---

### Post by Fen_Star on 2008-08-07
> **lnthai2002 said:**
> Has anyone experience gnome_panel freeze randomly recently? I have it freeze 4 times today. Any idea?I have, but I'm guessing I did something to mess it up.

Looking at some other threads it may have something to do with gnome applets.

---

### Post by Bob Howland on 2008-08-07
I started experiencing all sorts of problems with the panels and with minimizing applications after my last software update. If Ubuntu wants to have the reputation for just plain working, they're going to have to fix their very serious continuing problems with regression failures. It's a crapshoot any time that the software is updated.

Oh well, back to Windows 2000!

---

### Post by val88chan on 2008-08-08
yeah,,,i have the same problem too...with gnome-applet...it's so difficult for me to solve that...and may desktop icons also dissapered and i cant save anything there. and i also cannot open nautilus(am i right?this is like windows explorer for gnome??),,it;s always dissapear after i try to click folder.
i'm using ubuntu 7.10

thanks

---

### Post by n0th1n on 2008-08-08
Well, this might be what you mean or related, but I just recently started having a bunch of problems. First my theme changed suddenly, then firefox started crashing a bunch, and then it started crashing and saying "greeter appears to be crashing, trying another one" or something, over and over, restarted it, did it again, turned it off, waited, now its back to normal.

---

### Post by lnthai2002 on 2008-08-09
n0th1n,did you change anything to make it stop crashing? It starts to crash again even after i reboot (yup, it sounds like windows!) I tried xubuntu last week but since nautilus is the only file manager can browse my windows network, I have to come back to gnome base ubuntu. It seems the xfce applet is much better than gnome. Let us know if anyone found a fix for this crash

---

### Post by hugolia on 2008-08-09
In the last week I started to had freezed desktop over an over again. There is some apllications that hangs as soon as i set them on screen, like "ktorrent". I didn't install any program when this strange behaviour starts. Last modification I did to the system was some system sugested update.
The strange thing is that the screen freeze with half drawing windows, keyboard does not respond, but mouse pointer continue working!
System is still responding to network, and I can ssh to it in order to restart the system gracefully.
I tried reconfiguring X system, and video driver but have no success.
Any idea? 
Do I have to install the whole system again?
Hugo

---

### Post by skip mcshwang on 2008-08-11
I haven't found an answer to this either. My panel has been freezing every couple of days lately. Restarting gnome doesn't help so I have to restart the PC :(

---

### Post by woaibbhemm on 2008-08-12
hello~
    nice   to  meet  you   and     thank  you   for   youe   sharing ,  welcome   to   our   website  !












Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

### Post by lnthai2002 on 2008-08-12
> **hugolia said:**
> 
The strange thing is that the screen freeze with half drawing windows, keyboard does not respond, but mouse pointer continue working!
Hugo
i got this problem once, I think after I install the trackpoint manager and run it under sudo.

---

### Post by starcannon on 2008-08-12
If you would like to restore gnome-panel back to default and start from fresh:

Assuming you'll be using this guide, be sure to use ALT-TAB to cycle between the terminal and your web-browser, as the first command will make the panels disappear entirely.

Do to a [known bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/188174") skip the parts in italics:
[I][SIZE=1]completely remove gnome panel from current session
```
gnome-session-remove gnome-panel
```[/SIZE][/I]remove all custom settings
```
gconftool-2 --recursive-unset /apps/panel
```[SIZE=1][I]start gnome-panels back up
ALT-F2: gnome-panel[/I][/SIZE]
restart gnome-panel workaround:
```
pkill gnome-panel
```gnome panels will return to view a few moments after this command is issued.

You now have the default set of gnome-panels back, modify till it breaks knowing you can always reset them with this series of commands.

---

### Post by lnthai2002 on 2008-08-13
i notice the following condition is more likely to cause crash: when i open a lot of applications(more than 6) --> many tabs on the panel then i move the mouse over the panel to unhide it then quickly move away then move back --> crash

---

### Post by SlushieGute on 2008-08-14
how do i open the terminal w/o the panels? and ALT-F2 doesnt seem to do anyhting. sorry im very new to this. thanks for the help

---

### Post by lnthai2002 on 2008-08-16
> **SlushieGute said:**
> how do i open the terminal w/o the panels? and ALT-F2 doesnt seem to do anyhting. sorry im very new to this. thanks for the help

If you are using gnome, then Atl-F2 should bring you the run window, type in "gnome-terminal" without quotes to open the terminal. For others windows manager, see this page for how to config 
[http://www.linuxforums.org/forum/linux-desktop-x-windows/5688-keyboard-shortcut-open-terminal-window.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/5688-keyboard-shortcut-open-terminal-window.html)

---


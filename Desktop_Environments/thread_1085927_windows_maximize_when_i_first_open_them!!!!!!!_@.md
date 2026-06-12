---
title: "windows maximize when i first open them!!!!!!! :@"
date: 2009-03-03
forum: Desktop Environments
---

### Post by hai_long21 on 2009-03-03
I was using Ubuntu 8.10... and all of a sudden one day, every time I open anything (folders, applications, internet... anything), I get a maximized window. On top of that, I can't see the title bars that include the close/minimize/maximize buttons. 

So everytime I want to unmaximize it, I have to press Alt, click on my window then move it. After that I can resize it. But when I want to maximize it again, the title bar is not there anymore.... and its annoying always having to click File --> close to close my windows.

thanks for the help!!!

---

### Post by NoaHall on 2009-03-04
Are you using Gnome and have you downloaded KDE files? 
If so, use the behaviour option and see if the "Current application's meun bar(Mac OS-style)" is selected, if it is, change it to "Desktop menu bar" or "None", that should fix your problem.
If you haven't, try going to System > Preferences > Advance Desktop Effects Settings, then under "Effects" make sure that "Window Decoration" box is ticked

Hope I helped.
Noah.

---

### Post by zephred on 2009-04-28
I am having the same problem, after upgrading to 9.04 (every new window appears as maximized, without any handle or title bar, I need to move it (with alt + mouse1) to have back to normal size + borders).
I had the package netbook installed, which might have changed some settings. I un-installed it, and re-booted, no change.
NoaHall, I do not find "behaviour option" nor "System > Preferences > Advance Desktop Effects Settings" in the menus.
Could this behavior be changed using gconf-editor ?

Thanks for any help,
Fred.

---

### Post by Kindath on 2009-04-29
I have the same problem as zephred; I just updated to 9.04 today and boom, all maximized windows with no title bar. If I unmaximize them, I get the title bar, but if I maximize back... no bar. Oddly, the Appearance Preferences window (System->Preferences->Appearance) doesn't have this problem; that one keeps the title bar when it maximizes. But that's the only exception I've found.

The Compiz Settings Manager has done me no good thus far; Window Decoration is on, as is Place Windows under Smart mode. As far as I can tell, everything is working except for auto-maximization with no title bars.

I'm running an nVidia GeoForce 7150M on an HP 9000 series Pavilion laptop, if that helps.

---

### Post by zephred on 2009-05-10
> **zephred said:**
> 
I had the package netbook installed, which might have changed some settings. I un-installed it, and re-booted, no change.

OK, problem solved for me: netbook also installed "maximus" ( [https://launchpad.net/maximus](https://launchpad.net/maximus) ). doing a 
```
sudo apt-get remove --purge maximus
``` solved it.

---

### Post by el_baby on 2009-06-04
> **zephred said:**
> OK, problem solved for me: netbook also installed "maximus" ( [https://launchpad.net/maximus](https://launchpad.net/maximus) ). doing a 
```
sudo apt-get remove --purge maximus
``` solved it.

Great!... this was my problem... one more note... since maximus is started by x-session-manager, you either have to logout/login again or (as I did) [s]kill the maximus process[/s]... **Noooooo**

Killing the process was **A Big Mistake(TM)**... One of my machines freezed, and in the other one, X-windows died...

Don't do this at home, kids... (but **do** logout/login in order for **maximus** to disappear)

---


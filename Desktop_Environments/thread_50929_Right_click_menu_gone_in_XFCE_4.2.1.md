---
title: "Right click menu gone in XFCE 4.2.1"
date: 2005-07-21
forum: Desktop Environments
---

### Post by DemiUrge8 on 2005-07-21
Long time lurker, first time poster. Yay. :)

I've recently started using XFCE4 as my window manager. Something about Gnome felt too... I dunno, Windows like. Wanted to try something different, without having to completely start over (Fluxbox). Everything was going fine until a couple days ago when my background image wouldn't take, and my right click menu wouldn't work.

I tracked down a thread that mentions this very problem (see here: [http://ubuntuforums.org/showthread.php?t=12004&highlight=xfce+background](http://ubuntuforums.org/showthread.php?t=12004&highlight=xfce+background) ) in Warty instead of Hoary, and it mentions Nautilus somehow being locked in the XFCE session, or something. I did what it said (xfdesktop &) and my wallpaper is back, but the menu's not. The thread died, so it almost looks like no one ever figured out what the problem was.

So here I am, begging for a solution. Obviously I'm running Hoary, kernel 2.6.10-5-386, XFCE 4.2.1 installed from Synaptic in the universe repository, I think. Everything's current, and the OS and Window Manager themselves are running just fine. Anyone have a suggestion? Thanks in advance. :)

EDIT: I should clarify a little and say that I'm not getting any menu when I right click. I just noticed that the thread I linked to said they were getting a nautilus menu. I get nothing.

---

### Post by psychicdragon on 2005-07-22
You're sure xfdesktop is running?
The desktop wallpaper for me doesn't go away even when I stop xfdesktop.

Run xfce-mcs-manager

Desktop > Menu tab

Make sure that "Show desktop menu" is checked.

If it's already checked, you should take a look at the menu file:
~/.config/xfce4/desktop/menu.xml

Maybe it got deleted or something?

---

### Post by bored2k on 2005-07-22
[QUOTE=psychicdragon]You're sure xfdesktop is running?
The desktop wallpaper for me doesn't go away even when I stop xfdesktop.

Run xfce-mcs-manager

Desktop > Menu tab

Make sure that "Show desktop menu" is checked.

If it's already checked, you should take a look at the menu file:
~/.config/xfce4/desktop/menu.xml

Maybe it got deleted or something?[/QUOTE]
 Perhaps he just opened nautilus without the --no-desktop shortcut, thus it taking over.

---

### Post by DemiUrge8 on 2005-07-22
Thanks for the replies.

"Show desktop menu" is checked. ~/.config/xfce4/desktop/menu.xml is there and correct. Nautilus isn't running, unless typing "killall nautilus" is wrong or lying to me. I have a normal XFCE4 menu on my panel, just no right click menu.

If I log out of XFCE and go back in from GDM, the background disappears again, replaced by a solid brown background, presumabily from Gnome's Human theme.

I'm beginning to wonder if I should uninstall XFCE4 and start over fresh. Will doing a complete removal in Synaptic wipe out all the config files as well, or is there a better way to do that with apt-get? Surely there's a fix somewhere, somehow.

---

### Post by yay4furryanimals on 2005-07-23
I have this same problem with xfdesktop.

When I first installed the xfdesktop ran just fine.  Then I don't know if I updated something or what, but upon further reboots xfdesktop would no longer run.

Still looking into it, seems like nautalis is hijacking it.

---

### Post by yay4furryanimals on 2005-07-23
Somehow I was able to restore xfdesktop and make it stay put:
[B]ps -ef | grep nautilus
kill -9 <pid>
xfdesktop &
[/B]

---

### Post by DemiUrge8 on 2005-07-24
[QUOTE=yay4furryanimals]Somehow I was able to restore xfdesktop and make it stay put:
[B]ps -ef | grep nautilus
kill -9 <pid>
xfdesktop &
[/B][/QUOTE]
 I ended up removing every XFCE package i could find and reinstalling. I cheated. Glad to hear you got your situation worked out though. :)

---

### Post by yay4furryanimals on 2005-07-24
[QUOTE=DemiUrge8]I ended up removing every XFCE package i could find and reinstalling. I cheated. Glad to hear you got your situation worked out though. :)[/QUOTE]

Was worth it thought right? :)  The proper font sizes alone make me happy.

---

### Post by DemiUrge8 on 2005-07-24
[QUOTE=yay4furryanimals]Was worth it thought right? :)  The proper font sizes alone make me happy.[/QUOTE]
 Yeah, there's something oh so satisfying about something actually working. :)

---

### Post by v2.0 on 2005-09-28
the whole thing with the xfdesktop doesn't stay. might work for some people, don't know how since your just running xfdesktop for that one sesh but cool if it does. so, anyone have a solution that sticks?? tanks

---

### Post by psychicdragon on 2005-09-28
Wow, this is an old thread.

For anyone still having trouble, please try this out:```
killall nautilus
killall xfdesktop
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
xfdesktop &
```

Make sure to save your session when you log out.

---

### Post by 762 on 2006-07-12
This worked for me.

From the Xfce Menu
Settings > Desktop Settings > check "Allow Xfce to manage the desttop"

Once I checked the box, my wallpaper and most importantly, the right-click menu came back and the settings remained persistent after rebooting.

Running Ubuntu kernel 2.6.15

---


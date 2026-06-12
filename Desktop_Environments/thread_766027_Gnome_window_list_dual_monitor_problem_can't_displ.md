---
title: "Gnome window list dual monitor problem can't display windows from other screen"
date: 2008-04-24
forum: Desktop Environments
---

### Post by underwater on 2008-04-24
Hello,

I have a weird problem that I did not have in Gutsy.  I have my dual monitors working and correctly configured in the position that I want, and I think they are configured the same way that I used to configure them, though I don't quite remember, but window lists are being a big hassle.

I have 2 panels--1 on each screen
Only the one on the right screen has a window list that shows what programs are open
Unfortunately, I have this weird problem that it won't show that it knows a window is open unless that window is currently positioned on its screen.  SO if I say have calculator open on screen 1 the window list that is on screen 2 won't show it.  If I drag the calculator and move it over to screen 2, then it will appear in the window list.


Any ideas?

Nvidia and I'll post xorg info if people feel it is relevant, but I'm not sure it is right now.  (Using Twinview right now, going to mess around and see if something else helps)

---

### Post by rcasha on 2008-11-10
Did this get solved?

---

### Post by matthurne on 2008-11-24
I have this issue as well; whether I have any panels on the secondary screen or not makes no difference.  I added a panel to the secondary screen, and added a Window List item to that panel.  It is just empty; it doesn't show windows from either screen.  So the only way I can get windows on the secondary screen to show up in a Window List is to configure that Window List to "Show windows from all workspaces", which is not what I want.

I'm running Intrepid.

---

### Post by sterni1971 on 2008-11-26
intrepid/32bit/metacity/Gnome 2.24.1 

The same issue here. 

Looks like an old bug which pop up again 
I found in the redhat bug tracker:
[https://bugzilla.redhat.com/show_bug.cgi?id=138874](https://bugzilla.redhat.com/show_bug.cgi?id=138874)

regards!

sven

---

### Post by jckdnk111 on 2008-12-02
This is such an annoying bug.
Has anyone found a workaround for this?

---

### Post by NcScZ on 2008-12-03
I was able to get it to work by
[LIST]
[LIST]
[*]Add a panel to secondary screen
[*]add a window selector to the new panel
[*]drag the icon that shows left of the window selector to the right side of the selector
[/LIST][/LIST]

After doing this the applications on the secondary screen appear on the panel on that screen & applications on the primary screen show on that panel.

---

### Post by hakanurhan@gmail.com on 2008-12-24
Hi guys. I've had the same problem and I have been searching for an answer for days. I'm using Ubuntu 8.10 and I believe I do have a solution. At least it works for me :).

1. Using the System->Preferences->Screen Resolution, adjust the monitors so that their bottoms are aligned. I used to align their tops but apparently thats the problem.
2. If you don't have a panel in the second monitor add one.
3. Move the new panel to the bottom of the second monitor.
4. Add a "Window List" to this panel and Voila! you'll have your windows in your second monitor only.

That's the solution for me. I hope it works for you as well

---

### Post by olmecnz on 2009-04-06
I was having this issue and tried those things recommended above. The thing that finally worked for me was right clicking on the empty window list on my second monitor, choosing preferences from the popup menu and then in the preferences I chose "show windows from all workspaces"

I only have one workspace on my setup and I though this would result in windows from both screens showing on my panel on the second monitor but it did not. Only the windows from monitor 2 were listed.

---

### Post by c0mp13371331337 on 2009-04-13
I *had* this working the way I wanted.  That is, I have my primary (left) monitor with the panels and my secondary (right) monitor with no panels.  My window list showed all windows from both monitors of the current workspace.  However, I just moved my window list and it disappeared (crashed?) so I re-added it.  Now it's only showing windows on my primary monitor.

If I move the panel to the secondary monitor, it only shows those windows on that monitor.  Moving it back changes the window list back to the windows on the primary monitor.  I'll try a couple of the fixes here and will report back.

---

### Post by c0mp13371331337 on 2009-04-13
Yeah.... no.... nothing's working for me.  Using nvidia graphics drivers and TwinView, all configured using nvidia-settings.  All on an up-to-date version of Intrepid 64.  If any one has any ideas, please share!
:guitar:

---

### Post by oi_antz on 2009-07-17
Have a real close look at your panels and remove any extra "window list"  panel items that may have been added. Once I had done that, the sole window list now lists all windows in the current workspace, even windows positioned on the right monitor.

---

### Post by jalbert on 2010-10-23
@oi_antz: Thanks, it really solved my problem.
On my dual monitor desktop I had two panels on my primary screen.
Removing window list from the second panel made the list of applications now complete.

---

### Post by sidragon on 2011-05-05
> **oi_antz said:**
> Have a real close look at your panels and remove any extra "window list" panel items that may have been added. Once I had done that, the sole window list now lists all windows in the current workspace, even windows positioned on the right monitor.

This fix works. And this applies to Ubuntu 11.04 (in Classic mode), as well. Look carefully for that small Window List tab.

---

### Post by Unsynced on 2011-08-05
> **oi_antz said:**
> Have a real close look at your panels and remove any extra "window list"  panel items that may have been added. Once I had done that, the sole window list now lists all windows in the current workspace, even windows positioned on the right monitor.
Thanks! This was the issue for me too.

---

### Post by apast on 2012-11-15
If UI doesn't help, remove manually gconf-editor respective to Window List applets instances.

These folders can be found at:

```
~/.gconf/apps/panel/applets/<applet-name>
```

After remove folers, configurations keeps in memory. Restart your gnome session (i.e.: ```
gnome-session-save --logout
``` command)

Regards,

AndPast

---

### Post by oldos2er on 2012-11-15
Old thread closed; please don't bump old threads.

---


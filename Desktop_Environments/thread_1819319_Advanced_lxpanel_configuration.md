---
title: "Advanced lxpanel configuration"
date: 2011-08-05
forum: Desktop Environments
---

### Post by whatthefunk on 2011-08-05
Ive been messing around with my lxpanel for the last few days just trying to see what I can get it to do.  Im actually amazed at what can be done with it and how easy it is to configure. 

However, there are some things that I cant seem to do.

-I want the corners of the panel to be rounded.  I can of course do this be creating an image with rounded corners, but because LXDE only offers false opacity, the panel only appears to have rounded edges when it is against the background.  When it is against a window, the rounded corner effect is ruined by little bits of the background sharpening the edges.  Is there any way to do this?

-I want to change the system clock to anything else.  By default, it seems that there are only two options...a small, boring digital clock and a hard to read wall clock.  Is there any way to get a different clock?

-Is there any way to get two panels to appear on the bottom?  You can have one on the top and one on the bottom, but I would like to have one centered in the bottom and another small one on the right on the bottom.  Is this possible?

---

### Post by kerry_s on 2011-08-06
1. xcompmgr maybe ?
2. no, xclock ? lol
3. no

---

### Post by kerry_s on 2011-08-06
with xcompmgr & docky on lubuntu(lxde).

---

### Post by whatthefunk on 2011-08-06
Hey thats pretty nice looking.  I never considered using xcompmgr + docky...is that resource intensive?  Im on kind of a low spec system...

So far Im stuck with this (attachment).  I feel like Im heading in the right direction, but its not quite what I want it to be.

---

### Post by kerry_s on 2011-08-06
on mine it's using the exact same memory as it was using before, no more, no less.

mines an atom n270 1.6ghz, 2gb ram. its a nettop.

---

### Post by whatthefunk on 2011-08-06
Hmmm...Ill give that a shot.

Some further tweaking on lxpanel has got me this (attachment).  This one is closer to what I want.  I lost my shutdown button though...how do I get that back?  I didnt see it listed anywhere in the program menu.  Also, how do you change the icon for shutdown?  The stock one is a little blurry...

---

### Post by kerry_s on 2011-08-06
i went to /usr/share/applications & switched to root, then opened shutdown in leafpad. changed the icon to just "exit".

you'll need to edit that file to unhide the shutdown.
change "NoDisplay=true" to "NoDisplay=false"

you can change it back after you get it back on the panel.

---

### Post by whatthefunk on 2011-08-06
There is no shutdown file in my /usr/share/applications...  Maybe I need to make another one?  Not quite sure exec to point it to...

---

### Post by kerry_s on 2011-08-06
strange. here's what mine has.

```
[Desktop Entry]
Name=Shutdown
Name[zh_TW]=&#38364;&#27231;
Comment=Shutdown or Reboot
Icon=exit
Exec=lubuntu-logout
NoDisplay=true
```

---

### Post by whatthefunk on 2011-08-06
Ahhh....I was going to the directory in the terminal and there its listed as lubuntu.logout.  Didnt even think about trying the file manager (so thats what its for!)  Live and learn I guess.  
I restored the default panel before I realized this and am starting again from scratch.  Screen shots to follow.

---

### Post by whatthefunk on 2011-08-07
Making progress now.  Im really surprised at how much you can do with such a simple light weight panel.

Is there anyway to edit the items in the system tray?

---

### Post by kerry_s on 2011-08-07
> Is there anyway to edit the items in the system tray?

what do you mean? edit how?

---

### Post by whatthefunk on 2011-08-07
> **kerry_s said:**
> what do you mean? edit how?

I cant seem to get rid of the wireless connection icon.  I dont use wireless so dont want it.  I cant find any way to disable it without loosing the whole system tray.

---

### Post by kerry_s on 2011-08-07
There only 1 network icon, it should change with the connection type.
Like on mine I'm wired so I have 2 up/down arrows. 
 Let me check your pic again, be back.

yours looks strange, what is the green icon with down arrow?

---

### Post by whatthefunk on 2011-08-07
I dont connect with NetworkManager...I use pppoeconf.  Maybe thats what the problem is?

---

### Post by whatthefunk on 2011-08-07
> **kerry_s said:**
> yours looks strange, what is the green icon with down arrow?

That would be Guake, the terminal I use.

---

### Post by kerry_s on 2011-08-07
See if you can kill network manager. 
killall networkmanager

---

### Post by whatthefunk on 2011-08-07
That gets rid of it, but then network manager starts up again automatically.  Weird...

---

### Post by kerry_s on 2011-08-07
> **whatthefunk said:**
> That gets rid of it, but then network manager starts up again automatically.  Weird...

i figured that would happen. go to /etc/xdg/autostart
edit network manager with leafpad as root, put a #(comment) in front of the exec line. that should stop it, just log out & back in.

---

### Post by whatthefunk on 2011-08-07
Its still there...  Ahhh...network manager, my arch nemesis.  The only thing it seems to be good at is not going away.

---

### Post by kerry_s on 2011-08-07
See if it's in your ~/.config/autostart

---

### Post by whatthefunk on 2011-08-07
Nope, its not there.  Theres a network manager file in init.d...maybe thats the culprit?

---

### Post by kerry_s on 2011-08-07
maybe we're over thinking it. in the menu(preferences-> desktop session settings) try checking it an unchecking it, that should create a autostart file to turn it off in ~/.config/autostart.

---

### Post by whatthefunk on 2011-08-07
Maybe got it.  The problem is, Ive found, not with the program Network Manager but with the nm-applet.  If I kill the nm-applet, the icon goes away.  I think Ive solved this...well see after my next reboot.

Thanks for all the help kerry_s.

---

### Post by kerry_s on 2011-08-07
good to hear. i got this thread subscribed, so i'll get a email if you need help. my mail app is set to check every 30min so you won't have to wait long.

---


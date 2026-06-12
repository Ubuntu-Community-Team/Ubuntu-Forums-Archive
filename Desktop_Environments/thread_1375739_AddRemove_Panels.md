---
title: "Add/Remove Panels"
date: 2010-01-08
forum: Desktop Environments
---

### Post by goodlukeing on 2010-01-08
I am just messing around with Avant Window Manager and Screenlets at the moment to try and see if I can get used to a panel-less desktop. But (for once) I thought ahead and realised if I delete the panels I can't right-click them to add them back if I don't like the panel-less idea.

So my question here is: Is there an easy way (preferably GUI-based) to add a new (or the default) panels back when you have none at all.

---

### Post by ssulaco on 2010-01-08
Take a look at these threads,hope it helps,
[http://ubuntuforums.org/showthread.php?t=392387](http://ubuntuforums.org/showthread.php?t=392387)
[http://ubuntuguide.net/how-to-restore-the-default-gnome-desktop-panels-in-ubuntu](http://ubuntuguide.net/how-to-restore-the-default-gnome-desktop-panels-in-ubuntu)

---

### Post by nothingspecial on 2010-01-08
This isn`t really advisable but what I do is

```
sudo mv /usr/bin/gnome-panel ~/.panel
```

To get it back

```
sudo mv ~/.panel /usr/bin/gnome-panel
```

---

### Post by chrisinspace on 2010-01-08
I haven't tried, but you can probably do it through the [gconf-editor]("http://en.wikipedia.org/wiki/Gconf-editor").

---

### Post by chrisinspace on 2010-01-08
Oh yeah...and if you are trying to go panel-less you might also want to play with Compiz if your system can handle it.  It gives you some nice mouse-navigation otpions like [Expo]("http://wiki.compiz.org/Plugins/Expo"), [shift-switcher]("http://wiki.compiz.org/Plugins/Switcher#Shift"), and [Show desktop]("http://wiki.compiz.org/Plugins/Showdesktop").  You can assign a corner of your screen to each of these.  Then when you move your pointer to the top-right, for example, it can trigger Expo and you can see all of your virtual desktops.  I hide my panels and do most of my navigation in this way.

You should also check out Gnome-Do.  That was the component that just about got me off of the panels forever.  Like I said, I still have them auto-hide so I can fall back if i need to, but I find myself using them less and less.

---

### Post by Belizeian on 2010-01-08
what I do is just make gnome-panel none executable, then killall gnome-panel and things are golden if I need it back and I haven't in months I can just make it executable again.

sudo chmod -x /usr/bin/gnome-panel
killall /usr/bin/gnome-panel

**AND TO GET IT BACK**
sudo chmod +x /usr/bin/gnome-panel


Things to note are that you will lose ALT-F2 and menu hotkeys.

But I use gnome-do which is like ALT-F2 on steroids.  And Avant basical so I can access what's running but I keep it autohid. and Compiz for effects and window management inculdeing the ability to tile windows, which is something gnome should do by itself.

---

### Post by nothingspecial on 2010-01-08
Plus one for gnome-do, who needs panels, or docks, or window decoration, or a mouse?

[ATTACH]142907[/ATTACH]

---

### Post by chrisinspace on 2010-01-08
> **Belizeian said:**
> what I do is just make gnome-panel none executable, then killall gnome-panel and things are golden if I need it back and I haven't in months I can just make it executable again.

sudo chmod -x /usr/bin/gnome-panel
killall /usr/bin/gnome-panel

**AND TO GET IT BACK**
sudo chmod +x /usr/bin/gnome-panel


That's a good approach.  I might give that a try.  Like you said, with Gnome-Do, you don't really need Alt-F2.

Off-topic: Belizeian!?  I LOVE Belize..favorite place on earth!

---

### Post by goodlukeing on 2010-01-09
Wow, that was a ton of responses. And yes I am already using Compiz and Gnome Do which I agree is "like ALT-F2 on steroids". Well these methods seemed to work, I liked this one the most:

```
sudo chmod -x /usr/bin/gnome-panel
killall /usr/bin/gnome-panel
```

**AND TO GET IT BACK**

```
sudo chmod +x /usr/bin/gnome-panel
```


I decided that I might just remember the location /usr/bin/gnome-panel. Then use the sudo nautilus thing go to it, right click it, go to permissions and click "make executable" or whatever it is. This way I don't have to remember much code (although very simple) and it can be more GUI based. And I risked it and tested it, and yes it worked fine.

PS: (I got a tad worried when I typed in "sudo chmod +x /usr/bin/gnome-panel" and nothing happened, but then I realised I had to actually run the gnome-panel)

Thanks guys for your help.

---

### Post by Albert Net on 2010-01-09
It is pretty easy to add/remove gnome-panels when there is at least one available.

```
sudo chmod -x /usr/bin/gnome-panel
killall /usr/bin/gnome-panel
``` 

This method in fact make gnome-panel inaccessible for everyone, which is probably not our purpose. 

Choose to not use gnome-panel is just your own preference, which should affect the whole environment of ubuntu. The consequence of the above method is disastrous for other ordinary users.

---


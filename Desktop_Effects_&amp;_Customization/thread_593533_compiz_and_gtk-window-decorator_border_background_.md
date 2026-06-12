---
title: "compiz and gtk-window-decorator border background issue - but not missing"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by Psykotik on 2007-10-27
Hi all,

Using either gtk-window-decorator or compiz gives me the same result : a border and a shadow with a strange background (see the picture).

It looks like there was a background picture, since moving the windows change also the background.

This effect is quite ugly; is there any means to get rid of it ? I've tried to check emerald options, gtk and compiz, with no luck.

Any idea?

---

### Post by Psykotik on 2007-11-02
I found what the problem was : this strange "reflexion" compiz plugin.

I deactivated it, and now I can enjoy a nice compiz. I'm wondering if anyone use that ugly compiz plugin...

---

### Post by Forlong on 2007-11-02
> **Psykotik said:**
> I'm wondering if anyone use that ugly compiz plugin...
LOL, you just used it wrong. It must be used on a transparent theme.

I'm glad you worked it out yourself, though. Isn't that a great experience? :)

---

### Post by Psykotik on 2007-11-02
> **Forlong said:**
> 
I'm glad you worked it out yourself, though. Isn't that a great experience? :)
The best one ! :)

---

### Post by engstrom on 2008-01-14
I've noticed that using the crux theme and then turning desktop fx on means I get the same problem i.e. the window decoration of the blocks disappear, the bar becomes semi-transparent and has gone  a dark red rather than purple. I don't have the reflection plugin enabled though...

After poking around some forums I've found that opening a terminal and typing "gtk-window-decorator --replace &" the windows look as expected...
But how to include this so it gets run (or indeed making compiz look like this so I don'tneed to run it) each time compiz kicks off
I've tried launching ccsm and inserting the correct command in 'decoration' plugin commandline configuration to no avail.

---

### Post by Forlong on 2008-01-14
Sounds like you have Emerald installed and don't want to use it.
Just remove it then:
```
sudo apt-get remove emerald && sudo apt-get autoremove
```

---


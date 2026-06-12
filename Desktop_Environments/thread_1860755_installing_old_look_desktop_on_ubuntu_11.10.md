---
title: "installing old look desktop on ubuntu 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by abdulrehman.ansari on 2011-10-15
I have recently installed ubuntu 11.10 (which has unity shell by default), i am not very much comfortable with Unity interface, i much used to classical gnome desktop (like it was in 9.4, 10.10),
after searching on net, i have tried all these:
[LIST]
[*]sudo apt-get install gnome-panel
[*]sudo apt-get install gnome-fallback
[*]sudo apt-get install gnome-shell
[/LIST]

I am able to get gnome classic option on login screen,but this gnome classic is not same as what it was on old editions, problems with this classic gnome:
[LIST]
[*]I am not able to control its panel (it is fixed not able to movie them, not able to add new panel)
[*]appearance window in system manager is totally different, i am not able to add my favorite theme.
[*]Compiz effect is not coming, i have install and try to configure it with CompizSettingManager, but still it not working. i use to enable compiz effect from appearance manager screen, visual effect tab, selecting Extra option on it, all these are missing in new appearance window.
[/LIST]

Any suggestion to how get all these features back?
Thanks in Advance.

---

### Post by 2F4U on 2011-10-15
My understanding is that Gnome classic is no longer developed and will therefore disappear. If you really don't like Unity or the new Gnome 3, what about using a different desktop environment? Personally, I am using KDE and XFCE at the moment and I am very satisfied with both.

---

### Post by Copper Bezel on 2011-10-15
Edit - Misread you there.

Compiz should be running unless you select the "No Effects" session. Try running compiz --replace and see what happens.

Hold Alt while right-clicking panel objects to get the menu to modify them. 

Look up gnome-tweak-tool for theme settings.

---

### Post by alenis on 2011-10-15
I would suggest switching to Xubuntu or Lubuntu too. Lubuntu is surpisingly good :)

---

### Post by Copper Bezel on 2011-10-15
[QUOTE=alenis]I would suggest switching to Xubuntu or Lubuntu too.[/QUOTE]
Honestly, I would suggest taking the time to figure out what a piece of software is capable of and how to make it work for you instead of basing your decisions on a first glance.

Again, there are easy answers to all of the questions above. Switching to a new DE entirely is going to mean more work and frustration in the long run. Using one of these simpler DEs like LXDE can be a fun learning experience, but it's still going to be far more limited and less polished than Gnome.

---

### Post by tartalo on 2011-10-15
> **Copper Bezel said:**
> Switching to a new DE entirely is going to mean more work and frustration (...) far more limited and less polished than Gnome.

I'm going to disagree with you here. In this moment Gnome 3 and Unity are the least polished and most frustrating DEs out there. if nothing else because they are unfinished. [www.google.com/search?q=gnome+3+touchpad](www.google.com/search?q=gnome+3+touchpad)

I recommend switching to another DE too. KDE is wow, XFCE is fast. They both do work as intended.

---

### Post by Copper Bezel on 2011-10-15
Gnome 3 may be new, but it's not "unfinished" - it's at full release status. I'm not certain what you're getting at with the touchpad issue - could you explain a bit more?

I said nothing about KDE, and it's a fine desktop environment. It's just not an answer to the question. The OP's question was how to beat Gnome into shape, and if that's what he actually wants to do, then it's a simple process, as I said. If he'd wanted suggestions on what to use in place of Gnome 3 because of problems inherent in Gnome 3, then that's a different question (to which KDE is the obvious answer.)

The last time I tried XFCE, which was under 10.10, I found it to be exceptionally brittle. Not unstable, exactly, but unpredictable with tasks like adding external monitors or tweaking keyboard settings. I can't really recommend it in good conscience. It's fast, but it doesn't really feel like a complete DE.

Unity isn't a desktop environment, so it doesn't make any sense to compare it to them. It's a Compiz plugin. You could run it over LXDE.

---

### Post by tartalo on 2011-10-15
> **Copper Bezel said:**
> Gnome 3 may be new, but it's not "unfinished" - it's at full release status.
So was KDE 4.0.

> **Copper Bezel said:**
> The OP's question was how to beat Gnome into shape
You are right, so I'll stop here. We can keep discussing the status of Gnome 3 and the alternatives in another thread if you want to.

---


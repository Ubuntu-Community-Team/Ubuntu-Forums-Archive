---
title: "Replacing Unity with AWN"
date: 2011-11-22
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-11-22
Have been using Xubuntu since 11.04. Just switched to Unity and am trying to like but... I detest the launcher on the left side.  I recently ran across [the following post]("http://www.andrewbolster.info/blog/2011/06/replace-unity-with-awn-and-gnome-do/"). This essentially replaces Unity with AWN. Just wondering whether anyone else has tried this?

---

### Post by bluexrider on 2011-11-23
I did almost the same thing with Lisa. Mints version and used Cairo-Dock. Seamed to work ok. After installing I logged out and back in under Cairo.

Good Luck

---

### Post by neu5eeCh on 2011-11-23
I should consider Cairo. I assume, when you logged back in the first time, you had to start Cairo?

---

### Post by Copper Bezel on 2011-11-23
Cairo Dock adds a custom session, so it's just like logging into Gnome Shell, Unity, Fallback, or Unity 2D. With AWN, you'd need to add it as a startup application and untick the Unity plugin in Compiz.

---

### Post by neu5eeCh on 2011-11-23
Hey, thanks for the tip Bezel. After you mentioned it, I looked it up and found the info [here]("http://www.webupd8.org/2011/09/cairo-dock-240-released-with-custom.html").

---

### Post by neu5eeCh on 2011-11-23
Just installed and tried Cairo Dock, but when choosing Cairo Dock Session, I still get the strange gnome panel (?) at the top of the screen: File, Edit, View, etc... 

Is this something I need to remove with gconf?

---

### Post by Copper Bezel on 2011-11-23
That's weird. 

* If it looks like a panel, run "System Monitor" and see if the Unity 2d panel is running.

* If it's just the menu text incongruously rendering over the wallpaper, do this instead, via _[markbl]("http://ubuntuforums.org/showthread.php?p=11472805#4")_:

```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

---

### Post by neu5eeCh on 2011-11-23
Here's what I found out. 

The mysterious bar on the top screen is caused by a bug in Nautilus. I did a little Google search and got lucky: "[How to remove the superior panel on "cairo dock with gnome" session?]("http://glx-dock.org/bg_topic.php?t=5686")"

This site takes one to the [following PPA]("https://launchpad.net/%7Ematttbe/+archive/ppa/+sourcepub/2036648/+listing-archive-extra"). So, doing the following fixed the problem:

> sudo add-apt-repository **ppa:matttbe/ppa**
sudo apt-get update
sudo apt-get upgradeSince installing Ubuntu yesterday, it seems like a less mature or flexible DE than Xubuntu. Seems rife with little bugs and limitations. Gnome3 doesn't work on my laptop - seems to be a show-stopping bug having to do with ATI. Gnome classic is awful. Has none of the flexibility of G2 - would choose Lubuntu over **that**.

**Edit: **If I were more so**f**isticated, I would combine all those commands into one.

---

### Post by PaulW2U on 2011-11-23
> **Copper Bezel said:**
> Cairo Dock adds a custom session, so it's just like logging into Gnome Shell, Unity, Fallback, or Unity 2D.

Yes it is. I installed it, logged out, selected Cairo Dock, logged back in and it's all working perfectly. I don't see the top panel that some others are reporting and with a bit of customisation I could have something that is quite usable.

I won't say it's better than Unity but it seems to be an alternative that's worth exploring and I have a Gnome 2 style menu as well. :)

---

### Post by neu5eeCh on 2011-11-23
Here's another option:

[http://www.andrewbolster.info/blog/2011/06/replace-unity-with-awn-and-gnome-do/](http://www.andrewbolster.info/blog/2011/06/replace-unity-with-awn-and-gnome-do/)

This weeds out Unity altogether.

---

### Post by neu5eeCh on 2011-11-23
Gotta' say, discovering all this has renewed my enthusiasm for Ubuntu. :guitar:

I try to like Unity, but using it is like wearing a straight jacket. I wish Shuttleworth all the best, but I'm grateful for all those who can give us alternatives.

---

### Post by makitso on 2011-11-23
This thread was originally about AWN.  I have not been able to use AWN with Unity on 11.10.  I tried hiding the Unity dock but every time I move a desktop icon or launch something from AWN, the dock pops out.  So, I switch to the Gnome 3 shell.  Now it works very well.

---

### Post by neu5eeCh on 2011-11-23
> **makitso said:**
> This thread was originally about AWN.  I have not been able to use AWN with Unity on 11.10.  I tried hiding the Unity dock but every time I move a desktop icon or launch something from AWN, the dock pops out.  So, I switch to the Gnome 3 shell.  Now it works very well.

If you read the links I provided, and you're not going to use Unity anyway, try deleting as per the folllowing:

> sudo apt-get remove unity unity-asset-pool unity-place-applications unity-place-applications

---

### Post by neu5eeCh on 2011-11-23
OK, well, anybody who goes this root will probably want three items, gnome-do, xbindkeys, and the other is gmrun. The three can be installed via repositories.

The problem is that Alt-F2 no longer works in the Cairo or AWN environment, so that if you want to *gksu nautilus*, you have to do it Terminal (or at least that was the only alternative I could come up with). I used xbindkeys to create a run command with gmrun:

> sudo apt-get install xbindkeysCreate Initial Config File:

> xbindkeys --defaults > $HOME/.xbindkeysrc3. Edit ~/.xbindkeysrc and add to the end of the file:

> "gmrun" 
Alt+F2It's not as slick as a lens, but it works better and more efficiently IMHO.

And because I'm not Linux savvy enough to figure these things out by myself, here are my sources:

[http://ubuntuforums.org/showpost.php?p=10799169&postcount=8](http://ubuntuforums.org/showpost.php?p=10799169&postcount=8)

[http://amirtinkering.com/64/replacing-unitys-run-command-with-gmrun/](http://amirtinkering.com/64/replacing-unitys-run-command-with-gmrun/)

**Edit: **Don't forget to add xbindkeys to startup.

---

### Post by jerrrys on 2011-11-23
I actually like the unity-launcher-panel and have incorporated into my gnome-classic desktop.  You said that you dislike the side panel, gnome-classic does not have one. And I have ran AWN and Docky on it.

---

### Post by Copper Bezel on 2011-11-23
I'd use Synapse instead. It's Zeitgeist-powered and semantic like Unity's bar and very quick, but still takes arbitrary bash commands.

You can also just add it as a keyboard shortcut in Compiz's Commands plugin.


[QUOTE=makitso]This thread was originally about AWN. I have not been able to use AWN with Unity on 11.10. I tried hiding the Unity dock but every time I move a desktop icon or launch something from AWN, the dock pops out. So, I switch to the Gnome 3 shell. Now it works very well.[/QUOTE]
I don't mean to discourage you from Shell, which is brilliant, but the idea is replacing Unity entirely. If it's still running at all, you need to turn it off in Compiz. (Just untick the Unity plugin.)

---

### Post by neu5eeCh on 2011-11-23
> **jerrrys said:**
> I actually like the unity-launcher-panel and have incorporated into my gnome-classic desktop.  You said that you dislike the side panel, gnome-classic does not have one. And I have ran AWN and Docky on it.

Jerrrys, what do you make of the following:

[https://lh3.googleusercontent.com/-qKvluvJa1zs/ToMX2r7l4WI/AAAAAAAAGDo/8FOZDVCQwn0/cairo-dock-panel-mode.png](https://lh3.googleusercontent.com/-qKvluvJa1zs/ToMX2r7l4WI/AAAAAAAAGDo/8FOZDVCQwn0/cairo-dock-panel-mode.png)

Is that an XFCE panel on the top, or a Gnome panel? I like that look. Very clean.

---

### Post by jerrrys on 2011-11-23
Looks like gnome-classic with conky installed.  The ubuntu main menu icon could be the new menu extention i have heard about.  Im running gnome-fallback and it looks like this

[ATTACH]207857[/ATTACH]

---

### Post by neu5eeCh on 2011-11-23
> **jerrrys said:**
> Looks like gnome-classic with conky installed.  The ubuntu main menu icon could be the new menu extention i have heard about.  Im running gnome-fallback and it looks like this

[ATTACH]207857[/ATTACH]

I don't see conky? That's Cairo Dock on the bottom. The top just doesn't look like gnome-fallback to me... but maybe it is. I was trying to reproduce it. I think I'd have to do quite a bit of googling to make the gnome-fallback panel look like this.

---

### Post by jerrrys on 2011-11-23
just a guess, but i dont know.  looks doable to me

---

### Post by neu5eeCh on 2011-11-23
> **Copper Bezel said:**
> I'd use Synapse instead. It's Zeitgeist-powered and semantic like Unity's bar and very quick, but still takes arbitrary bash commands.

Installed synapse and have been using it. I'm sold.

So far... I have Cairo dock all but invisible (since it's buggy) and have AWN running on the right side. AWN seems more responsive, cleaner and quicker - but that may be subjective. Between AWN & synapse, I've got everything I need. I have a clock and workspace switching applet running on the desktop - compliments of Cairo Dock.

---

### Post by jerrrys on 2011-11-23
show us a pic :)

---

### Post by neu5eeCh on 2011-11-23
> **jerrrys said:**
> show us a pic :)

OK... I'll post a pic tomorrow morning. Me and my boring desktop. 8-)

---

### Post by wildmanne39 on 2011-11-24
Hi, I have unity with the left launcher hidden and awn at the bottom of the screen with an application menu like gnome2 on it so it is easy to access.

---

### Post by neu5eeCh on 2011-11-24
OK, as promised, my awe-inducing desktop. You should be able to click on this to see it in all it's heart-faltering glory.

[[IMG]http://poemshape.files.wordpress.com/2011/11/screenshot-at-2011-11-24-083042-reduced.jpg[/IMG]]("http://poemshape.files.wordpress.com/2011/11/screenshot-at-2011-11-24-083042.jpg")

**Edit:** This, by the way (for anyone who hasn't been following) is "Unity", Ubuntu 11.10, using the Cairo Desktop with Gnome effects. No panel, which seems needless to me, and no launcher. AWN, to me, is a much better launcher and on the right side of the screen.

---

### Post by jerrrys on 2011-11-24
A clean and functional unity desktop, nice going VTPoet

---

### Post by neu5eeCh on 2011-11-24
Thanks, I just used Ubuntu Tweak to move the buttons back to the right and I think I'm all set until 12.04 comes out. Then I'll decide not to upgrade and crumble within a week.

---

### Post by jerrrys on 2011-11-24
12o4 will be supported for five years and I for one am looking forward to that.

---

### Post by bluexrider on 2011-11-25
> **VTPoet said:**
> OK, as promised, my awe-inducing desktop. You should be able to click on this to see it in all it's heart-faltering glory.

[]("http://poemshape.files.wordpress.com/2011/11/screenshot-at-2011-11-24-083042.jpg")

**Edit:** This, by the way (for anyone who hasn't been following) is "Unity", Ubuntu 11.10, using the Cairo Desktop with Gnome effects. No panel, which seems needless to me, and no launcher. AWN, to me, is a much better launcher and on the right side of the screen.


So you ended up with the best of AWN and Cairo. Nice job! I'll have to re-think adding AWN to my desktop.

---

### Post by neu5eeCh on 2011-11-25
> **bluexrider said:**
> So you ended up with the best of AWN and Cairo. Nice job! I'll have to re-think adding AWN to my desktop.

I'm super pleased with the results. I use Xubuntu on my smaller and older laptop (and have it set up almost identically), but XFCE lacks some of the refinements of Gnome. Being able start up a Cairo session, rather than Gnome Shell or Unity, is a fantastic innovation for those of us who like neither Gnome Shell nor Unity but want the benefits of gnome, unity and compiz under the hood. For instance, I activated the grab handles (so I get that part from Unity).

I tried Cairo through and through, but AWN seems a little cleaner, simpler and more stable.

---


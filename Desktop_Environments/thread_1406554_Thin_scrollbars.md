---
title: "Thin scrollbars"
date: 2010-02-14
forum: Desktop Environments
---

### Post by smokyink on 2010-02-14
First of all sory if the tread is in the wrong place... 

As the title says, I want to set the window scrollbars to be thinner.  I hate wasting screen space, besides I usually use the mouse scroll or the arrow keys...                                                                                                                                                 

I have gnome, compiz and a some themes that I have added.                                                                                                                                                  

Is it possible to set all window scrollbars to say 5-6 px or even less?   

If yes how do I do  that? 

I mean is there a config file somewhere or is it theme dependent?

---

### Post by howefield on 2010-02-14
This would take care of most of them, but some extra applications may ignore it, eg Chrome.

Type the following in a terminal

```
gedit ~/.gtkrc-2.0  --
```

And paste the following into it, where "6" equals the pixel width that you require for your scroll bar, 6 is what I use. Save and close. 

```
style "scroll"
{
    GtkScrollbar::slider-width        = 6
}

class "*" style "scroll"
```

---

### Post by smokyink on 2010-02-14
Wow that is great I will try it now.

By the way if .gtkrc doesn't exist I create one right? Also do I need to log-out/log-in for the changes to take effect?

Edit:

Just tried it and .gtkrc has to be created if not there. Also log-out and then log back in for changes to take effect.

Works great. Thanks [howefield]("http://ubuntuforums.org/member.php?u=186490"). :)

---

### Post by howefield on 2010-02-14
> **smokyink said:**
> By the way if .gtkrc doesn't exist I create one right? Also do I need to log-out/log-in for the changes to take effect?

It most likely doesn't exist, the terminal command I gave will create the empty file for you. You won't need to logout/back in, simply restart the program.

> Is there a wiki on things like that? I searched the forum and google...but couldn't find

I have used this since about 7.04, maybe earlier and got it from the ever helpful Robbie Ferguson of Category5.tv

---

### Post by smokyink on 2010-02-14
Thanks for all  the help :)

---


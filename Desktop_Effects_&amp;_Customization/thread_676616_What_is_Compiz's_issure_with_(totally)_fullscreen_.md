---
title: "What is Compiz's issure with (totally) fullscreen windows?"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2008-01-23
I can't watch videos in VLC's fullscreen mode because the video messes up and for some reason it makes VLC somewhat transparent.
I can't use the Elisa media center program because Compiz keeps making it flicker in and out of visibility trying to show my desktop for some reason. 

I don't really know how to describe it. But really, what is with Compiz and fullscreen things? Why don't they play well?


Just FYI, when I say fullscreen, I mean literally fullscreen. Covering the panels and AWN, everything.

---

### Post by Thanoulis on 2008-01-24
I'm not sure of what you're talking about...
I had some kind of same problems with VLC's full screen in 7.04, but after i upgraded to 7.10, it gone!
Are you having Direct Rendering enabled?

---

### Post by rainwalker on 2008-01-24
How do I check if I do?

---

### Post by theRightNee on 2008-01-24
```

glxinfo | grep direct

```
to find out if you have direct

---

### Post by rainwalker on 2008-01-24
> **theRightNee said:**
> ```

glxinfo | grep direct

```
to find out if you have direct

Yep, I do.  ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by gurukreff on 2008-03-13
I have the exact same problem (i'm using Gusty) and i don't have any idea of how to solve it.
It conflicts with compiz, because, when i turn it off it doesn't give me that problem anymore.
Any thoughts?

---

### Post by chapterthree on 2008-04-19
> **gurukreff said:**
> I have the exact same problem (i'm using Gusty) and i don't have any idea of how to solve it.
It conflicts with compiz, because, when i turn it off it doesn't give me that problem anymore.
Any thoughts?

I'm having the same issue as well.  I heard somewhere that it is being caused by the [relatively] older Nvidia driver that is in Gusty stable.  I'm looking forward to see if Hardy fixes this issue.

---

### Post by rainwalker on 2008-04-19
Actually, I managed to fix it by adding "fullscreen" to the list of windows with 100% opacity

---

### Post by chapterthree on 2008-04-19
> **rainwalker said:**
> Actually, I managed to fix it by adding "fullscreen" to the list of windows with 100% opacity

Can you please elaborate on what exactly you did so that I can try the same thing?  Thanks!

---

### Post by mgmiller on 2008-04-19
You need to have the compiz config settings manager installed:
```
sudo apt-get install compizconfig-settings-manager
```

Once that is installed, go to System > Preferences > Advanced Desktop Effects Settings.

In there, click on the General Options, then go to the Opacity settings tab.
You will see a drop down for Window Opacities.  It is blank by default.  Click on the +Add button to add the things you want to vary the opacity for.
To answer your question, you would add to "opacity windows area" fullscreen and in the "opacity window value" area put in 100.

I think there is a bug in the slider to select the value, it seems to give very weird numbers.  Just type a number into the box.

There are many things you can change the opacity for.  Here is a list of what I have:
dock   85
dropdownmenu  90
popupmenu  90
tooltip   85
notification  85

I am sure there are more, I just don't know what they are.

---

### Post by chapterthree on 2008-04-19
Ah OK, thanks, I'll keep that on tap.  It seems that I may have fixed my issue by installing xserver-xgl.  I'll have to run a few more tests, but so far I haven't had any issues since installing xserver-xgl.

---


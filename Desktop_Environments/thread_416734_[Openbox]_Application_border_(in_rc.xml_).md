---
title: "[Openbox] Application border (in rc.xml ?)"
date: 2007-04-21
forum: Desktop Environments
---

### Post by freduardo on 2007-04-21
Hello!

I just did a fresh install of Feisty on my old laptop (only a CLI system with openbox, etc...).

I wanted to get a transparent terminal "embedded" in my desktop.
So I installed rxvt-unicode. Added this to my .Xdefaults file:

> ## urxvt config
urxvt.font:             xft:Dejavu Sans Mono:size=8
#urxvt.background:       black
urxvt.foreground:       #004500
urxvt.scrollBar:        false
urxvt.borderless:	true
urxvt.geometry:		84x24
urxvt.tintColor:        white
urxvt.fading:           0
urxvt.fadeColor:        black
urxvt.shading:          100
urxvt.inheritPixmap:    true
urxvt.pointerColor:     black
urxvt.pointerColor2:    white

To get it transparent etc.

Then I adjusted my ~/.config/openbox/rc.xml to get rid of window decorations etc.
I added this in the <applications> section:

> <application name="urxvt">
    <decor>no</decor>
    <shade>no</shade>
  </application>

This works, only** it still leaves me with a black line/border around my terminal windows**. (As you can see in de screenshot below). :(

So, can anyone suggest a method to get rid of this annoying border? I presume it has to be done in either the .rc.xml file, or the .Xdefaults file, but I can't think of what I'm missing here.

A big thanks in advance.

Freduardo

---

### Post by freduardo on 2007-04-21
Ok, I think I've sort of figured it out myself by accident (oops).

Its not the rc.xml file, nor is it the .Xdefaults one. Everything I put in there was/is correct.
Only most openbox-themes draw a border around each window. 
So I had to disable that by editing my theme config file.

So I guess this is solved :D

---


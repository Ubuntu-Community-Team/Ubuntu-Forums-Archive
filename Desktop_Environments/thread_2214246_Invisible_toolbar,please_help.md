---
title: "Invisible toolbar,please help"
date: 2014-03-31
forum: Desktop Environments
---

### Post by viktor5 on 2014-03-31
I have Lubuntu 13.10

I left the kids with the pc a few hours and they managed to create a new second toolbar on the top,
Instead of just remove it I had the wonderful idea of setting the width from 100 to 0,
so now I can't maximize the windows! :-(

How can I remove this ghost toolbar?

Thanks for your help

---

### Post by ajgreeny on 2014-03-31
You will find the configs for your panel(s) in **/home/<user>/.config/lxpanel/Lubuntu/panels/** so look at the files in there and you will be able to figure out which panel is which from the content.

In my OS of Lubuntu 14.04 in virtualbox where I have two panels, one at the top, one on left, the files show:-
```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
    [COLOR=#ff0000]edge=left[/COLOR] (or [COLOR=#ff0000]edge=top[/COLOR])
    allign=center
    margin=0
etc, etc.
```
so delete the file for the top panel and it should be gone.

---

### Post by viktor5 on 2014-03-31
Thanks for your help,
I can't see the top toolbar that I want to remove,
what should I remove here?

Global {
    edge=bottom
    allign=left
    margin=0
    widthtype=percent
    width=100
    height=24
    transparent=0
    tintcolor=#000000
    alpha=0
    autohide=1
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=1
    fontsize=10
    fontcolor=#000000
    usefontsize=0
    background=1
    backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
    iconsize=24
    loglevel=2
}

---

### Post by ajgreeny on 2014-03-31
How many files do you have in that **.config/lxpanel/Lubuntu/panels** folder?  There should be two if you have two panels, one for the bottom and another for the top, but you have only the bottom pnel file, so I am wondering if the top panel has already been removed but the margin has been set in the openbox configuration.

Have a look there and see if the top margin has been reserved so that it is never covered by a window.

---

### Post by viktor5 on 2014-04-02
:guitar: Lol,I did not get it the first time that it was another file named top...I was looking in the panel file,
I'm really a newbie on ubuntu...,
once I eliminated the top file and reeboted it is all perfect!

Thanks for your help;)

---


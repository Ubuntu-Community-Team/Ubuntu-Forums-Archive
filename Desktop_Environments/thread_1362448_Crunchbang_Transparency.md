---
title: "Crunchbang Transparency"
date: 2009-12-23
forum: Desktop Environments
---

### Post by WorldTripping on 2009-12-23
OK so not sure if this is the right place for this, so please move if necessary.

I want to know how to permanently enable compisiting transparency for an application launched in #!

Explicitly, when I launch a terminal I want the transparency set to 30%.

Is this easily achievable ?

Cheers,

WorldTripping.

---

### Post by pasti on 2009-12-23
well in ubuntu I do this:-

start the terminal > edit > profile preferences then click the background tab, at the bottom of the window there's a slider, slide it left or right to get the transparency you want.

I don't use # so start here:-

[http://crunchbanglinux.org/wiki/theming](http://crunchbanglinux.org/wiki/theming)

---

### Post by AllRadioisDead on 2009-12-23
Look in your openbox startup file, it should be in there.
You will need to uncomment a line.

---

### Post by WorldTripping on 2009-12-23
> **ihermit said:**
> Look in your openbox startup file, it should be in there.
You will need to uncomment a line.

You mean this line right ?

```

# Enable Eyecandy - off by default
# see "/usr/bin/crunchbang/xcompmgr-crunchbang" for more info
xcompmgr-crunchbang --startstop &

```

That turns on the compositing by default so that you don't have to 'Enable' it before using.

However it does not remember the state that you put a particular application window in.

e.g. I can set the transparency of a terminal to 30% but as soon as the terminal is closed that setting is forgotten.

Any ideas ?

WorldTripping

---

### Post by WorldTripping on 2009-12-23
> **pasti said:**
> 
well in ubuntu I do this:-

start the terminal > edit > profile preferences then click the background tab, at the bottom of the window there's a slider, slide it left or right to get the transparency you want.


Thanks for the reply but the terminal in crunchbang works slightly differently to the Ubuntu one (no menus).

WorldTripping.

---

### Post by koleoptero on 2009-12-23
I don't think xcompmgr can do per application settings. If the terminal application you use won't do transparency by itself then you can install any other that does, like gnome-terminal.

---

### Post by gutterslob on 2009-12-23
Okay.... if you just want terminal transparency, all you need to do is edit your Terminator config (it should be in your #! prefs menu under  Terminator Config", I think)

Just uncomment the lines that refer to transparency (you'll know it when you see it)

If you want transparency via xcompmgr at startup, it might be a little tricky.... there's basically a few ways to achieve that.

Simplest solution in to download the xcompmgr-dana package from the repos (makes sure you turn off your current xcompmgr before you do this, as it removes xcompmgr before installing xcompmgr-dana.

You then edit your startup script and add something like this (or try it out with Alt+F2 first)
xcompmgr -CcfF -I20 -O10 -D1 -t-5 -l-5 -r4.2 -o.82 -m.70
*play with the -o and the -m values for opacity and menu transparency, but please be advised that setting transparency here will affect all windows, not just the terminal (I don't use this method, btw.. so I can't be 100% sure)

The better way, is to edit your ' /usr/bin/crunchbang/xcompmgr-crunchbang ' and set transparency within there, but I'm not sure if you want to use this method.

Note: I suggest you enable transparency via terminator (the first part of this post) if you just want transparent/translucent terminals.

Hope this helps.

---

### Post by WorldTripping on 2009-12-23
> **gutterslob said:**
> Okay.... if you just want terminal transparency, all you need to do is edit your Terminator config (it should be in your #! prefs menu under  Terminator Config", I think)

Just uncomment the lines that refer to transparency (you'll know it when you see it)

Hope this helps.


** facepalm **

How stupid do I feel right now ?? :oops:

Why on earth did I not look in the terminator config ??

```

# Uncomment below to enable transparency
# --------------------------------------
background_type=transparent
enable_real_transparency=true
background_darkness=0.8

```

That is exactly what I was looking for as I only want the terminal transparent for when I am reading a document and typing.

Thanks. =D>

WorldTripping.

---

### Post by bapoumba on 2009-12-24
Moved to Desktop Effects.

---


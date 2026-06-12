---
title: "How I managed to mostly fix Compiz."
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by atomicthumbs on 2007-10-02
OK, here were my problems:

1. No window decorations in KDE.
2. Large windows totally black.
3. compiz-config-settings-manager wouldn't start.

I've fixed 2/3 of these. 

How to fix 1 and 2 in one swoop:

instead of using ```
compiz --replace
``` to start compiz, use this:

KDE:
```
compiz --sm-disable --replace decoration wobbly fade minimize cube move place resize rotate scale switcher water zoom kde-window-decorator
```

GNOME:
```
compiz --sm-disable --replace decoration wobbly fade minimize cube move place resize rotate scale switcher water zoom gnome-window-decorator
```

I'm not sure why this works, but it does. :)

Perhaps this should be stickied, as it seems to solve a problem that tons of users have been having.

Now, I need help. I can't get ccsm to start! Here's the error in the console:

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

It acts like it's opening, and a window opens and disappears immediately. This is very annoying, as I can't change any of compiz's settings without it! And fusion-icon doesn't work either.

---

### Post by vikrant82 on 2007-10-02
I was facing same issue after gutsy upgrade.

As far as I remember somehow compiz-gnome had a dependecy libwnck which could not be installed from repos. So I installed it offline.

Moreover I thought it turned out to be previous compiz "junk" scattered. I dont exactly remember, but i cleaned up every damn compiz word and then installed using amaranth repositories.

deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
Note that you might have to disable your Gutsy Universe repos for time being. 

Afterwards, I let it upgrade with gutsy repos and now it works like charm.

Hope it helps.

---

### Post by atomicthumbs on 2007-10-02
I'm using Feisty with the Amaranth repos already. :P

---

### Post by ProfKaramba on 2007-10-02
I'm using Gutsy with a X1400 and have no borders or effects either.
When I execute that comand it gives me some errors but I star seeing the effects of beryl... (but no window borders yet)

How can I solve this?
thanks

---

### Post by atomicthumbs on 2007-10-02
> **ProfKaramba said:**
> I'm using Gutsy with a X1400 and have no borders or effects either.
When I execute that comand it gives me some errors but I star seeing the effects of beryl... (but no window borders yet)

How can I solve this?
thanks
Okay. I don't know what the GNOME window decorator is called, but replace "kde-window-decorator" with the name of the GNOME one.

pb[EDITp/b[: Method figured out and added to the top post.

---

### Post by ProfKaramba on 2007-10-02
thanks
but still gives me this error:
/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/compiz/default-cubecap.png


and there are no window borders :\
I'm just a noob :x

---

### Post by atomicthumbs on 2007-10-02
hmm, I don't know. Maybe try "gtk-window-decorator" instead.

Or, if you have Emerald, just type "emerald --replace" seperatly. It doesn't work for me, but it might work for you. 

```
sudo apt-get install emerald
```

---

### Post by ProfKaramba on 2007-10-02
with emerald and gtk-window-decorator some kind of borders appeared but still no buttons and I can't drag the windows...

This is a really weird problem :X

---


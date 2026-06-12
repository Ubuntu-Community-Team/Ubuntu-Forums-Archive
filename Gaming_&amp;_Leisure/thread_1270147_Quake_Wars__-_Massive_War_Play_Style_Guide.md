---
title: "Quake Wars  - Massive War Play Style Guide"
date: 2009-09-19
forum: Gaming &amp; Leisure
---

### Post by Perfect Storm on 2009-09-19
**[SIZE="5"]Quake Wars - Massive War Play Style Guide[/SIZE]**

[COLOR="Red"][I]This guide will show how to set up a massive bot war in Quake Wars. The default maximum level of bots is 15 (+1 player = 16). The guide is geared towards Single Player style.

So you are looking for a massive war in Quake Wars, this is the guide.[/I][/COLOR]


1. Enable Quake War Console
2. Enable key Console 
3. Quake Wars - Massive War Launcher
4. Setting up the bots



---------------------------------------------------------------------------

**[SIZE="4"]1. Enable Quake War Console[/SIZE]**

The Quake Wars Console should be enabled by default. But you might want to check it in case it is not.

```
nano ~/.etqwcl/base/etqwconfig.cfg
``` 

Go to line 90
The line should look like this if it´s enabled;
**seta com_allowConsole 1**

Save: [ctrl]+[o]
Exit: [ctrl]+[x]



---------------------------------------------------------------------------

**[SIZE="4"]2. Enable key Console [/SIZE]**

The default key to enable the Console is: [ctrk]+[alt]+[~]
**If your Quake Wars Console works, please jump to part 4**

This is more of a non-english keyboard problem that the Console key is not recognized. But also a good way to change the default Console key.

First you need to decide which key should enable the Console, then;

```
xew
```

Press the key you want Console key to be;
Mine is;
```
KeyRelease event, serial 34, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 10930928, (-410,216), root:(814,240),
    state 0x0, **keycode 51 (keysym 0xa7, section)**, same_screen YES,
    XLookupString gives 2 bytes: (c2 a7) "§"
    XFilterEvent returns: False

```

The bold marked text is the info I need for the next step.


```
nano ~/.etqwcl/QW-MassiveWar.sh
```

add;

```
#!/bin/sh
OLD_CONSOLE_KEYMAP=`xmodmap -pke|grep "**51**"|cut -d "=" -f 2`
xmodmap -e "**keycode 51** = quoteleft asciitilde"
sh /usr/local/games/etqw/etqw-rthread $@
xmodmap -e "**keycode 51** = ${OLD_CONSOLE_KEYMAP}" 
```


The bold text is info I used from the **xew**.

Save: [ctrl]+[o]
Exit: [ctrl]+[x]

```
chmod +x ~/.etqwcl/QW-MassiveWar.sh
```



---------------------------------------------------------------------------

**[SIZE="4"]3. Quake Wars - Massive War Launcher[/SIZE]**

```
alacarte
```

Go to the Game section in Alacarte and push the New Item button. Fill in;

```
**Name:** Quake Wars - Massive War
**Command:** sh -c "cd ~/.etqwcl && ./QW-MassiveWar.sh" 
**Comment:** Quake Wars - Massive War allows you to have as many bots as you like.

**Icon:** /usr/local/games/etqw/etqw_icon.png
```

Done.



---------------------------------------------------------------------------

**[SIZE="4"]4. Setting up the bots[/SIZE]**

In the warmup phase of Quake Wars press the Console key.

This example sets up 31 bots + 1 player;

```
si_maxplayers "32" 
bot_minclients "-1"
```

Now you are ready to give bots to either the stroggs and to GDF.

To give the strogg side an extra bot;
```
admin addbot strogg
```

And for the GDF;
```
admin addbot gdf
```

When you have maxed out the bots. You´re ready for some heavy battles ^_^


Enjoy

Regards
A.I. Dude

---

### Post by Perfect Storm on 2009-11-09
Have now been tested on 9.10

---

### Post by Perfect Storm on 2010-06-17
Tested on Ubuntu 10.04

---

### Post by Perfect Storm on 2010-10-29
Tested on Ubuntu 10.10

---

### Post by Technophobia on 2010-10-30
Are the bots good? Or is it just target practice?

---

### Post by Perfect Storm on 2010-10-30
Set them all to "Expert" both in handling missions and aiming/actions and you'll real busy to keep yourself alive.

The bots are great in QW.

---


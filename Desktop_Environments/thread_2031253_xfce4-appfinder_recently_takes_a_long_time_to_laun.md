---
title: "xfce4-appfinder recently takes a long time to launch"
date: 2012-07-21
forum: Desktop Environments
---

### Post by MrPopinjay on 2012-07-21
xubuntu 12.04 with xfce 4.10

Installed xubuntu a week or two ago and I have been particularly enjoying xfce4-appfinder. I hit the hotkey and it pops up instantly, or rather it did. Today it's been very sluggish, taking up to 5 seconds to appear after I hit the hotkey.

It works fine once it has launched, it just takes a long time to get there. I don't believe anything has changed regarding my system and my processor isn't under any stress, etc. I have turned off my computer several times throughout the day but the problem persists.

Could anyone identify my problem and help me fix it? Or should I give up and try an alternative like synapse or something?

Thanks,
Louis

---

### Post by black veils on 2012-07-21
i cant help with your underlying issue, but maybe you could try Synapse instead ?  have a look, it is a very useful app. it adjusts to your usage. you cant search the settings manager app through it though, the menu file for the settings manager needs to be tweaked, that is all.

---

### Post by MrPopinjay on 2012-07-21
I'm starting to think that it may be getting progressively slower as my computer is left on. It seemed snappy when I used it to launch my browser an hour ago yet now it seems slower, though no where near as bad as it was earlier in the day. Nothing else is taking a long time to launch.

I used to use synapse and I'm considering going back to it. Is it still being developed? I heard it was dead.

edit: Literally the minute I posted this it started taking several seconds to launch. I have absolutely no idea what has changed. I haven't even used any programs other than my browser in that time...

editedit: I get this error message when I launch it from the terminal. When it does launch but takes ages, that is.

(xfce4-appfinder:4167): xfce4-appfinder-CRITICAL **: Failed to open window: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by tmartiro on 2012-11-07
hi,

try to use xfce4-appfinder without becoming D-BUS service

 **xfce4-appfinder -c --disable-server**

it worked for me.

---

### Post by LewisTM on 2012-11-07
> **tmartiro said:**
> hi,

try to use xfce4-appfinder without becoming D-BUS service

 **xfce4-appfinder -c --disable-server**

it worked for me.
Thank you tmartiro for the tip. I have been experiencing the same weird delay.

The Xfce keyboard shortcuts settings map Alt-F2 to [FONT="Courier New"]xfrun4[/FONT] which is a symlink for xfce4-appfinder. That's the right place to append [FONT="Courier New"]-c --disable-server[/FONT].

I prefer Synapse most of the time except if I want to run a complicated command (you can't edit the command line in Synapse) or if I want to browse categories. I have heard rumors that it is dead :confused: But looking at their [launchpad]("https://launchpad.net/synapse-project") page, it says it is still under active development with future versions planned. No new version since March though, maybe development has simply slowed?

Cheers!

---

### Post by Dafydd on 2013-01-08
> **tmartiro said:**
> hi,

try to use xfce4-appfinder without becoming D-BUS service

 **xfce4-appfinder -c --disable-server**

it worked for me.

Thanks for that. This got rid of the delay. Now appfinder is very snappy. Cheers.

Dafydd

---

### Post by Buntu Bunny on 2013-01-08
I've been having the same problem. Mr. Popinjay, thanks for asking about it! I use appfinder a lot. However, this is what I get 

```
~$ xfce4-appfinder -c --disable-server
xfce4-appfinder: Unknown option -c.
```

---

### Post by Buntu Bunny on 2013-01-08
> **Buntu Bunny said:**
> I've been having the same problem. Mr. Popinjay, thanks for asking about it! I use appfinder a lot. However, this is what I get 

```
~$ xfce4-appfinder -c --disable-server
xfce4-appfinder: Unknown option -c.
```

Irregardless, appfinder is popping up faster than before. Go figure.

---


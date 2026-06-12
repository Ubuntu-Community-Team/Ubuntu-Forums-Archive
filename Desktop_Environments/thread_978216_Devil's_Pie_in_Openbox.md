---
title: "Devil's Pie in Openbox"
date: 2008-11-10
forum: Desktop Environments
---

### Post by Mitch72 on 2008-11-10
Apologies if this is the wrong place top post this, I ran a search and couldn't find anything...

Has anyone been successfull in getting devil's pie to work with openbox? When I run it in metacity it works fine, but in openbox (running in GNOME, not on it's own), i get several of the following messages:

```
(devilspie:8146): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE
```

Anyone able to replicate this? Help would be appreciated :p

---

### Post by modmadmike on 2009-06-12
> **Mitch72 said:**
> Apologies if this is the wrong place top post this, I ran a search and couldn't find anything...

Has anyone been successfull in getting devil's pie to work with openbox? When I run it in metacity it works fine, but in openbox (running in GNOME, not on it's own), i get several of the following messages:

```
(devilspie:8146): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE
```

Anyone able to replicate this? Help would be appreciated :p

Like this ```
(gnome-panel:20061): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE
```
Try launching almost any application in the terminal in openbox and chances are you will get this error constantly lol

---

### Post by Locutus_of_Borg on 2009-06-12
is there something devilspie does that you cannot do in rc.xml?

there is a huge amount of window manager tweaks you can insert into the rc.xml file, see if you can accomplish what you are trying to do there rather than use devilspie

---


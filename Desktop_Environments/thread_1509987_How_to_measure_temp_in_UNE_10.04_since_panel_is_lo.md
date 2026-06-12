---
title: "How to measure temp in UNE 10.04 since panel is locked"
date: 2010-06-14
forum: Desktop Environments
---

### Post by narnie on 2010-06-14
Does anyone have any good ideas for a GUI program that monitors temp for CPU and hard drive?

I'd prefer one that is like a system monitor that can show trends on a graph (like CPU usage, etc).

It is irritating that you can't even add a silly app to the panel because UNE is locked (ERR, Ubuntu, what were you thinking??? Give US the choice!!!  Rant over)

So far, I have just written a quick script after installing lm-sensors and hddtemp and run the necessary setup routines that will show me, but I would like some of the history data.

```
#! /bin/bash
#

zenity --info --title "Temp INFO" --text "`sensors`"
```

Cheerio,
Narnie

---

### Post by nilarimogard on 2010-06-15
How about [unlocking the gnome panel in UNE]("http://www.webupd8.org/2010/05/how-to-add-remove-applets-from-gnome.html")?

---

### Post by narnie on 2010-06-15
> **nilarimogard said:**
> How about [unlocking the gnome panel in UNE]("http://www.webupd8.org/2010/05/how-to-add-remove-applets-from-gnome.html")?

I don't want to "mess up" my Gnome setting as at times I like to use a regular Gnome desktop.

I did a lot of hacking and got some things changed on UNE.

I should have mentioned unlocking UNE (it really isn't unlocking, it is just stealing the UNE desktop config) isn't a solution for me.

Thanks for the suggestion, tho.

:)

Narnie

---


---
title: "Hibernates whenever unplugged"
date: 2011-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wilbefast on 2011-01-09
I've got this weird problem: my computer, if unplugged when not fully charged, tells me that it has only 1 minute of battery left and promptly hibernates. Even if it's charged up to 90%.
If, however, the battery IS fully charged, I can unplug it and use the machine for a good hour and a half. My Windows partition doesn't seem to have this problem: my guess is Ubuntu jumps the gun when it should be waiting a moment for things to stabilise a little (at which point it would realise that it has an hour, not a minute).

Is there anything I can do to fix this? It's very bad for my blood pressure.

Cheers,

William

Vostro 1510
Ubuntu 10.02 64 bit

---

### Post by fjgaude on 2011-01-09
I'm not sure if this is a bug or not but this usually fixes the problem: in Configuration Manager click down to apps, then to gnome-power-manager. There, click general and uncheck use_time_for_policy.

See if this works.

---

### Post by Wilbefast on 2011-01-12
Thanks for the reply, I'll give it a try as soon as I get home :D

Edit: it works - fantastic!

Since it took me ages to find the code, here's the command you need to run to get into the configuration editor
[gconf-editor]("http://live.gnome.org/GnomePowerManager/FAQ")

---

### Post by olihall on 2012-01-12
Looking to solve this exact problem.  Trouble is there's no "General" tab under gnome-power-management.  Using version 11.10 so not sure whether this has been removed in the newer versions.  Getting rather irritating now and doesn't seem to be any other fix for this.

---

### Post by Wilbefast on 2012-01-12
> **fjgaude said:**
> click down to apps, then to gnome-power-manager.  There, click general and uncheck use_time_for_policy.
The part fjgaude left out is that the menu he's using is:
> **Wilbefast said:**
> [gconf-editor]("http://live.gnome.org/GnomePowerManager/FAQ")

---

### Post by olihall on 2012-01-22
Here's what I did:

-Opened Terminal
-Typed gconf-editor
-clicked down to gnome-power-manager

No 'General' option there.  the only menu items available are: 
=acitons
=backlight
=buttons
=disks

I guess there's no fix for this right now for this so I'll just have to be carefull not to unplug while attached to power.

---

### Post by Wilbefast on 2012-01-22
> **olihall said:**
> No 'General' option there.  the only menu items available are: 
=acitons
=backlight
=buttons
=disks
That's odd. I have the [following]("http://imagebin.org/index.php?mode=image&id=194867"):
-(all those mentioned)
-general
-lock
-notify
-statistics
-thresholds
-timeout
-ui

---


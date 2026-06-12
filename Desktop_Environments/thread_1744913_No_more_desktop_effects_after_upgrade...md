---
title: "No more desktop effects after upgrade.."
date: 2011-04-30
forum: Desktop Environments
---

### Post by RobotGymnast on 2011-04-30
I upgraded to Ubuntu 11.04, and now I no longer have wobbly windows, or any of my other custom effects, like animations. How can I get these set back up?

---

### Post by Copper Bezel on 2011-04-30
I'm assuming you're using the Classic desktop?

If so, run [font="Courier New"]compiz --replace[/font].

If this works, I *think* you need to run [font="Courier New"]gconf-editor[/font] and navigate to desktop -> gnome -> session -> required_components and change the field [font="Courier New"]windowmanager[/font] from [font="Courier New"]metacity[/font] to [font="Courier New"]gnome-wm[/font]. This will allow Gnome to launch with Compiz as the window manager, providing your desktop effects.

Since the Classic desktop is also the fallback for video cards that can't run Compiz, 11.04 forces it to start with Metacity instead. Previously, the key in gconf was set to gnome-wm, which uses your default window manager as set in Appearance Preferences (by activating desktop effects.)

I *think*.

Try it with [font="Courier New"]compiz --replace[/font] first, though. It's also possible that a regression has made your video card no longer support Compiz.

---

### Post by manzdagratiano on 2011-04-30
These settings may also have been disabled. To re-enable them, install Compiz Config Settings Manager:

sudo apt-get install ccsm

and then re-enable them in ccsm.

---

### Post by Copper Bezel on 2011-04-30
The package name is actually [font="Courier New"]compizconfig-settings-manager[/font] . The *command* is [font="Courier New"]ccsm[/font] . I make that mistake frequently enough, myself.  = )

---

### Post by filster on 2011-04-30
Also check if your graphic driver is working properly (eg. do you have any other problems, like Unity not working or other stuff like docks (that need 3D support) not working etc. ?).

---

### Post by RobotGymnast on 2011-04-30
> **Copper Bezel said:**
> I'm assuming you're using the Classic desktop?

If so, run [FONT=Courier New]compiz --replace[/FONT].

If this works, I *think* you need to run [FONT=Courier New]gconf-editor[/FONT] and navigate to desktop -> gnome -> session -> required_components and change the field [FONT=Courier New]windowmanager[/FONT] from [FONT=Courier New]metacity[/FONT] to [FONT=Courier New]gnome-wm[/FONT]. This will allow Gnome to launch with Compiz as the window manager, providing your desktop effects.

Since the Classic desktop is also the fallback for video cards that can't run Compiz, 11.04 forces it to start with Metacity instead. Previously, the key in gconf was set to gnome-wm, which uses your default window manager as set in Appearance Preferences (by activating desktop effects.)

I *think*.

Try it with [FONT=Courier New]compiz --replace[/FONT] first, though. It's also possible that a regression has made your video card no longer support Compiz.

The first time I booted, it said something about my hardware not supporting Unity, and booting into classic.

compiz --replace makes it work, but much more slowly than it used to! Also, my windowmanager is set to compiz, not metacity nor gnome-wm. Setting it to gnome-wm and rebooting makes no difference; still no effects.

---

### Post by Copper Bezel on 2011-04-30
Yeah, this is definitely starting to sound like a video card driver regression issue. What's your card?

---

### Post by RobotGymnast on 2011-04-30
> **Copper Bezel said:**
> Yeah, this is definitely starting to sound like a video card driver regression issue. What's your card?

Some crappy integrated Intel laptop card. Looks like Intel GM965.

---


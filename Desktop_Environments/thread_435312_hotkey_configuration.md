---
title: "hotkey configuration"
date: 2007-05-06
forum: Desktop Environments
---

### Post by christian_johansson on 2007-05-06
I use Ubuntu Feisty, everything upgraded to the latest versions available in the repos.

My logitech keyboard has a volume knob on it. Everything worked out of the box including next and prev buttons, but the volume knob and the mute buttons affect the surround sound volume control, not the master control like it should.

So when I try to decrease the volume, only the surround-speakers volume goes down. And mute only mutes the surround speakers.

I know for sure its the surround speakers, because I can see the surround gauge move when I use these hotkeys.

This appears to be a bug to me, and I will submit it too. But does anyone know how to change the gagues the hotkeys work on for a quick fix?

---

### Post by TheOtherShoe on 2007-05-07
Here is something you might try: right click on the volume control applet in the panel and open its preferences. There you can select which device the applet should control. I'm guessing that Gnome is set up so that the keyboard control affects the same device that the applet does; so selecting a different device for you applet to control might fix your problem.

EDIT: If the above doesn't work, then try selecting the device you want to control in Preferences > Sound.

---

### Post by Purple Grant on 2007-05-08
> **TheOtherShoe said:**
> If the above doesn't work, then try selecting the device you want to control in Preferences > Sound.

That's the way to do it.
My keyboard was adjusting my mic volume.

Select "master" in the "Default Mixer Tracks" bit and bob's yer auntie

---


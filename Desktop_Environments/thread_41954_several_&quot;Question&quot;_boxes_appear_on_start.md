---
title: "several &quot;Question&quot; boxes appear on startup"
date: 2005-06-15
forum: Desktop Environments
---

### Post by holr on 2005-06-15
Hello,
   A new user to linux, ended up choosing ubuntu because it seems to do everything i need to so far!

   I am using an ibm t41p laptop (with a pentium-m / centrino cpu) and tried to install some speedstep style programs (like the speedswitch xp program you can get for windows) so that i can manually change my cpu speed.

   Anyway, recently afterwards, I have run into problems, im getting several "Question" boxes appear when I get into ubuntu gnome.

They all say "The panel encountered a problem while loading OAFIID:GNOME_......
then one of
..._EmiFreqApplet , ..._Panel_WirelessApplet , ..._BattstatApplet , ..._MixerApplet , ..._TrashApplet

I have no idea what I have done wrong! But my trash can icon in the bottom right has disappeared along with other icons relating to these errors.

Any ideas what I can do to sort it out? Thanks! I have attached a screenshot of whats being said.

---

### Post by Knome_fan on 2005-06-15
Hm, obviously some gnome applets don't load, that's why you get the messages.

The first thing you should make sure is, that the applets you are trying to load are indeed installed. Maybe you accidentely deleted something while playing around. The easist way would probably to make sure that ubuntu-desktop is installed.

If that doesn't help, you could try to delete the offending applets and later add them again and see if it works than.

Other than that, something I always found useful was to choose xterm as a session from gdm and then start gnome-session from this xterm. That way you might be able to see where gnome has problems while it's loading.

Good luck!

---

### Post by holr on 2005-06-15
[QUOTE=Knome_fan]Hm, obviously some gnome applets don't load, that's why you get the messages.

The first thing you should make sure is, that the applets you are trying to load are indeed installed. Maybe you accidentely deleted something while playing around. The easist way would probably to make sure that ubuntu-desktop is installed.
Good luck![/QUOTE]

Wow, thank you very much!!! Using your suggestion, I merely did a " sudo apt-get install ubuntu-desktop " followed by a "killall gnome-panel" and that fixed it! thanks!! Saved a reinstall of ubuntu ;-)

---


---
title: "Keyboard Shortcuts don't work globally"
date: 2009-11-12
forum: Desktop Environments
---

### Post by Gilthans on 2009-11-12
Hey,
I'm transitioning into Ubuntu. So far its been pretty smooth, but one issue has been bugging me:
Whenever I'm in fullscreen mode for some program, I can't use any keyboard shortcuts. So if I'm playing a game, and suddenly my phone rings, I have to minimize or exit the game so I can use the mute button.

I think this is related as well, but if I load up my laptop during class, and I get the login screen, I want to make sure that the loadup-sound doesn't play, and try to use the mute button, but it doesn't work until after gnome has loaded (and played the sound). Currently I have disabled startup sound but this is not what I want.

Any solutions to this issue?


Thanks,
Daniel

---

### Post by Giblet5 on 2009-11-12
Most games will grab ALL keyboard input (aggressively) and prevent other programs from seeing the keypress/keyrelease events.

Shortcuts won't work inside many games under linux, just as they won't work under Windows, MacOS, Solaris, HPUX......

This is an issue better discussed with the game vendors because they probably don't realize their products do that.

---

### Post by Gilthans on 2009-11-13
This is true sometimes, however under windows, the mute and volume buttons worked even under games, and they couldn't have been grabbed at all. Like some other OS special buttons which can't be controlled by programs (such as ctrl+alt+delete).

Isn't there a way to make those button or that combination un-interruptable? OS sensitive buttons and such? In Ubuntu, I'm pretty sure that ctrl+alt+F1..8 are OS specific and can't be grabbed. Can't I do something similar with the volume buttons?

---

### Post by Gilthans on 2009-11-13
I'd like to add to that another example: even alt+tab (which I'd naturally use to minimize a full screen window) doesn't work under the said full-screen program (Frets on Fire, by the way). Contrary what I thought before, not even ctrl+alt+shift+F1 works, so basically if the game freezes - I have to reboot!
Result: I have no way of minimizing the screen, and to do anything at all, such as muting or volume decrease, I need to exit the game completely; and if the game ever freezes, I can do nothing but hard reboot.

I know you might say this is the developers fault for making the game grab all those key events, but Ubuntu shouldn't let it be doing it in the first place. The OS' stability and usability shouldn't be damaged by a program run on top of it, if not from a usability standpoint, at least from a security standpoint!

So is there a solution here? This seems like a pretty big issue in my books, but I couldn't find anyone with the same problem.

---

### Post by Gilthans on 2009-11-17
Does anybody have a solution for this? This seems like an issue to me.
For now I've disabled full screen mode on the game, but I still can't control volume from the gnome login screen.

---

### Post by harbimilan on 2011-03-11
Hey, I've got the exact same problem.

I can't increase or decrease (or mute) volume while playing full-screen games. How can we fix it? 

Somebody help please..

---


---
title: "Yellowish Unity Launcher"
date: 2012-04-05
forum: Desktop Environments
---

### Post by monk0nuggets on 2012-04-05
Since a recent update, my desktop settings went back to default for some reason, but after readjusting them to how I had them the launcher bar opacity doesn't seem to be changing and it has a strangely yellowish hue to it which I'm not sure how to adjust. I'd like to make it clear(ish) like it was before, and like my task bar is.  Any ideas?  Here's a screen cap:

---

### Post by Lemuriano on 2012-04-05
Did you try myunity?

---

### Post by White-Energy on 2012-04-05
I have the same issue.. i think ubuntu-tweak has caused it..
Nothing seems to fix it =/

EDIT: I've logged into a guest session and the issue isnt there..
I've tried these commands to reset compiz/unity


> **DO NOT TRY THESE COMMANDS!!**
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
unity --reset

But the issue still exists..
Changing the color for the panel made it worse.. i think we should somehow dig into it.
I've also noticed that just after logging in the panel doesnt have this yellowish color, but just when the desktop fully loads the yellow thing appears.. I'll try my best to find a workaround or even a fix, if i do, i'll keep you guys updated. ;)

EDIT2: I might have found the issue.. i'm not very sure because i've got into much trouble with my session while trying many things :( but however.. here's something you can try :)

> rm -r .cache

Logically.. something must have gone wrong while refreshing the settings with unity..
Tell me if it worked :)

---

### Post by grahammechanical on 2012-04-05
What version of Ubuntu are you using? I ask because that effect is standard in 12.04. The launcher panel picks up its colour from the wallpaper background image. Try setting the wallpaper to the slide show and watch how the launcher panel changes is hue. The same happens to the Dash and the shortcuts overlay. That is if you are using 12.04

Regards.

---

### Post by monk0nuggets on 2012-04-05
Tried the latest fix, and no dice.  Still yellow.  But, I tried MyUnity, and it did manage to change it, but it changed it to a solid color rather than clear.  After doing this I went back into CompizEditor and reset the defaults and it fixed the yellow.  But after readjusting the opacity to how I want it, it changes back to yellow.

---

### Post by monk0nuggets on 2012-04-05
I am using 12.04.  That's annoying.  I wonder if there is a way to override it.

---

### Post by White-Energy on 2012-04-06
I think resetting compiz and unity and deleting .cache folder solves it.. as for me.. i've been thru hell to fix it.. i nearly deleted all my session settings.. got them restored now. and the bug disappeared after resetting compiz, unity and deleting cache. try also deleting these files ".ICEauthority" ".Xauthority" if it changes anything for you, if not, move these files/folders ".gconf .config .compiz-1 .gnome2 .gnome2_private .Xauthority .ICEauthority .cache" into a new folder u can call "OLDCONFIG" (u can delete them, backing them up is better) logout and login.. problem solved.
Cya ):P

---

### Post by Frogs Hair on 2012-04-06
grahammechanical is correct and 11.10 also has the Chameleon effect . I have a wallpaper with a similar base color and it affects the launcher the same way , so as much as I like I can't use it in Unity 3D. I don't know if 2D is affected the same way.

---

### Post by White-Energy on 2012-04-06
> **Frogs Hair said:**
> grahammechanical is correct and 11.10 also has the Chameleon effect . I have a wallpaper with a similar base color and it affects the launcher the same way , so as much as I like I can't use it in Unity 3D. I don't know if 2D is affected the same way.

Well i've tried changing the wallpapers before i fixed the issue.. but that did not work ;) it must be somehow something went totally wrong when trying to copy the base color of the wallpaper. unity2d wasn't affected by the issue.

---


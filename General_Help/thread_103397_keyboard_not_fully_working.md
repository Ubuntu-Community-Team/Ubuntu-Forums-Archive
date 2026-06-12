---
title: "keyboard not fully working"
date: 2005-12-14
forum: General Help
---

### Post by djpate on 2005-12-14
hi guys,

i've installed breezy a couple of days ago and fixed most of the issue i had but now i'm stuck with my keyboard.

i have a plain french keyboard nothing fancy, the keyboard is azerty and is working as azerty in ubuntu so far so good but when i hold the shift key to use so function or the alt gr key it doesnt work :( if i do ctl + alt + supr it works so the key are recognized so i dont know what to do.

thanks for any help

---

### Post by aysiu on 2005-12-14
Do you have something like this in your System Settings? Adjusting the keyboard layout may help...

---

### Post by djpate on 2005-12-14
well i have something like that in gnome but its allready set to french and if i try to change something it says 
Erreur lors de l'activation de la configuration XKB.
Cela peut arriver pour plusieurs raisons :
- un bogue dans la biblioth&#232;que libxklavier
- un bogue dans le serveur X (xkbcomp, utilitaires xmodmap)
- serveur X avec une impl&#233;mentation de libxkbfile incompatible

Donn&#233;es de version du serveur X :
The X.Org Foundation
60802000

Si vous rapportez cette situation comme une anomalie, veuillez inclure :
- Le r&#233;sultat de xprop -root | grep XKB
- Le r&#233;sultat de gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

its in french but maybe its a common error

---

### Post by TrinitronX on 2005-12-14
make sure you have the libxklavier and libxkbfile libraries.  An easy way to do this is to open up the 'synaptic package manager' and search for them.
Also, if you just installed breezy, it's probably a good idea to update everything.
In gnome, I think there's a program called 'update manager'.  Just run that and install the updates.

---

### Post by djpate on 2005-12-14
done evrything,
all the package are installed and i did the update but i still have the error and the bad keyboard configuration.
i did an update from hoary to breezy if that could be the problem

---

### Post by frodon on 2005-12-14
[QUOTE=djpate]done evrything,
all the package are installed and i did the update but i still have the error and the bad keyboard configuration.
i did an update from hoary to breezy if that could be the problem[/QUOTE]djpate, you could try to remap the keyboard following this guide : [http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)
I have a french keyboard too and never got any problem, strange

---

### Post by teaker1s on 2005-12-14
[https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/2963)

---

### Post by djpate on 2005-12-14
so there is nothing i can do :confused: 
can i reinstall xorg or something i dont know this is very rustrating i cant work with that...

---

### Post by frodon on 2005-12-14
djpate, here are some threads about the same issue : 
[http://www.ubuntuforums.org/showthread.php?t=75197](http://www.ubuntuforums.org/showthread.php?t=75197)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15372#c35](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372#c35)
[http://www.ubuntuforums.org/showthread.php?t=52410](http://www.ubuntuforums.org/showthread.php?t=52410)

---

### Post by teaker1s on 2005-12-14
you will need to look at the bug link I suppled and edit gnome as it states to gb for great britain /fr for france and the nasty xkb error should disappear

---

### Post by djpate on 2005-12-14
thanks guy but i gave up i installed from 5.10 cd and it worked fine (?!!!@@)
:)  thanks for your help

---


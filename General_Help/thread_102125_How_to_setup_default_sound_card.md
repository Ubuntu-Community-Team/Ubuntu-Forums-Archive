---
title: "How to setup default sound card?"
date: 2005-12-11
forum: General Help
---

### Post by maxx_730 on 2005-12-11
Here's my problem: i have 2 sound cards on my system, and ubuntu, xubuntu and kubuntu installed. One of these sound cards is the better one , the other is one built-in to my motherboard. I'd obviously like to use the better one. On ubuntu it selected that one as default out of the box, but on kubuntu and xubuntu it did not. So, anyone know how to setup the default sound device for ESD or ALSA?

---

### Post by lysis on 2005-12-11
you need to get to System, Preferences, Sound.

Default sound card right there buddy.


oh; i just read using the other desktops . . . i would ask in those forums; you're in the gnome forum, may not get an answer here i dunno.

---

### Post by cutOff on 2005-12-11
Why you don't disable built-in soundcard from the Bios?

---

### Post by lysis on 2005-12-11
cutoff, he may need it.  i am told some applications . . . such as teamspeak and enemy territory . . . will not operate together so you must use two separate cards.

---

### Post by maxx_730 on 2005-12-12
I just looked in the bios, and there's no such option. Also i looked which app did the sound config in gnome, it was gnome-sound-properties, but it doesn't seem to be downloadable in synaptic. I also tried running the ubuntu binary but i didn't get any buttons in the screen, just an empty window. Noone knows what config file to edit?

---

### Post by archer75 on 2005-12-12
[QUOTE=lysis]you need to get to System, Preferences, Sound.

Default sound card right there buddy.


oh; i just read using the other desktops . . . i would ask in those forums; you're in the gnome forum, may not get an answer here i dunno.[/QUOTE]

I have the same problem. Ubuntu has never worked on my soundblaster cards. And it does'nt show up in that menu. 
Though when I installed Cedega it recognized that it was there. It just does'nt work.

---

### Post by maxx_730 on 2005-12-18
Ok i finally fixed it. This is how:
sudo apt-get install gnome-control-center
gnome-sound-properties
Select default sound card
<optional>
sudo apt-get remove gnome-control-center

---


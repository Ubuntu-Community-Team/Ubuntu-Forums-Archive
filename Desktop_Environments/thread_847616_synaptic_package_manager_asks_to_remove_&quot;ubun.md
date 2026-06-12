---
title: "synaptic package manager asks to remove &quot;ubuntu desktop&quot;"
date: 2008-07-02
forum: Desktop Environments
---

### Post by niffcreature on 2008-07-02
so, my computer has a lot of software problems running ubuntu. most of them dont really bother me, like when i decided to install xfce and kde along with gnome, and i ended up ALWAYS getting the kubuntu start up screen, the xubuntu login screen, and then actually logging in with a gnome session, even after i (at least tried) to uninstall them. like i said, that doesnt bother me very much because its mostly aesthetic. 
when i installed 8.04 lts i got a bunch more problems though. i guess i was kind of stupid to install it, since i didnt really know how it was different from 7.10 and all, but i did anyways. since then, audacity has stopped working because it says that theres some problem with the sound output (check project rate etc...). i kind of thought that had to do with ALSA but i tried it with oss output and esd and it doesnt work with those either. the strange thing is that totem movie player (using alsa) still works about half the time, and under multimedia systems selector the test works sometimes as well, and other software using alsa (like dragon player) ALWAYS works. 
along with that, it appears as though JACK audio server is having some problems with the microphone input, and i think its having some other problems as well (audacity doesnt work with it either).
...so as an attempt to fix all of this stuff on my own, i went into the synaptic package manager and attempted to reinstall pretty much all of my multimedia related packages and install anything else that seemed interesting or like it might help. this was going alright (even though i didnt have a very good idea what i was doing and i was pretty doubtful that it was going to do anything), but after marking a fair amount of packages for installation and reinstallation, i marked a package to be installed and a message popped up telling me that if i wanted to install this package, i had to uninstall the package "ubuntu-desktop". what the heck? isnt that like the whole gnome desktop environment and most of my operating system? why would some random piece of software make me want to uninstall my desktop environment? i tried installing some other packages and they all wanted me to do the same thing. it makes absolutely no sense to me. everything works fine on windows so i dont think its a hardware problem. i have no idea why it would be anyways. my computer is an ibm thinkpad t23 with a celeron 1.2ghz. any help would be much appreciated. apologies for the extremely long post.

---

### Post by scragar on 2008-07-02
> 
when i installed 8.04 lts i got a bunch more problems though. i guess i was kind of stupid to install it, since i didnt really know how it was different from 7.10 and all, but i did anyways. since then, audacity has stopped working because it says that theres some problem with the sound output (check project rate etc...). i kind of thought that had to do with ALSA but i tried it with oss output and esd and it doesnt work with those either. the strange thing is that totem movie player (using alsa) still works about half the time, and under multimedia systems selector the test works sometimes as well, and other software using alsa (like dragon player) ALWAYS works.```
killall pulse-audio
```pulse audio has a few problems.



ubuntu-desktop is actualy a metapackage(not a real package, just installs a ton of packages that make up the distro of choice when you install it, same goes for kunutu-desktop etc.), so uninstalling that itself is not a problem, although I cannot be 100% sure that another package may need it at a later date.

---

### Post by niffcreature on 2008-07-02
thanks for that, i will try it. im not sure i was having any problems with pulse audio though. i just discovered that apparently ubuntu-desktop is "broken" so im going to reinstall that and hope it fixes most of my problems.

---

### Post by niffcreature on 2008-07-02
alright. i tried reinstalling ubuntu-desktop and it no longer says its broken or asks me to uninstall it, so i was able to install and reinstall my various sound applications and libraries in an attempt to get my sound working better. it didnt work. im pretty much back where i started.
i tried killing pulseaudio and it said "no process killed". i dont know if that means it wasnt running or if it was running and it didnt stop it. im sure i have it installed.
oh, and another thing. whenever i install, reinstal, or uninstall anything at all, i get a message that says:
E: timidity: subprocess post-installation script returned error exit status 1
E: timidity-interfaces-extra: dependency problems - leaving unconfigured

i have no idea what that means either, especially when it seems to pop up on completely randomly.

---


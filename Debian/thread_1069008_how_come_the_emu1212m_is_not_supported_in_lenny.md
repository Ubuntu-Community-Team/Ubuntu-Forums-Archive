---
title: "how come the emu1212m is not supported in lenny"
date: 2009-02-13
forum: Debian
---

### Post by cmay on 2009-02-13
hi. i have a soundcard for making audio recordings and its a emu1212m card. debian etch finds it and installs the drivers for it so i need only to turn up the volume when i am done installing.

 i would think that it was so with debian lenny. but i tried to install lenny and it did not load any drivers and i cant even find the package with the firmware loaders for the card. why is that? i am using the full dvd image in this case. of both etch and lenny. the etch image is the multi architecture dvd i got from a linux magazine cover and i downloaded the official debian lenny dvd1 image.

 
anyone knows how to get around that issue. (or if i am doing something wrong here)
thanks.

---

### Post by jim_p on 2009-02-14
As I see here in alsa supoorted cards list for creative, emu1212m is supported since 1.0.14

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

Debian lenny has alsa 1.0.17 (etch is on 1.0.13), so it seems weird for it not to be supported by alsa.
What does alsaconf identify as your audio card?

---

### Post by cmay on 2009-02-14
the build in audio card i presume or a unknown device . when i ran alsaconf it could not find any soundcard that it could enable. it listed some choices that was not the emu 1212m but it could not enable sound trough any of them. 

 i have installed open solaris instead on the machine as of right now. i took out the card and put it in another computer and installed 64studio which finds the card and so does etch if i install etch.

 the card is fine and the package that contains the firmware loaders was not in the respotories of etch. which was the official dvd1 image which should be the same as i use for etch except it is not multi arcitecture and both installs the standard debian gnome desktop system. both should automatic install the proper drivers for the card. the etch dvd does and i need to only turn up sound when its installed at first login . 

i had also enabled the multimedia respotories but it was not there. i cant remember the exact name of the package but there is a alsa restrictred firmware loaders that contains modules and drivers for many cards including the emu 1212m. what i do not get is why i could find that package. 

i got video working first and flash playing but no sound and as i was going to start making some music it took to long before i could find a solution so i went back to my 64studio but the whole point of getting it to work with debian lenny is that the upgraded 64studio version is not very satisfying . it is broken in some ways and i wanted to use lenny to build my own audio recording setup just by using the same programs and configure it much the same way as the old 64studio is set up.

---


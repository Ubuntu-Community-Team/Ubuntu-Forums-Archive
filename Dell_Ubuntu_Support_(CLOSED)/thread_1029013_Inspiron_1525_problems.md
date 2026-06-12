---
title: "Inspiron 1525 problems"
date: 2009-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Amerinidiot1231 on 2009-01-02
I have a brand new 1525 Inspiron Notebook and just installed Ubuntu Ibex 8.10.  The system is giving me some issues and questions which I could not find answers to in the forum, which I am trying to get answered here.

1) The touch buttons above my keyboard to raise and drop sound do not appear to control the sound at all.  The blimp appears on the screen for the sound but no matter what I do there is no variation.  The only way I can appear to control sound is by using the icon in the system Notification Area.  

2) The sound is very quiet compared to Vista.  I am nearly afraid to sing while I have music playing in fear I will not be able to hear the artist.  I have everything at full volume and have set everything at full volume using the alsamixer command in terminal(unless I am doing it wrong).

3) There is a ghost in my notebook randomly pushing open the Cd-Rom drive.  Well maybe not a ghost, but the drive randomly opens in linux 2-3 times a day.

4) The battery discharge appears much greater in Ubuntu over Vista. Is there a way to reduce cpu usage in linux as one can in Vista?

Thanks help would be appreciated.

---

### Post by Amerinidiot1231 on 2009-01-03
I have fixed the lack of sound loudness.  Im not sure how but I suspect its from Right clicking my sound menu, selecting volume control, and raising every-things volume.  

I have also fixed the sound shortcuts.

Here are the steps to fix the incorrect keyboard shortcuts for sound.

1) Right Click your sound Icon.  Select preferences.  Take note of the selection that is there (the device thats selected and its selected component).  

2)Select your system menu.  Select preferences.  Select Sound.  

3) In the sound config menu look at the bottom at "Default Mixer Tracks."  Your device and selected component need to be the same as the ones you determined in step one.

Its fixed test out your hot keys!

---

### Post by AmyRose on 2009-01-03
I just bought an Inspiron 1525 as well. I have the same oddities with the CD/DVD drive randomly popping open too. I bought it from Dell's open-source section so I don't have Vista to compare anything though (it came preloaded with Hardy :D )

The random opening of the CD/DVD drive is kinda scary though, especially since I carry this computer around the house (I don't want to break the drive off!)

---

### Post by Amerinidiot1231 on 2009-01-09
I reformatted and reinstalled, as well as updating bios and no more random cd-rom.  :D

---


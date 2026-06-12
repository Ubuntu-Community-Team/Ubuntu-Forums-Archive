---
title: "Two Sound Card and No Sound!"
date: 2006-01-06
forum: Desktop Environments
---

### Post by fine_young_misanthrope on 2006-01-06
Im using a C-Media PCI CMi8738 sound card and my motherboard has a sound card on it (a SiS S17012).  I can get sound in some games such as Doom3 and programs such as xine, but i dont get sound through some games such as the opening of WoW and some programs such as xmms or flash in firefox.  I also don't have much volume control on the sound i do have. In my Sound Preferences, it always shows my SiS S17012 when i check the defalt even after i change it to th PCI card and close the window.  I recently installed linux and am very new, so please walk me through any and all step and help you can provide.

---

### Post by nalmeth on 2006-01-06
I'm sorry, not sure what your prob is.
Are you using Cedega or wine for your games? I suppose you are using native client for doom3, I have never played WoW.

Right Click xmms, find preferences, and make sure output is set to ALSA. 

I am not a buff in this area, but you want alsa basically to run all your sound. Maybe you just don't have ability to play restricted formats? If this is the case, you can easily. Post more info specifically related to each problem.

EDIT: try rythmbox for your music.

---

### Post by fine_young_misanthrope on 2006-01-06
Well i gained one problem and lost another.  Thanks for the tip about xmms. That fixied that problem.  But Im not getting sound for Doom3 any more.  I was using the motherboard's sound card to get sound out of that game.  Any more advice will help.

---

### Post by nalmeth on 2006-01-06
Sorry, I don't know much about Doom3, as I play it on my xbox. I also don't know much about sound in Gnome, even though I have been forcing myself to use it lately! I know in KDE you can go to control center and make sure the audio settings are to your liking. I would assume gnome would have a similar option. Just make sure everywhere you see audio you see ALSA! Maybe you can change the sound settings inside doom3?

Sorry, but thats about all I can recommend, unless you find some new information related to this

good luck

---

### Post by apparition on 2006-01-06
If you haven't already done so, try opening the 'Volume Control Applet' in Gnome (speaker with sound waves by the clock) and go File->Change Device->(choose your PCI card).  System->Preferences->Sound->'Default sound card' should also be the PCI card as you have tried already.  You can then control 'Master' (which didn't do much for me)...if you experience the same issue, then right click on the same Volume Control Applet and choose Preferences.  Make sure the device is your PCI card, then click on the 'PCM' track.  You should be able to control the sound with the slider now.

As for your gaming woes, I can't say I'm a gamer, but I also had problems with onboard sound and PCI sound devices.  The easiest solution may be to just disable the onboard device (assuming you don't use it) through your motherboard BIOS.

I was trying to get my keyboard to control the volume using its volume dial...tried many suggestions on previous threads, but while I could control the volume using the applet slider, my keyboard still controlled my onboard device's PCM volume!  It seems like System->Preferences->Sound->'Default sound card' is not a system wide change (?).  Oh well, that all went away after disabling the onboard sound.

---


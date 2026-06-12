---
title: "Music Player &quot;Could not Open Resource&quot;"
date: 2005-08-14
forum: Desktop Environments
---

### Post by SpiKeRs on 2005-08-14
Hi, I have recently decided to try ubuntu out and have really liked what i have seen so far. I am keen to incorporate it into my daily use more. One of the areas I want to sort out in that regard is with playing various media. 

I have a desktop running WinXp and have setup a network to my laptop. Have shared my music collection on my desktop on my laptop which I have been able to access in ubuntu. The music all plays fine in Totem, however one slight problem is the hidden files windows has (desktop.ini, the album cover jpeg etc) which if I choose to play the entire album in ubuntu, get included in the playlist as well. So I tried Music Player as an alternative because of its library feature. However, it refuses to play the songs, saying it "could not open resource for writing." I dont understand why Music Player should want to write to the song file in the first place. Does anyone have any suggestions?

---

### Post by jasmuz on 2005-08-14
Not a clue but if you like library based players, you could use Muine.

---

### Post by SpiKeRs on 2005-08-15
Thx muine looks quite nice, just a pity it i cant play anything from a shared folder :( Does anyone have any other ideas as to how I can make Music Player play this music. I had a suspicion that its because the music is on a winxp ntfs hd, which ya cant write to if i understood correctly(?) but i really dont know.

---

### Post by Reb on 2005-08-15
You could mount the harddrive writeable, but that's not a great solution. I would try using another media player, maybe beep-media-player, helix player or amaroK.
Just a note: "Music Player"'s official name is Rhythmbox, you might hear it called that.

---

### Post by doclivingston on 2005-08-15
The "Could not open resource for writing" error means that it can't get access to the audio hardware. This can happen if some other application has exclusive access to it, but in that case totem wouldn't work either, which you said it does.

I have no idea why totem would work, but Rhythmbox wouldn't.

---

### Post by SpiKeRs on 2005-08-17
Well i dunno quite what ive done but its playing in rhythmbox now. I tried beep and amarok, they didnt work very well so uninstalled em and then rhythmbox started working...so i dunno. Anyways Ive also found that rhythmbox only works when "enable sound server startup" is clicked in sound preferences. However clicking it stops realplayer and totem from working so, does anyone know how i can get around that one? :D thx

---

### Post by doclivingston on 2005-08-17
Can you go to "Preferences->Multimedia Systems Selector" and see what the default audio sink is? If you want it to work with "enable sound server startup" turned off, this needs to be set to something other than ESD, probably OSS or ALSA.

Totem-gstreamer should behave in the same way as Rhythmbox, but if you've installed totem-xine it may be different.

---

### Post by SpiKeRs on 2005-08-24
Thanks I have it all working now. Sorry if this is drifting off topic slightly but Im wanting to try something other than rhythmbox now, however, its the only player I have found so far that will open locations (so I can use the smb:// address to my shared music folders) and I am wondering if there is anyway around this, or if any of you know alternative players that support that?

---

### Post by doclivingston on 2005-08-24
The smb:// uris are handled by gnome-vfs, which means that you need a music player which uses that. Rhythmbox and Muine are the only two I know of that use gnome-vfs, although there may be others.

Muine is in universe, so you can install it from synaptic, although it requires mono.

---


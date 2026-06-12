---
title: "Mplayer?"
date: 2005-05-21
forum: Desktop Environments
---

### Post by veraction on 2005-05-21
I tried installing it via apt-get, but there are too many errors for me to decipher.

I installed it via source, and it seems to be there, but I have no GUI. Anyone have any ideas on how to get the GUI?

On another newbie note, how would I go about putting something which is installed via source (i.e. Mplayer) onto my gnome Applications Menu?

---

### Post by jasmuz on 2005-05-21
[QUOTE=veraction]I tried installing it via apt-get, but there are too many errors for me to decipher.

I installed it via source, and it seems to be there, but I have no GUI. Anyone have any ideas on how to get the GUI?

On another newbie note, how would I go about putting something which is installed via source (i.e. Mplayer) onto my gnome Applications Menu?[/QUOTE]
 #mplayer -gui [foofilename]

---

### Post by veraction on 2005-05-21
Ah, I see. I guess I compiled without GUI support somehow (thats what message I got in terminal).

Guess I gotta find a different source file to compile rather than the one at MPlayer's site

---

### Post by vaskark on 2005-05-21
[QUOTE=veraction]Ah, I see. I guess I compiled without GUI support somehow (thats what message I got in terminal).

Guess I gotta find a different source file to compile rather than the one at MPlayer's site[/QUOTE]

You don't need another source. Use the source from the MPlayer site and use this when you run configure:
 ```
./configure --enable-gui
``` 
This will create the gmplayer executable.

---

### Post by lorap on 2005-05-22
hi friend!
install this player - VLC, and you'll be out of troubles, trust me.
but before you install it via synaptic you've to add it to the repositories's list.
let's do it right now so after i get home the only thing you'd have to do just install the only package.
first of all open System-->Computer Management-->Synaptic Package Manager.
after you get it open go to the Setting-->Repositories.
once you get the repositories window open press Advanced button and mark all checkboxes possible except "download only upgradable packages" then press Ok.
after what you'll need to wait until the update process completes. the repositories' window'll close at the end of the process so you'll be prompted again the synaptic window.
press the Reload button and wait until the reload process completes.
now you're able to install the VLC player.
press the Search button and write in VLC then press Ok.
once you have the package fount out mark it for install and then press Apply button. wait until install process completes after what close the synaptic.
have a nice day.
pavel

---

### Post by veraction on 2005-05-22
I already have VLC.

The main reason why I was trying to set up MPlayer was because all of my other video players don't work correctly. When watching videos, the audio becomes out of sync by   at least 3/4 of a second for every video file, no matter what format. This happens with all media players I've tried -- Totem, Xine, VLC.

All files work great in Windows Media Player, of course ;\

anyways, I give up on MPlayer. I got it to have a GUI, but no audio.

---


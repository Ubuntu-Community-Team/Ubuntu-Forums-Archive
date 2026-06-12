---
title: "Help with uninstallation of VLC"
date: 2008-12-29
forum: General Help
---

### Post by OinkOink2 on 2008-12-29
Hi,

I've buggered my VLC up since I tried to change it's skin. Please see the screenshot.

Point is, I've tried 'complete removal' in synaptics of VLC and all plugins and attempted to reinstall it. This hasn't worked and I still get the same error.

I noticed that upon re-installing VLC the files are not re-downloaded which makes sense because Synaptics probably has a reference to them in a folder somewhere but because I'm new to Ubuntu I cannot find where those files are?

Maybe if I delete the files on my computer it may get rid of the problem prior to re-installing through Synaptics?

Any ideas?

Anyhow, I also have another problem. It's with the 'Add/Remove...' manager - absolutely no programs show up whatsoever. And the "show" option is set to show installed programs. Whenever I click around I still get the message "**There is no matching application.**"

Again, any ideas on how to rectify that?

Cheers.

---

### Post by wolfen69 on 2008-12-29
after you completely remove something from synaptic, do 
```
sudo apt-get clean
``` and
```
sudo apt-get autoremove
```
this will clean your cache and any unused dependencies, insuring that you download a fresh copy of what you are reinstalling.

---

### Post by cariboo on 2008-12-29
Remove vlc from ~/.config, that should solve you problem. To view hidden files and directories in Nautilus, open Nautilu (Places-->Home Folder) and press Ctrl-h.

Jim

---


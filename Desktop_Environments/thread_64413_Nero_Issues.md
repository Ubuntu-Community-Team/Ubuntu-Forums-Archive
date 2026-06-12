---
title: "Nero Issues"
date: 2005-09-10
forum: Desktop Environments
---

### Post by karuptdata on 2005-09-10
One more question and ill leave you guys alone for the night..I just installed nero and it doesnt recognize my cd burner...does scsi emulation need to be turned on and if so how to activate??


Thanks A Million

---

### Post by manicka on 2005-09-10
Probably not want you want to hear but why use nero anyway. There's enough tools in kde (k3b) and gnome (gnomebaker and nautilus cd burning tools) to do any job equally or better than nero.

---

### Post by karuptdata on 2005-09-10
Really? I never new that i am running gnome where can i find these tools?? Thanks for your input...

---

### Post by manicka on 2005-09-10
[QUOTE=karuptdata]Really? I never new that i am running gnome where can i find these tools?? Thanks for your input...[/QUOTE]
 Gnomebaker  - Applications-->Sound&Video-->Gnomebaker

Most of the nautilus tools are available by right clicking on iso images or on discs themselves.
For instance right clicking on an iso gives the option to burn the image or right clcking on a  disc gives you the option to copy the disc.

Rhythmbox has the ability to create audio cd's from playlists. (I think this feature might only exist in the breezy version of Rhythmbox)

If you don't mind installing some kde libs then you'll find k3b (similar to gnomebaker) a very powerful app that is IMO superior to Nero. Amarok (audio player) integrates nicely with k3b and will also burn playlists to disc.

---

### Post by rafakl on 2005-09-10
to install GnomeBaker do:

sudo apt-get install gnomebaker

Because is not installed by default.

The only problem i see with gnomebaker is that burns very slow.

---

### Post by karuptdata on 2005-09-10
Thanks gentlemen I like gnomebaker i think i can sacrifice a lil time for something that works right away then to fight with software for days on end..LOL ](*,)

Thanks Again

---

### Post by Dolphin on 2005-09-11
Personally, I hated gnomebaker.  I thought it was pretty featureless and it didn't work well for me half the time.

NeroLINUX works great for me.  And while it still lacks all the features of it's windows counterpart, it still has, IMO, more features than gnomebaker.

---

### Post by jeremy on 2005-09-11
nerolinux works, but K3b is soooooo much better,has soooooo many more features, and it is free, in every sense of the word.

---

### Post by jeffreyvergara.NET on 2005-09-17
i have a bad experience with K3b, i wasted so many CD and all of them didnt work. I would like to find a burning tool, like Nero for windows that burn Audio, Data, and VCD/DVD. Im using Gnomebaker, but it dont have VCD/DVD tools

---

### Post by Mr Frosti on 2005-09-22
My experience with NeroLINUX is that DMA has to be enabled for your device to be recognized. To do this, type this in the console:

```
sudo hdparm -d1 /dev/hdc
``` 

"sudo" - This will execute the program with root permissions

"hdparm -d1 /dev/hdc" - This is a utility that can be used to configure DMA modes among other things on devices. This sets DMA to on (1) for your CD ROM drive (/dev/hdc)

Restart Nero after this has been done and see if your device is listed under "Choose recorder". If not, eject any CD's you currently have in the device and restart Nero. 

Still a little rough around the edges...

---


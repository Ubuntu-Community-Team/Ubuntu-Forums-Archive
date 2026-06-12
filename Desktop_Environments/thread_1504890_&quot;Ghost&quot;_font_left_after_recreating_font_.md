---
title: "&quot;Ghost&quot; font left after recreating font cache"
date: 2010-06-08
forum: Desktop Environments
---

### Post by Frogbarf on 2010-06-08
Lengthy history; please be patient!

Last year I installed a number of Georgian fonts in /usr/share/fonts/truetype, all with "BPG" prefixing the names. These were not fully Unicodified but eventually I found BPG Unicode Standard, which is, and installed that in ~.fonts

I decided to delete all the fonts installed earlier, so removed the .ttf files. I then recreated the font cache via sudo fc-cache -f -v

Now, when I go to start Fontforge, I get the following messages:

1, From Fontforge itself, when started via Terminal:

[INDENT][b]Copyright (c) 2000-2007 by George Williams.
 Executable based on sources from 02:03 GMT 10-Nov-2007.
Help! Server claimed font
	-bpg-courier-medium-r-normal--13-0-0-0-p-0-iso10646-1
 existed in the font list, but when I asked for it there was nothing.
 I may crash soon.
Segmentation fault[/b][/INDENT]

2. In kern.log, messages, and syslog:

**Jun  7 21:57:24 glenn kernel: [1141528.391260] fontforge[32285]: segfault at 00000048 eip b70c204f esp bf8a8990 error 4**
I
3. In Xorg.0.log

**FreeType: couldn't open face /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/BPG_Courier.ttf: 1**

BPG Courier is(was) one of the fonts I'd deleted, but evidently somewhere in the system, it's still listed as an available font.

How do I get rid of this "ghost" font? Fontforge invariably crashes, as can be seen from the error messages.

PS #1: I forgot to say: I'm running Hardy (8.04 LTS), Gnome 2.22.3, all updates applied before this mess started (say, a month ago)

PS#2: I went into /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/ and found a number of links to the BPG .ttf files. I've deleted them, but Fontforge still crashes. Where does a line like **-bpg-courier-medium-r-normal--13-0-0-0-p-0-iso10646-1** live? If I know that, I may be able to hand-delete it.

**SOLUTION**: My memory was on the fritz. I hadn't installed these fonts by hand, and they are good Unicode fonts, contrary to what I thought. I'd installed the ***ttf-bpg-georgian*** package with Synaptic. Reinstalling the package over the ruins of the previous installation didn't work, so I uninstalled it (with the "complete uninstall" option), then reinstalled it. Voila! No more ghost font, and now Fontforge starts up just as one would expect.

**MORAL**: Keep track of what font packages you have installed via Synaptic and don't try to uninstall them by hand.

---


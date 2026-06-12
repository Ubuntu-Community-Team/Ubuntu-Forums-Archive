---
title: "[SOLVED] Band In A Box 2007 and Hardy Heron"
date: 2009-01-25
forum: General Help
---

### Post by Noel96 on 2009-01-25
GETTING BIAB WORKING IN UBUNTU 8.10

Success. It's not an ideal solution but it works. I have Ubunutu 8.10 (as mentioned) and I now have BIAB 2007 working in it. What I needed to do was to load a soundfont that contained general midi instruments into ALSA.

How I did that..

I used Synaptic Package Manger to install AWESFX
I copied [b]8MBGMSFX.SF2[/] to my Ubuntu desktop (this file contains the midi sounds for my Audigy soundcards synth)
use ALT+F2 to bring up a run window
In the "Run" command line, I typed "asfx" (no quotes) and then selected "Run with file" and chose the 8MBGMSFX.SF2 file
Started BIAB and it's all working fine


You should be able to fine the .SF2 file on the web if you need it.

You will need to load this soundfond each time you start Ubuntu if you want to run BIAB. It's not that annoying because ALT+F2 will store the command and it's just a matter of selecting it from the drop-down menu. 

For reference, my settings are...

Ubuntu Sound (double click speaker on menu bar)
* set to ALSA 
* SYNTH is enabled and the volume is fully up

BIAB Settings
* Opt >> Midi/Audio driver setup
* Output is set to Wine Midi mapper

Configure Wine settings
* ALSA selected
* everything else unselected.

(P.S. It may be necessary to reboot your computer after this. I have noticed that some WINE settings do not engage until a reboot.)

---


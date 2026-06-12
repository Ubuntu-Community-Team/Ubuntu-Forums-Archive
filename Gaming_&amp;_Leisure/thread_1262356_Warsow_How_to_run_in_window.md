---
title: "Warsow: How to run in window?"
date: 2009-09-09
forum: Gaming &amp; Leisure
---

### Post by The Bright Side on 2009-09-09
Hi!

I was curious about Warsow, so I downloaded it, but when I start it, I get a black screen with an error message from my screen: it cannot display whatever resolution the game starts in. Any idea how I can set the game resolution outside the actual game? Or run it in a window?

Thanks!

---

### Post by Bölvaður on 2009-09-09
Windowed : Alt + Enter
or change this line the file *~/.warsow/basewsw/config.cfg*
seta vid_fullscreen "1"
to "0"

according to the warsow wiki page you can enter the following in the console
r_mode -1
vid_customheight h
vid_customwidth w
vid_restart

Which means that you can change this config file *~/.warsow/basewsw/config.cfg* and look for
seta r_mode 

and change it to

seta r_mode "-1"
seta vid_customheight 1280
seta vid_customwidth 1024


you can also just change seta r_mode to something like
[QUOTE=warsow wiki page]Sets the resolution, I've fetched the modelist from Q3, hope they apply to the Qfusion engine as well:

Mode -1: Your custom resolution, which is defined by vid_customwidth and vid_customheight

Mode 3: 640x480
Mode 4: 800x600
Mode 5: 960x720
Mode 6: 1024x768
Mode 7: 1152x864
Mode 8: 1280x960
Mode 9: 1280x1024
Mode 10: 1600x1200
Mode 11: 2048x1536 [/QUOTE]


mine is set to:

seta r_mode "9"
I have had problem with one computer not sometimes being able to show fullscreenprograms in 800×600 but any other resolution is fine.

---

### Post by tommyvo09 on 2009-09-09
what a great info, thanks.
Thanks so much for this. I appreciate the effort. It really helps a lot.
  [COLOR=black][FONT=Arial][[color=#FFFFFF]_ financement credit personnel | taux demande simulation pret en ligne _](http://pretpersonnelenligne.org)[/color][color=#FFFFFF]à la disposition des particuliers un logiciel pour une simulation de prêt personnel en ligne[/color][[color=#FFFFFF]_ financement credit personnel | taux demande simulation pret en ligne _](http://pretpersonnelenligne.org)[/color][/FONT][/COLOR]
:popcorn::lolflag::guitar:
[COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by The Bright Side on 2009-09-10
Works! Thanks! :-)

---

### Post by ArunavAm on 2010-12-02
> **Bölvaður said:**
> Windowed : Alt + Enter
or change this line the file *~/.warsow/basewsw/config.cfg*
seta vid_fullscreen "1"
to "0"

according to the warsow wiki page you can enter the following in the console
r_mode -1
vid_customheight h
vid_customwidth w
vid_restart

Which means that you can change this config file *~/.warsow/basewsw/config.cfg* and look for
seta r_mode 

and change it to

seta r_mode "-1"
seta vid_customheight 1280
seta vid_customwidth 1024


you can also just change seta r_mode to something like



mine is set to:

seta r_mode "9"
I have had problem with one computer not sometimes being able to show fullscreenprograms in 800×600 but any other resolution is fine.
Thanx a ton for the info.... It's a common operation for any quake engine to set custom resolution this way (QUAKE/ ALICE/ DOOM Whatever....) which I mastered in Windows. But u hav let me find the .cfg to edit in my new Ubuntu 10.10 .... thanx buddy :) BTW... The game rocks...!!!

---


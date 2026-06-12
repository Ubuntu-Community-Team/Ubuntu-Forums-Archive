---
title: "UT 2004 and Sound?"
date: 2005-03-29
forum: Gaming &amp; Leisure
---

### Post by Drakx on 2005-03-29
Greatings

I seem to be having a small problem with sound on my UT2004 game when i load it there is no sound!!

I have a Sound Blaster Live if that helps

any one know how to solve this? 

Please

---

### Post by Drakx on 2005-03-29
Farcry too has the same problem please help

---

### Post by Whiffle on 2005-03-29
does it work anywhere else? 


When you run UT2004 from a terminal, grab the output and post it, i bet it has something useful to say.

---

### Post by Drakx on 2005-03-29
Thanks for the reply

All sound works from Xine right throught to opening a terminal but as soon as i open UT2004 and FarCry. Infact any game it seems

Oh i'll post the out put of the terminal asap just in win at the mo  :oops:  sorry!

---

### Post by GigaShadow on 2005-05-01
Did you ever get a resolution here? I have the same issue and would like to find out what the problem is.

              G

---

### Post by Janne on 2005-05-31
Just out of curiosity.. How is your ut2004 running with linux? I'll be installing it later today and im already a bit worried about my ati card  :|

---

### Post by Ribs on 2005-06-02
Hi,

Looks like esd and your games are clashing (esd is the thing which manages sound in Gnome, if you didn't know). A simple (but ugly) fix for now is to kill esd before you play. For example;
```
killall esd
ut2004
```When you've finished playing, make sure ut2004 is closed (Ctrl+C if you have to, I know it doesn't always close properly) and run;
```
esd &
```to restart esd (you'll hear strange beeps, this is normal and is a re-assuring sign that esd has started again)

I know there is a proper way to make ut2004 work okay with esd (and other games). But I can't for the life of me remember what it is. I'm planning to play ut2004 later today, so I'll look into it then :)

Happy Fragging... :)

-Ribs.

---

### Post by Gaming_Junkie on 2005-10-28
I tried killall esd, and then sound works with all my other games, just not UT 2004 for some reason.

---

### Post by Gaming_Junkie on 2005-10-28
[QUOTE=Janne]Just out of curiosity.. How is your ut2004 running with linux? I'll be installing it later today and im already a bit worried about my ati card  :|[/QUOTE]

UT 2004 Runs great on Linux, I think a little faster than on Windows.  Not sure about your ATI card working properly though.  I hope you're on Breezy, because there's better driver support there.  It installed my new sound card perfectly (I now hear Doom 3 in 5.1).  I run a GeForce 5200 FX myself, and UT 2004 runs really well.

about sound---
killall esd does not work for sound on UT 2004.  It does, however, work on the other games I've tried (Frozen Bubble, Doom 3).  Could it be something with the config file?

---

### Post by vega113 on 2005-12-01
strange i killed esd and sound worked on ut2004.
you might need to set sound configuration(alsa) , i googled and found how to do it.

---


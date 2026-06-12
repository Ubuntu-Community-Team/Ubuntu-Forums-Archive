---
title: "All games crash."
date: 2007-08-10
forum: Gaming &amp; Leisure
---

### Post by itehjosh on 2007-08-10
All games that I have played and installed under linux crash after loading the map (about 20 seconds to 2 minutes in to it) Which include:
Counter-Strike 1.6 (wine)
Nexuiz
OpenArena

They don't crash right away it takes them atleast 30 seconds into the game for it to crash and the game looks very smooth and plays 100 fps so I'm not sure what this is.

---

### Post by hikaricore on 2007-08-10
Do they actually crash and close?  Or does your system lockup?

Video card?  What drivers are you using?
And any other hardware/configuration info you could share might help someone help you.

If just the games are crashing run them from command line and watch for any error output .
(aside from WINE, don't post WINE error output here as it is mostly useless)

---

### Post by Bofur on 2007-08-11
Have you tried playing with your graphic options(ex. changing resolutions) at all? I remember when my Source games used to crash because one of my graphics options was on high instead of medium

---

### Post by MaximB on 2007-08-11
run them from a command line and print us the output after it crashes.

---

### Post by h4mx0r on 2008-03-29
I get a similar problem any 3d game I play crashes after a while. I've tried getting the error output but it looks like a perfectly clean exit something about signal 11. On occasion it doesn't crash cleanly and the game will knock me back to options menu or something while spitting out weird C code jibber so I just click ok and go. I think the problem is related to not having enough power for the awesome graphics card I have my power supply is only 250watt and it heats up after a while of gaming. My experience with this problem isn't as severe as yours it will usually play for a while like 10-30 minutes. I'm using a nvidia geforce 7300gs with the nvidia-glx-new package for ubuntu gutsy (7.10) and its version 100.14.19 . I haven't done anything custom to the kernel though this is pretty plain setup. I also dualboot and windows seems to be fine with executing the same stuff although on some games ran under windows I notice little patterns engraved onto the graphics like looking through a dirty screen perhaps a shader issue? At one point I noticed a slight purplish tint bottom left on loading 3d apps but after opening up my system and reseating the card it went away. Also what exactly does Option "dpms" do under xorg.conf could that have anything to do with this error?

---

### Post by h4mx0r on 2008-03-31
Problem found and wow do I feel like a noob! I did nvclock -T command and noticed the temperature was absurdly high and after some poking around while the system was running noticed it was actually kind of hot. I turned everything off and let it cool then took out the graphics card and removed the fan it had. The thermal goo stuff was all glopped on the wrong way and not making contact with the fan base. I cleaned it with some damp cotton swab (those things used for cleaning your ear) then I let it dry for an hour. Next I put a tiny bit of artic silver 5 thermal paste on it and smeared it evenly over the top of the small cpu to the graphics card. I pressed down the fan to make sure it was firmly attached and held it for a few minutes to make sure it was in place.

Before:
67C- idle
76C- under load

After the first boot:
40C- idle
57- under load

Awesome results! And I expect it to be even better after the paste sets in hardening. My only guess as to my windows partition not complaining about such issues is that its not using the graphics card to its fullest or it just doesn't have such safety features for hardware.

---


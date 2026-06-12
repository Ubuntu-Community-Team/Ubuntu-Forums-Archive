---
title: "wow freezes on loading screen"
date: 2007-10-05
forum: Gaming &amp; Leisure
---

### Post by Nyxess on 2007-10-05
im using the newest version of WINE. i've just updated my drivers, and my video card(NVIDIA GeForce NX7600GS) works fine with WoW. 

oh, I'm using Ubuntu 7.04

the first problem i had was that upon starting WoW, i would hear the music, and the WoW cursor would appear, but the screen stayed the same as before i started wow(i could still see my background). i fixed this problem by updating my drivers.

now i have another problem.  i use the command in Terminal: <wine "C:\Program Files\World of Warcraft\WoW.exe"> to start WoW. WoW will load, and i select my character, and click Enter World. about halfway through the loading prcess, the screen goes to black and white(the same thing that happens when a program usually freezes, i think). then the color comes back, and it shows 100% loaded, then the color fades again and it stays like this. It seems to only open in highly populated areas(asi can log in with my other characters, but not with this specific one, which happens to be outside of Karazan at peak raiding times). Any idea of how to fix this? I've disabled all my addons and set my video options all the way down.

---

### Post by mrtrick on 2007-10-09
What do you mean by the latest version. Are you running 0.9.46? Did you also try running it with the opengl flag?

wine "C:\Program Files\World of Warcraft\WoW.exe -opengl"

---


---
title: "How is this possible?!"
date: 2007-06-24
forum: Gaming &amp; Leisure
---

### Post by Asian_Wannabe on 2007-06-24
I installed ubuntu about a month ago and decided to put World of Warcraft on it. It gave me a few problems which were easily fixed :D. But on my old machine (Windows XP) I used to play WoW all the time, averaging about 10-15 fps in Ironforge even with a good graphics card. Now when I play WoW in ubuntu, I average 40-50 fps in ironforge :o! How is it that a machine not designed to play this game natively can manage to play it better than the machine it was made for?

---

### Post by mitchellthegreat on 2007-06-24
Because windows is a piece of junk and ubuntu is better in almost every way. ITS COMMON SENSE!:p

---

### Post by Asian_Wannabe on 2007-06-24
Hmm....makes sense to me :tongue:

---

### Post by insane_alien on 2007-06-24
bet you had a lot more back ground processes in XP. probably had an antivirus, firewall, etc etc. running in the background. caould be lots of reasons, including malware.

---

### Post by steveneddy on 2007-06-24
Linux, even running games through WINE, has less overhead that any Windows machine. 

Want real gaming power? Make yourself a log on that can run games, but has nothing running except what you need to run the game. The FPS and the performance will be unbelievable.

---

### Post by Asian_Wannabe on 2007-06-24
Can you explain how to do this to a noob? :)

---

### Post by steveneddy on 2007-06-24
You can search the forums for this answer, but little things like turning off your wallpaper and making it one color, or no color at all. 

If Gnome has transparent tool bars, make them opaque.

Turn off any services that you don't need at start up so the system resources will be free to run the game.

Then have a regular log in that has Beryl, wallpaper and such for the computing thing.

The less you have running on the machine when running the game, the more power goes to the game.

Maybe you could install Fluxbox and log on to Flux and game from there. Now that will save your power for the game.

---

### Post by cogadh on 2007-06-24
I posted [this mini how-to]("http://ubuntuforums.org/showpost.php?p=2542267&postcount=6") about two months ago. It explains how to create a script that will launch a game through Wine in its own X session without having your window manager (Gnome, KDE, etc.) running in the background at all. Basically, it removes an entire layer out from between your game and the OS/hardware and frees up almost all those resources that are normally dedicated to the GUI interface. The performance improvement can be very dramatic, although the method for launching the game is a bit cumbersome. I'm sure someone way smarter than me could come up with a better way to do it, but this method has worked great for me.

Just to give credit where credit is due, I did get the basic script structure from a WoW how-to someone else had posted here, but the method actually works for any Wine game.

---

### Post by Asian_Wannabe on 2007-06-24
Thanks dude! I got about 5-10 extra fps with that :D

---


---
title: "New Sauerbraten released!"
date: 2010-07-24
forum: Gaming &amp; Leisure
---

### Post by tommcd on 2010-07-24
Sauerbraten 2010-07-19 "Justice Edition" has just been released. There is supposed to be a new version out in 2011 also:
[http://www.phoronix.com/scan.php?page=news_item&px=ODQ0MA](http://www.phoronix.com/scan.php?page=news_item&px=ODQ0MA)
[http://sauerbraten.org/](http://sauerbraten.org/)
There are new maps, new game modes, and the graphics look a bit better I think.
I thought I had read previously that the developers of Sauerbraten had quit developing this game in order to focus on Blood Frontier. Glad to see Sauerbraten is still in active development.

---

### Post by J.K.Makowka on 2010-07-24
Bloodfrontier is dead, now there is RedEclipse :p

But both of those projects were made with only limited contributions by the Cube2 makers.

But yeah the new Cube2 release is pretty nice... real solid release, with cool new maps, especially for CTF.

---

### Post by tommcd on 2010-07-24
> **J.K.Makowka said:**
> Bloodfrontier is dead, now there is RedEclipse :p
Hmm, I did not know that. I have not been keeping up with this stuff. I will have to check out Red Eclipse.
Some of the screen shots on the Red Eclipse site look a lot like Sauerbraten.

---

### Post by Bramkaandorp on 2010-08-05
After reading about the update, I wanted to know how I can install it.

I already have the version from the repository, so if I can add other repositories or something similar, I would be very happy.

Cheers

---

### Post by tommcd on 2010-08-06
> **Bramkaandorp said:**
> 
I already have the version from the repository, so if I can add other repositories or something similar, I would be very happy.

You can just download the sauerbraten_XXX.tar.bz2 file to your /home direcory. Then untar it:
```
tar -xvjf sauerbraten_XXX.tar.bz2
```
(Note: Replace the XXX with whatever the version number is.)
Then cd into the newly created sauerbraten directory:
```
cd sauerbraten
```
Then make sure the sauerbraten_unix file is executable. If it is not then make it so:
```
chmod +x sauerbraten_unix
```
Then run it:
```
./sauerbraten_unix
```
And you should be good to go.
You may want to remove the sauerbraten version from the Ubuntu repos, just to prevent any conflicts with your ~/.sauerbraten directory.

NOTE: On my system, since I had removed pulse audio, I had to install *libsdl1.2debian-alsa*. This removed *libsdl1.2debian-pulseaudio*, which I had not removed before, and installed *libsdl1.2debian-alsa*. This was necessary for me to get sound on sauerbraten. If you still have pulseaudio, or you have libsdl1.2debian-alsa installed, this will not apply to you.

---

### Post by Mozenrath on 2010-09-21
The game plays great but then suddenly slows down my entire system when the server changes maps. :(

---


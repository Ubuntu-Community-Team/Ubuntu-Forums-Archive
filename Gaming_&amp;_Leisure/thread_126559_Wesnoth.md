---
title: "Wesnoth"
date: 2006-02-06
forum: Gaming &amp; Leisure
---

### Post by qalimas on 2006-02-06
I installed Wesnoth 1.0.2 from a repository for Ubuntu, but I noticed when making or loading a game, it lags, a lot.  I'm running a 2500+ 64bit Sempron, it shouldn't do that.  Should I compile from source to fix it or will that be useless?

---

### Post by curuxz on 2006-02-07
Which repo?

---

### Post by qalimas on 2006-02-07
deb [http://deb.svx.pl](http://deb.svx.pl) breezy main universe restricted

---

### Post by gil-galad on 2006-02-07
Do you have 3d acceleration?

---

### Post by qalimas on 2006-02-07
Yeah, I have an nVidia 5200 with the drivers instlaled.  Wesnoth gaming itself isn't slow, but starting the game, example once I hit I'm ready in an online game, everyone will ahve their screens up and playing, but mine is still loading and stuck on the screen where it lists the people in the room.  Or once I hit load game on the title screen and pick my game then press 'load', it'll take 10-20 seconds before it actually loads the game and Wesnoth will act liek it's frozen.

---

### Post by qalimas on 2006-02-07
Nevermind, the guys at the Wesnoth board got me fixed up :D  It seems the Ubuntu Wesnoth uses compressed files and each time I made or loaded a game, they got uncompressed and cached.  I got rid of them and just unzipped the files to the Wesnoth dir, and all works like it should :D

---

### Post by Harleen on 2006-02-07
You don't need 3D acceleration.
The short freezes are quite normal, but they shouldn't be that long as you experience. I haven't taken the time, but I'd say it's only about 5 seconds (on an AMD XP 2000+). In that time everything stops - even the mouse won't move. This is true for Ubuntu and Windows, so that seems to be an issue of Wesnoth and not on your side.

Edit: too slow.... But can you provide a link to the wesnoth forum thread or describe which files to unzip? I'd really like to try that out.

---

### Post by qalimas on 2006-02-07
They didn't tell me what to unzip, I figured it out on my own.  Unzip all files in /usr/share/games/wesnoth/ to the directory the zips are in, you should end with about 5 folders (some directories such as data need to be overwritten, don't worry, no files will be delted or anything)

---


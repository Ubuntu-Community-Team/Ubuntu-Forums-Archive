---
title: "How To: Quake 2 on Hardy"
date: 2010-01-18
forum: Gaming &amp; Leisure
---

### Post by spcwingo on 2010-01-18
Just thought I would let ya'll know that even though it was a real bear, I have Quake 2 running on hardy without a hiccup.  For those interested here are the steps I took to install:

1.  Grab the quake2 package from here: [http://packages.ubuntu.com/dapper/quake2]("http://packages.ubuntu.com/dapper/quake2")

2.  Install the quake2 package (this will also pull in libsvga1 and quake2-data).

3.  Install the packages libsdl1.2debian and libsdl1.2debian-pulseaudio (or libsdl1.2debian-alsa).

4.  Pop in you Quake 2 CD and mount 'er up (it's not absolutely essential to have this, but you won't be able to install the full game).

5.  Open a terminal and run this command:

```
sudo dpkg-reconfigure quake2-data
```

then follow the on-screen instructions.

6.  Run quake2 once from the terminal by inputting "quake2".

7.  Open the file ~/.quake2/baseq2/config.cfg with gedit (or your favorite text editor) and replace:

```
set snddriver "oss"
```

with

```
set snddriver "sdl"
```

You're now good to go.  If you would like to add Quake 2 to your menu I suggest pointing the command to /usr/lib/games/quake2/quake2.real instead of just quake2.  The reason I recommend that is if not you will have a terminal emulator open in the background waiting for you to type in "yes" about confirming the security risk of playing online.  ;)

---


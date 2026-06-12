---
title: "Xwinwrap Gutsy Gibbon?"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2007-11-19
How would i set-up xwinwrap to work with ubuntu gutsy 7.10? As far as i can tell the repos for xwinwrap are only supported up to 7.04, am i wrong?

---

### Post by kdarkentity on 2007-11-19
Ok i read some more and i have xwinwrap installed but now i cannot figure out how to set a video as a wallpaper.

---

### Post by Forlong on 2007-11-19
```
sudo apt-get install mplayer
```

```
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg
```
[http://en.opensuse.org/Xwinwrap](http://en.opensuse.org/Xwinwrap)

---

### Post by kdarkentity on 2007-11-19
> **Forlong said:**
> ```
sudo apt-get install mplayer
```

```
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet movie.mpg
```
[http://en.opensuse.org/Xwinwrap](http://en.opensuse.org/Xwinwrap)

where do i put the movie.mpg file?

---

### Post by Forlong on 2007-11-19
Just replace *movie.mpg* with the */path/to/the/movie/you/want/to/use.mpg*

---

### Post by kdarkentity on 2007-11-19
> **Forlong said:**
> Just replace *movie.mpg* with the */path/to/the/movie/you/want/to/use.mpg*

does it have to be an mpg?

---

### Post by Forlong on 2007-11-19
No.

---

### Post by kdarkentity on 2007-11-20
why does my screen turn blue when trying to play a vdeo as a wallpaper?

---

### Post by kdarkentity on 2007-11-24
alright i have it working, now can i do this, can i set it play at start-up, can i get to play in a loop and can i make it so its now windowed?


also when i tell nautilus to stop drawing my wallpaper ,it also stops drawing my icons, in addition to that i have to be using metacity as my window manager otherwise i can't see the video being played.

---

### Post by curtis1552 on 2008-02-02
To start with startup goto System ; Preferences ; Sesson 
Create a new program for startup (cliack ADD)
then type the line you use to setup the player 
i'm using xwinwrap and the xmatrix screensaver so i type:
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/xmatrix -window-id WID -small -delay 50000 -density 60 -crack
Give it a name/desc and try the restart.

---

### Post by kdarkentity on 2008-02-02
> **curtis1552 said:**
> To start with startup goto System ; Preferences ; Sesson 
Create a new program for startup (cliack ADD)
then type the line you use to setup the player 
i'm using xwinwrap and the xmatrix screensaver so i type:
xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/xmatrix -window-id WID -small -delay 50000 -density 60 -crack
Give it a name/desc and try the restart.

wow thats cool i'll have to give it a try when i get the chance.

---

### Post by blackvd on 2008-02-06
This is really cool but I'm not seeing a way to kill the sound of the video playing? Also would there be a way to loop the video?

---

### Post by kdarkentity on 2008-02-06
> **blackvd said:**
> This is really cool but I'm not seeing a way to kill the sound of the video playing? Also would there be a way to loop the video?

i imagine it can be done, i just did a google search and found this [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=662046]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=662046"). I dont have mplayer and xwinwrap installed right now and i am currently booted into windows so I'll have to play with it later.

---

### Post by blackvd on 2008-02-06
Cool thanks for the reply. I found the -loop argument earlier must be a way to kill sound too. I'll check mplayer commands didn't notice that's all it was using. Ha it's just -nosound >.<

---

### Post by curtis1552 on 2008-02-06
add -quiet for silent movie playback

pulled from this thread
[http://ubuntuforums.org/showthread.php?t=319503](http://ubuntuforums.org/showthread.php?t=319503)

---

### Post by kdarkentity on 2008-02-08
Hmm.. neat, did we figure out how to get it to be unwindowed yet?

---

### Post by curtis1552 on 2008-04-10
1. I enabled Extra Visual Effects located indet System>Preferences>Appearance> (tab) Visual Effects.
2. Run the video file. The original list on this post would work except for sound, for which it uses the wrong command. -quiet is for xscreensaver -nosound is for mplayer. The command I used is

xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet ~/Desktop/REM-Endoftheworld.avi -nosound

This ran the REM movie as a transparent video on my desktop, giving me access to both my icons and watching the movie quietly. 
This also enable and untitled window, which I didn't have last time I ran it, so I'll see if I can get rid of it by starting at bootup.
More later.

EDIT

add the -fs (fullscreen option) to remove the 'window' marker.
new command line is:
 xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet ~/Desktop/REM-Endoftheworld.avi -nosound -fs

good luck implementing.

REDIT
I got interested again,
 xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet -nosound -fs -enqueue ~/background/* -loop 0  -nosound -fs
this plays ALL videos files in the folder background inside of my home directory. The -fs MUST be last to avoid having a 'window'. the loop command loops the playback. Hella lotta fun now.

---


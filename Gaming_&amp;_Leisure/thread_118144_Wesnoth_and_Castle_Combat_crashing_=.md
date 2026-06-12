---
title: "Wesnoth and Castle Combat crashing =\"
date: 2006-01-16
forum: Gaming &amp; Leisure
---

### Post by moomooman on 2006-01-16
First of all, I should tell you that I am a COMPLETE newb to Linux.... 

Anyways, I was looking for a couple of games to play on my brand new Ubuntu, and I found Castle Combat, Wesnoth, and Falcon's Eye... CC and FE I just couldn't install, and after slaving for a whole day on Wesnoth I finally installed it, but I got some SDL I/O error and some eror about initializing video. I searched the forums, and saw they are all on repo -thank god! So I quickly downloaded them from the package manager....

FE seems to work, but when I run Wesnoth I get diagonal lines across a black screen and the thing freezes. CC doesn't even bother with the lines and crashes :-\
No ctrl alt bspace for me either!! What's up with that?

*EDIT:* Well, it turns out that all FE does is start up properly, after I select my char stats it blacks out and freezes, it's unkillable too...

---

### Post by moomooman on 2006-01-17
Errrm... Anyone? :(

---

### Post by dragonfyre13 on 2006-01-17
I'll give it a shot.

What Video card are you using?
Are you using Kubuntu, Xubuntu, or Ubuntu?

First things first, after you answer the above, run Terminal. (It's in Applications->Accessories)

Type "falconseye" (With no quotes)

It will run Falcons Eye. Let it crash, and then move the evil black screen to the side, so you can get to the terminal.

Copy everything in the terminal, and paste it here.

---

### Post by moomooman on 2006-01-18
Well, I'm running Ubuntu and have a Geforce 6600 GT, I've downloaded the driver, and now CC works.... Falcon's Eye still doesn't.... Terminal just says 
"$ falconseye
............................................"
And Wesnoth no longer freezes, it just crashes and says:
> $ wesnoth
started game: 3720582290
Could not initialize audio: No available audio device
error display: could not open image 'wesnoth-icon.png'
Checking video mode: 1024x768x16...
32
setting mode to 1024x768x32
error display: could not open image 'cursors-bw/normal.png'
null neutral surface...
locale could not be determined; defaulting to system locale
No [language] block found in english.cfglocale could not be determined; defaulting to system locale
No translation for locale 'System default language', default to system locale
No [language] block found in english.cfgLanguage data not found
locale could not be determined; defaulting to system locale
Could not open or create directory: '/home/david/.wesnoth/cache'
caching cannot be done. Reading file
started music
574385312
showing title screen...
574385313
null neutral surface...
error display: could not open image ''
error display: Could not find title image
error display: Could not find game logo
error display: Failed opening font: Vera.ttf
error display: Could not get font for size 10
error display: Failed opening font: Vera.ttf
error display: Could not get font for size 12
error display: Failed opening font: Vera.ttf
error display: Could not get font for size 12
error display: could not open image 'buttons/button.png'
error display: could not open image 'buttons/button-pressed.png'
error display: could not open image 'buttons/button-active.png'
error display: could not open image 'buttons/button-active-pressed.png'
could not find button image: 'buttons/button.png'
error writing to preferences file '/home/david/.wesnoth/preferences'
closing audio...
Could not create button: Image could not be found

Could this be due to me poorly uninstalling Wesnoth before downloading it from the repo?

---

### Post by mdbarton on 2006-01-20
Falconseye: 

```
sudo gedit /etc/falconseye/jtp_opts.txt
```

comment out the following lines:
```
play_music=1
play_effects=1
linux_midi_player=/usr/bin/timidity -idqq %s
linux_mp3_player=/usr/bin/mpg123 -q %s
```

Worked for me! :D

Never played FE before, but like it a lot - shame there is no sound... :confused:

If you have trouble killing it again, run xkill.

---

### Post by moomooman on 2006-01-21
Thanks! God, you'd think it'd tell you if there was a sound prob... I downloaded Timidity and Freepats, and it works fine now - music and all :D

I also downloaded a newer version of Wesnoth from another repo... Now the only problem is that I can't save... At all!
No autosave or manual, and I can't download any campaigns except through the package manager. Could it be yet another permission problem? (I'm really getting sick of those =\)

---

### Post by moomooman on 2006-01-24
No one has any idea?

---

### Post by mike998 on 2006-01-24
I don't know where it saves or if you installed it using sudo...
However, go to your home folder, view hidden files (ones that begin with a full stop or period) and change the ownership of the .wesnoth (guessing here!) folder to your username.

---


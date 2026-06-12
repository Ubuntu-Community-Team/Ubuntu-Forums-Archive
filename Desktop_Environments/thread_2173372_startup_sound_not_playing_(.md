---
title: "startup sound not playing :("
date: 2013-09-09
forum: Desktop Environments
---

### Post by Coder88 on 2013-09-09
Using the Startup Applications from my System Tools:Preferences:StartupApplications menu, I clicked the Add button and added  and entry with this command line (I copied the .ogg file to my user account), which I tested in a terminal to be sure it would play and that the path was typed correctly:
play  /home/beowulf/Music/SystemSounds/KDE-Sys-Log-In-Short.ogg
Saved the entry. 
But if I logout then login, I do not hear that .ogg sound file play. But my sound is configured, I can hear the test speakers, I can play and hear music and video files. Soundblaster XFi-Titanium sound card. 
ArtistX Ubuntu 12.04

---

### Post by deadflowr on 2013-09-09
I generally run this command to launch a login sound
```
canberra-gtk-play  --file <filenamehere>
```
Or at least, that's what I add to the command section of start-up applications.
And I replace filenamehere with the full path to the file.

---

### Post by Coder88 on 2013-09-09
> **deadflowr said:**
> I generally run this command to launch a login sound
```
canberra-gtk-play  --file <filenamehere>
```
Or at least, that's what I add to the command section of start-up applications.
And I replace filenamehere with the full path to the file.

I actually tried that at first before just using the play command. When I tried command line canberra-gtk-play it would play a sound. Then I would exit the terminal. But then my audio was gone and I could no longer play music/video, testing sound config gave only silence. Something about canberra really messed up my system sound. I even tried killing any canberra processes.

---

### Post by Coder88 on 2013-09-09
> **deadflowr said:**
> I generally run this command to launch a login sound
```
canberra-gtk-play  --file <filenamehere>
```
Or at least, that's what I add to the command section of start-up applications.
And I replace filenamehere with the full path to the file.

Wait, maybe i was using cabberra wrong? I was doing:
canberra-gtk-play  --file[COLOR=#800000]**=**[/COLOR]filenamehere
but I see you do
canberra-gtk-play  --file <filenamehere>

---

### Post by deadflowr on 2013-09-09
I don't know if I added an extra space bertween the canberra command and --file or not, but in general it looks like
```
canberra-gtk-play  --file /home/me/folder/anotherfolder/sound.ogg
```

I also tend to run a command through the terminal to see if it'll run right.

---


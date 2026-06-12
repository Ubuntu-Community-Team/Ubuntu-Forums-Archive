---
title: "I Can't Play an Audio CD"
date: 2006-01-28
forum: Desktop Environments
---

### Post by danish_demon on 2006-01-28
alright, the thread title is pretty self-explanatory but i will describe what is going wrong.

when i try beep and attempt to open cd, it gives me an error along the lines of "no audio cd detected or cd inserted is not of correct format".

when i try sound juicer and hit play (it correctly reads and identifies the cd), it says "error playing cd.  reason: could not open resource for writing".

gnome cd player will again correctly identify the cd, but when i hit play it immediately turns the play/pause button back to play without doing anything else.

i can't figure out how to get mplayer to open a cd, so that just might be my fault.

rhythmboxx uses sound juicer, so that's that.

with totem, when i try to play a cd, it says, "Totem could not play 'cdda:/1'. This is an audio-only file, and there is no audio output available."

vlc and xmms will both play the cd, but no sound.  i have the master volume at a medium level and the volume in the individual players is at a medium/high level.

any ideas?

thanks in advance.

---

### Post by public_void on 2006-01-28
Try closing all other applications, then try vlc. File --> PlayDisc and choose Audio CD. If it works then it means the problem is the audio sharing thing. I'm not too sure why but only one program my use the sound driver. I think it effects alsa, or oss. 

Please someone correct me, as I'm too sure of the reason.

---

### Post by danish_demon on 2006-01-28
[QUOTE=public_void]Try closing all other applications, then try vlc. File --> PlayDisc and choose Audio CD. If it works then it means the problem is the audio sharing thing. I'm not too sure why but only one program my use the sound driver. I think it effects alsa, or oss. 

Please someone correct me, as I'm too sure of the reason.[/QUOTE]

i tried that with the same results.  :(   i should also mention that i am able to play mp3 files, so i know that my audio works (at least for mp3s).

---

### Post by danish_demon on 2006-01-29
just bumping this...  

i don't really envision myself listening to many cds on my laptop, but i would like to know that i can when i want to. :)

---

### Post by danish_demon on 2006-01-30
alright, i think part of the problem might be having more than one user logged in.  i don't know how to fix it (besides forcing a log out or restarting the laptop).

---


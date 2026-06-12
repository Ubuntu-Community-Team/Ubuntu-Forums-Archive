---
title: "Play sound when mouse hovers over icons"
date: 2008-09-08
forum: Desktop Environments
---

### Post by berale on 2008-09-08
Hi all,
I'm using ubuntu 8.04 and I'm trying to setup a simple desktop environment for my daughter who still cannot read. Apart from using large, colorful desktop icons and disabling panels I would like specific audio files to be played when the mouse pointer is hovering over some icons, something like mpg321 audio preview in nautilus but for non audio files as well. Just to make it easier for her to remember what each icon stands for.

Any ideas?

Furthermore, if you know of any examples of how to configure Ubuntu and make it 'child friendly' please let me know.

Thanks in advance

---

### Post by wolke on 2008-09-09
cool endeavor.

i tried to find a way to run arbitrary code when mouse hovering, but there is no way i could find without recompiling nautilus.


i did, however, figure a ridiculous way to implement this that meets all of your requirements, but is quite silly.

1) make a file called magic.mp3. have it be a recording of you saying 'this performs magic'. change the icon for all mp3 files to be a pointy hat with stars. put the file on the desktop, and stretch the icon.
repeat for fish.flac, sing.ogg, etc. 

2) make mp3 files, ogg files, flac files, etc. open with a simple script that performs an action based on the filename. either do some special thing, or open the file with your music player.

if $arg eq 'magic.mp3': do magic;
elif $arg eq 'fish.flac': do fish;
else: vlc $arg;


this way, audio preview will preview the file, but running the file can execute arbitrary code. this will only give you, say, 4 icons. they would be pretty and talk to your daughter, but her other music icons would look like hats or fish.

---

### Post by berale on 2008-09-15
Thanks Wolke, great idea. And it also works making it an even better solution.
BTW, in gnome you can change a given icon without effecting all other icons of its file type. You can therefore create these 'audio launchers' from just one type of audio files (e.g mp3) and their number is not limited to the system recognized audio formats.
Even better than what you thought.

---


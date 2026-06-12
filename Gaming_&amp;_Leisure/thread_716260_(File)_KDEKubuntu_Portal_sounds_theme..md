---
title: "(File) KDE/Kubuntu Portal sounds theme."
date: 2008-03-05
forum: Gaming &amp; Leisure
---

### Post by FrozenFox on 2008-03-05
Hi guys,

I made a quick and dirty (but seriously amusing) system sound theme to replace the small collection of sounds enabled by default in KDE from sound clips of Valve's Portal. I will add more later to replace the ones not enabled by default, I suppose. I'll also make one specifically for gnome at some point if no-one else beats me to it.

Instructions (Kubuntu or KDE only. This won't work for normal ubuntu users until I make a gnome version or someone changes this one):

1) Download the file from the bottom of this post to your desktop.
2) In the terminal/console/konsole, run the following lines.
3) sudo mkdir /usr/share/sounds/originalsounds
4) sudo cp /usr/share/sounds/* /usr/share/sounds/originalsounds
[NOTE: its unnecessary to back up ALL the sound files like this, but its quicker than the line to copy the specific files we will be changing, and the sounds folder is not very large anyway.]
5) tar -xvf ~/Desktop/KDEPortalSounds.tar.gz
6) sudo cp ~/Desktop/KDEPortalSounds/* /usr/share/sounds

In non-command-line jibberish, you're downloading the file, decompressing it, backing up your original system files, and then overwriting the old ones with the new ones. :p As an alternative to all of this, you can untar the files and put them somewhere else and set KDE to use them manually via kcontrol.

Done. :)


Edit: Sorry, I'm retarded. It would be a great idea to actually include the file.

---

### Post by Whiffle on 2008-03-05
I dont really use system sounds, at all, but if I did, I'd probably use these. :D

---

### Post by FrozenFox on 2008-03-05
Hehehe. 

"Hellooo..friend."

---


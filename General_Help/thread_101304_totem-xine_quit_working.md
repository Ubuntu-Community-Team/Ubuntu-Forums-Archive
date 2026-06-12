---
title: "totem-xine quit working"
date: 2005-12-09
forum: General Help
---

### Post by speckman on 2005-12-09
first it quit reading mp3s, then it had trouble with dvds, now it won't even read oggs.  i have all of these plugins in /usr/lib/xine/1.01/ (like i had before when it worked)

i know it's something stupid.  this ring a bell to anyone?

cause of my soundcard (delta 1010), i am using xine.

---

### Post by AllenGG on 2005-12-09
Darn it all, wished that I didn't know about  it, but I do. Such a pain
I caused my problem by experimenting without researching.
Then I managed to [COLOR=DarkOrange]"lose" libdvdcss2. [/COLOR]
So I did a removal,  then a new install, the added _"VLC" from VideoLan,_
then dug up libdvdcss2, a licensed program.
Totem G-Streamer conflicts. Using Synaptic, and the "all" section, highlight the program you wish to install, then move across to "Dependencies", scroll down and watch out for **[COLOR=Red]"conflicts"[/COLOR]**.
Removing several of the conflicting programs allowed Totem-Xine to work well, and of course I screwed it up again trying to add more "3D" programs.
Works really well now !!!
Allen:rolleyes:

---

### Post by speckman on 2005-12-09
man, it sure would help if this showed up visibly in synaptic.  like a little red ! !.
oops i dont know what i'm talking about.
yeah, i can get it running with sudo.
none of that helps though, the libs are all there, and the only thing conflicting is
xlibs 
totem-xine < .99 or something
totem-gstreamer (which isn't installed)

---

### Post by speckman on 2005-12-22
problem fixed with a synaptic "mark all updates" update.

dont know why though.  :)

---


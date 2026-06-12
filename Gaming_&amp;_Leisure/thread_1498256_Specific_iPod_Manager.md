---
title: "Specific iPod Manager?"
date: 2010-05-31
forum: Gaming &amp; Leisure
---

### Post by SubOneForty on 2010-05-31
hey all, ubuntu noob here which is probably obvious by my post count :p 


my question is, is there an iPod management program that can export the music from my iPod on my Music folder? but the way i want it done is, i would like each artist to have his own folder for example




Music -> The Beatles -> Abbey Road -> 01.mp3 02.mp3


so far everything i have done has just exported the song itself. help? thank you!

---

### Post by jaminthorns on 2010-05-31
Well, if you have already exported the music and all of the tags are correct, you can use Audio Tag Tool. Just search "tagtool" in synaptic and install it, then run it from the Sound & Video Menu. When it's opened up, change the working directory to wherever your music is and go to the "Rename Multiple Files" tab (the one with the two files and the gear). Under "File Name Format" enter "<artist>/<album>/<track>" and click go. That should group everything into the folder hierarchy you wanted and rename every track with its track number.

---

### Post by SubOneForty on 2010-05-31
it works for like 5 seconds, then it quits out. any idea s to why this is?

---

### Post by Noraphalem on 2010-06-03
Run it via terminal and copy/paste the output here. This could help a lot.

1. [Alt] & [F2] to open the run dialog
2. Type in "gnome-terminal" and press the [Enter] key
3. Type into the terminal "tagtool" or "audiotagtool" (I don't know exactly what is the name of the tool)
4. Mark the terminal output after the crash via the mouse
5. Copy it via right click & "Copy" (Or whatever it is on your machine)

---


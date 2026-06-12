---
title: "Beryl oh Beryl"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by Benbow on 2007-05-12
Thought I would give beryl a whirl and found the graphics quite something! However, it totalled my "movie player", it loaded flashed the start of the clip then nothing.
Next step was to try the beryl forum and I found that it does have that problem with MP and others of a similar ilk!
Turned off ubuntu and restarted, all ok. I am leaving beryl tucked up in her applications bed for the foreseeable future.

---

### Post by UbuntuniX on 2007-05-12
Switch back to Metacity and GTK for watching movies?

---

### Post by Campingman on 2007-05-12
Do the fixes mentioned in this thread help you out with movie playing when desktop effects are enabled?
[http://ubuntuforums.org/showthread.php?p=2493353&posted=1#post2493353](http://ubuntuforums.org/showthread.php?p=2493353&posted=1#post2493353)

---

### Post by notquitemichael on 2007-05-12
using vlc (and why not - it's great :P) seems to solve all my problems. it also allows you to play about with the output so the render (assuming you have an opengl card.) bypasses the window manager (it's in the advanced options as 'alternative methods') which should also help.

---

### Post by Goombie on 2007-05-12
Well, this fix worked for me with the same problem:

1) Open up a terminal, and type 'gstreamer-properties'. This will open up a little applet called the 'Multimedia Systems Selector.'

2) Go over to the 'video' tab.

3) under the section for 'default output', in the 'plugin:' combo box, choose 'X Window System (No Xv)'

4) Close the MSS, and enjoy your videos. :)

(I don't know if that fix will work for you, but I'd give it a shot, as the changes can be reversed.)

---


---
title: "aterm not reading .Xdefaults"
date: 2005-01-13
forum: Desktop Environments
---

### Post by dninja on 2005-01-13
I am running aterm and have setup the following .Xdefaults file:

Aterm*scrollBar: false
Aterm*transparent: true
Aterm*background: black
Aterm*foreground: white
Aterm*shading: 60
Aterm*fading: 55
Aterm*loginShell: true
Aterm*saveLines: 5000

However aterm is ignoring the file. If I pass the params on the command line the term picks the settings up.

I have tried with Xterm rather than Aterm and tried .Xresources file but nothing is working. The same file on other boxes is working but the other boxes are running fluxbox, this one is Gnome. Could this affect anything?

---

### Post by Kalden on 2005-03-14
I put this topic on top again....I have the same problem and can't find a solution...

---

### Post by dninja on 2005-03-15
Obviously no one else worries about his!

---

### Post by Kalden on 2005-03-16
I asked for help in the Afterstep / Aterm channel on Freenode. These guys were very helpfull and did several suggestions. None of these worked...
Maybe one of the "Ubuntu Master Roasters" can help us....

Greetz, Kalden

---

### Post by ladoga on 2005-03-16
[QUOTE=dninja]I am running aterm and have setup the following .Xdefaults file:

Aterm*scrollBar: false
Aterm*transparent: true
Aterm*background: black
Aterm*foreground: white
Aterm*shading: 60
Aterm*fading: 55
Aterm*loginShell: true
Aterm*saveLines: 5000

However aterm is ignoring the file. If I pass the params on the command line the term picks the settings up.

I have tried with Xterm rather than Aterm and tried .Xresources file but nothing is working. The same file on other boxes is working but the other boxes are running fluxbox, this one is Gnome. Could this affect anything?[/QUOTE]

This may sound stupid, but try to make those command lower case "aterm" instead of "Aterm" in both .Xresources and .Xdefaults. That's how i have it and it works.

---

### Post by fdoving on 2005-03-16
[QUOTE=dninja]I am running aterm and have setup the following .Xdefaults file:

Aterm*scrollBar: false
Aterm*transparent: true
Aterm*background: black
Aterm*foreground: white
Aterm*shading: 60
Aterm*fading: 55
Aterm*loginShell: true
Aterm*saveLines: 5000

However aterm is ignoring the file. If I pass the params on the command line the term picks the settings up.

I have tried with Xterm rather than Aterm and tried .Xresources file but nothing is working. The same file on other boxes is working but the other boxes are running fluxbox, this one is Gnome. Could this affect anything?[/QUOTE]
 try to run xrdb -merge .Xdefaults, and then start aterm.

---

### Post by Kalden on 2005-03-17
>  try to run xrdb -merge .Xdefaults, and then start aterm 

This one is doing the job. Thx fdoving.  =D>

---

### Post by dninja on 2005-05-04
Been off using fluxbox for a while, just given this a try and it does work, thanks.

---


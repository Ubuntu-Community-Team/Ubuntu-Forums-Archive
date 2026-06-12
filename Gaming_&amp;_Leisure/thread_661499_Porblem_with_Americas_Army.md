---
title: "Porblem with Americas Army"
date: 2008-01-08
forum: Gaming &amp; Leisure
---

### Post by accog on 2008-01-08
Hi, just a little problem here. I got AA to start installing and everything was going fine, but now in the space where it shows the progress bar in terminal it reads "waiting for already running kbuildsycoca to finish" and it does nothing. I scrolled up too see if it spewed out any errors. It says

accog@kickass:~$cd Desktop
accog@kickass:~/Desktop$ sudo bash ./armyops250linus.run
Verifying archive integrity... All good
Uncompressing Americas Army for GNU/Linux 2.5.0.....
Second stage unpacker running...
Starting actual installer...
/home/accog/.setup13885: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory.

I have 7.10 Gutsy running, Any help would be appreciated, thanks.

---

### Post by earobinson on 2008-01-08
you wont want to bother with aa becasue the most upto date version is not supported by linux :(

---

### Post by accog on 2008-01-08
I realize this. Thats why i DLed the 2.5 version. However I would still like to play it. I hear its like CSS and i LOVE that game. In the meantime I am getting ET.

---

### Post by accog on 2008-01-08
Shoot, i seem to be getting a similar problem in ET. It reads

/home/accog/.setup14538: Error while loading shared libraries: libgtk 1.2.so.0: Cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

---

### Post by Rhubarb on 2008-01-08
Try Assault Cube, it's simple play, and it's similar to CS, and works on linux / mac / windows fine.
[http://assault.cubers.net/](http://assault.cubers.net/)

---

### Post by accog on 2008-01-08
I may have found a solution. I just installed libSDL_mixer and and libSDL_image. Hope it works.:)

EDIT: sadly it didnt work, i'll try installing some more things :) *crosses fingers*

EDIT: Well, i have gotten this far.

accog@kickass:~$ armyops
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Cheat protection disabled
open /dev/[sound/]dsp: Device or resource busy
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.

History: 

Exiting due to error

Any ideas? please Help!

---


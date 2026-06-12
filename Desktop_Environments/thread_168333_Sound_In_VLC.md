---
title: "Sound In VLC"
date: 2006-04-30
forum: Desktop Environments
---

### Post by berwickboy on 2006-04-30
I have this problem, sometimes in VLC Media player it just wont play sound and other times it will, does anyone else have this problem/know the cure. Its highly frustrating. Thanks in advance

-John

---

### Post by gingermark on 2006-04-30
Sound in Linux can be a little bit of a pain.

KDE currently uses aRts to allow concurrent sound. This means if, say, you are using amaroK (with the aRts engine) and a system notification sounds, then you will hear it at the same time as your music.

The problem is, that not everything uses aRts (some might say that's a good thing - it is being dropped for KDE 4).

VLC has an aRts plugin you could install ('sudo apt-get install vlc-plugin-arts').
---------
EDIT: Sorry! Forgot to tell you what to do next. Open up VLC, and go Settings --> Preferences. In the Preferences dialog double-click "Audio" and select "Output Modules". Enable Advanced Options, and select "aRts audio output" in the dropdown box. Then click "Save".
---------

Another, less graceful way, is to disable the sound server before using VLC. To do this, Open 'System Settings' and click 'Sound & Multimedia'. Deselect "Enable the sound system" and click Apply.

You can always re-enable it when you're done with VLC.

Hope that helps.

---

### Post by berwickboy on 2006-05-01
Ah nice one mate, worked perfect. Cheers.

-John

---

### Post by Giga on 2006-05-01
i use VLC to watch dvd.

well.. after some time playing.. if i click on X to close the VLC window..
the program close (as expect to) but the sound keeps going!!!

any idea what might be cause that?


another thing.. what if the gnome sounds are dead, no signal, no mp3 play.. etc.
 but when i put a DVD with VLC, sounds play awesome...
im reset VLC to default.... same thing

by the way.. my sound card is Audigy 2 ZS (when i installed Ubunto, it was workign perfect.
but i didnt change any sound configuration , except in VLC)

Thanks

---

### Post by berwickboy on 2006-05-07
The VLC sound continuing is a VLC problem, i dont know how to fix it but i had that with windows, it stops after about 2 mins max.

I dont know much about Gnome as i use KDE but in "automatix" there is a box to download "Gnome sound fix" - "Corrects Sound Configuration in Gnome". That might be what your looking for, just browse the forum for automatix if you dont already have it.

-John

---


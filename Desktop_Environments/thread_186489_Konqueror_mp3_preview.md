---
title: "Konqueror mp3 preview"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Tweek84 on 2006-06-02
I can't seem to get the mp3 preview to work in Konqueror.

I can preview .ogg and .wav files

I do have mpg321 installed, and Embedded MPlayer for KDE is at the top of the service preferences order for x-mp3. 

I've searched but can't seem to find any answers other than those. Thanks!

Edit: I am able to play mp3s in amarok or any other media player flavour of the day.

---

### Post by asimon on 2006-06-02
Probably you have 'libxine-extracodecs' already installed (it's in the multiverse repository). For the sound preview KDE uses arts (that old unmaintained sound system which will go away in KDE 4) to play the sounds. But arts itself doesn't know how to play mp3 files. So you need additionally the package 'libarts1-xine', which enables arts to use xine's capabilities. Note that you need both packages.

After installing you need to restart arts for it to have any effect. Thus after logout and login again konqueror should also preview mp3 files.

mpg321 or mpg123 is not needed for sound preview in KDE. AFAIK that is needed for the sound preview in Nautilus, the file manager of GNOME.


PS: Another possibility is to use mpeglib instead of xine. For that you need the package 'libarts1-mpeglib'. But one is enough, either 'libarts1-xine' or ''libarts1-mpeglib'. I recommend to use xine.

---

### Post by tsb on 2006-06-03
Thanks.

someone please add this to the restricted formats wiki!

---

### Post by asimon on 2006-06-07
[QUOTE=tsb]someone please add this to the restricted formats wiki![/QUOTE]
Good idea, I added a sentence to the [RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) page.

---


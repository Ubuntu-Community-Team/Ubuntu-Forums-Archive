---
title: "do i need codecs?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Nikku49 on 2006-07-29
hey im trying to play some video's in totem, but everytime i try to play one of the video's it tells me "Xvid" isnt hadled or something, i had to install codecs in windows to play these videos before, but i cant seem to find any codecs for linux. any suggestions? is there anything like a massive codec pack i can get for linux? like k-lite codec pack mega.

---

### Post by cptnapalm on 2006-07-29
Same situation as with Windows: you need the codecs.  If you download and install Automatix (or EasyUbuntu), when you run it, there will be a checkbox for codecs.  Check it and install it.

---

### Post by vangheem on 2006-07-29
VLC has played everything I've ever thrown at it.

```
sudo apt-get install vlc*
```

That should do it.

---

### Post by PuleX on 2006-07-29
Please read the extensive wiki page on how you can play restricted formats (mp3, xvid, aac (itunes), etc.): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) 
That's where I learned how to enable everything.

---

### Post by bullgr on 2006-07-29
install automatix and select the checkbox for the codecs.
after that if you like to play and decrypt commercial dvd's...

> sudo apt-get install libdvdread3

and after it's installed run the script

> sudo /usr/share/doc/libdvdread3/examples/install-css.sh

and you are done... now you can play everything in totem... :D

---

### Post by Lord Illidan on 2006-07-29
Ironic. I am still trying to see an .avi (music video) in full colour on Windows. Downloaded divx, tried it with WMP, tried it with DivX, nada. black and white.

On linux...worked perfectly in kaffeine, xine, kmplayer...damn windows.

---


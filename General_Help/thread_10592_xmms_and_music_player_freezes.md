---
title: "xmms and music player freezes"
date: 2005-01-09
forum: General Help
---

### Post by ladoga on 2005-01-09
Today i tried to install debians VLC frpm apt-get,it didnt seem to work very well so i removed it. (complete removal) Now trying to play mp3 files causes every audio player i have to freeze. No error messages (not even if i run it from terminal)  nothing just complete freeze so i have to end process.

Any ideas what might have gone wrong?

---

### Post by Ste on 2005-01-09
[QUOTE=ladoga]Today i tried to install debians VLC frpm apt-get,it didnt seem to work very well so i removed it. (complete removal) Now trying to play mp3 files causes every audio player i have to freeze. No error messages (not even if i run it from terminal)  nothing just complete freeze so i have to end process.

Any ideas what might have gone wrong?[/QUOTE]
 Have you tried reinstalling xmms etc. ?

I read here that you shouldn't do a complete removal aswell.

---

### Post by ladoga on 2005-01-09
[QUOTE=Ste]Have you tried reinstalling xmms etc. ?

I read here that you shouldn't do a complete removal aswell.[/QUOTE]
yes i reinstalled XMMS and also compiled it from source without errors. 
Still it freezes, as does everything else that tries to play mp3s.

---

### Post by wallijonn on 2005-01-09
Have you started SPM, selected VLC, checked the "dependencies" tab, looked at all the files listed and seen if any of them are not installed, like, libcdi0, libflac4, libmad0, libmpeg2-4, libvorbis0a, etc. and re-installed them?

Like wise, did you install alsa-base, alsa-utils, esound, esound-common, libcdparanoia0, etc.?

---

### Post by ladoga on 2005-01-10
[QUOTE=wallijonn]Have you started SPM, selected VLC, checked the "dependencies" tab, looked at all the files listed and seen if any of them are not installed, like, libcdi0, libflac4, libmad0, libmpeg2-4, libvorbis0a, etc. and re-installed them?

Like wise, did you install alsa-base, alsa-utils, esound, esound-common, libcdparanoia0, etc.?[/QUOTE]

Thanks for help. Reinstalling gstreamer fixed it all.

---

### Post by vafnord on 2005-01-12
I'm having the same problem with xmms freezing up when I try to play mp3s, except I didn't install/uninstall any multimedia software, or indeed any software at all, between when it was working and when it stopped working.

I like ubuntu but I am about *this* close to going back to gentoo because I cannot get a simple thing like playing mp3s to work consistently.

UPDATE: Rhythmbox will play mp3s but xmms still freezes.

---

### Post by wallijonn on 2005-01-12
Did you install xmms-flac? There's also a xmms plugin for non-standard .mp3s. 

All I can say is that xmms & rhytmbox both play my .mp3s. 

In your case I would just add all the xmms programs listed under SPM.

---


---
title: "getting streaming media to work"
date: 2005-11-28
forum: Desktop Environments
---

### Post by escobar on 2005-11-28
I've been having serious issues getting streaming video to work. Audio is fine though. I've tried a bunch of different methods from setting up mplayer from cvs (which failed horribly) to installing every plugin I can find and still cannot get ANY video stream properly. 

Trying it with mplayer I constantly get the 'bad usage if cpu or ram' when attempting to watch any quicktime or real media clips. Totem just won't stream anything, no errors or anything provided. Gxine seemed to do well but wouldn't work consistently, randomly complained of demuxers and so forth being missing. VLC would strangely get the audio but not the video of most streams. I leave anything out?

 I can't be the only one with this problem. I have w32codecs installed. I have almost every gstreamer plugin known to man installed. I haven't run into anything I couldn't play  locally save .wav files (another story). I just can't stream jack properly. I don't consider myself a linux noob so it all can't be user error. Does anyone know a walkthrough or anything they can point me to that 'just works'?

I don't mean to rant but this is sort of the 'last thing I use Windows for' and it makes me crazy I can't get it working. I've resisted posting this for so long, reading endlessly to get this going. Any and all help would be appreciated. Thanks.

---

### Post by nix4me on 2005-11-28
Your not the only one.  I have mplayer plugin working pretty good but Firefox crashes every 3-4 clips.

nix4me

---

### Post by Dr. Nick on 2005-11-28
My mplayer plugine worked better in epiphany then FF. Have you disabled all the unneeded plugins for streaming in FF, that may be the reason for some of the crashes
Type ```
about:plugins
``` in the menubar and make sure only what you need is their, If you see extras note the filenames and move them out of the directory

---

### Post by escobar on 2005-11-28
[QUOTE=Dr. Nick]My mplayer plugine worked better in epiphany then FF. Have you disabled all the unneeded plugins for streaming in FF, that may be the reason for some of the crashes
Type ```
about:plugins
``` in the menubar and make sure only what you need is their, If you see extras note the filenames and move them out of the directory[/QUOTE]

I don't use the mplayer plugin for firefox. I use the media player connectivity one. Found here:

[https://addons.mozilla.org/quicksearch.php?q=media+player+connectivity&section=A](https://addons.mozilla.org/quicksearch.php?q=media+player+connectivity&section=A)

Bad?

---

### Post by Dr. Nick on 2005-11-28
Well Ive used it before and it was fine. What external program is it launching. For me totem and some others dont seem to take full advantage of the w32codecs. I seem to always have the best luck using mplayer, either mozilla plugin or in media player connectivity , I thin its supported their aswell

---

### Post by escobar on 2005-11-28
[QUOTE=Dr. Nick]Well Ive used it before and it was fine. What external program is it launching. For me totem and some others dont seem to take full advantage of the w32codecs. I seem to always have the best luck using mplayer, either mozilla plugin or in media player connectivity , I thin its supported their aswell[/QUOTE]

Using any of them will fail. Doesn't seem to matter.

---

### Post by Dr. Nick on 2005-11-28
Just Curious, Have you tried the synaptic supplied mplayer-plugin and used the epiphany browser. Not sure if that will solve anything or not, Most streams I use are Windows media so I may have the problem with qt and real and just not know it. I cant test it now either since im on the 64bit ver which lacks the w32codecs

---

### Post by escobar on 2005-11-29
[QUOTE=Dr. Nick]Just Curious, Have you tried the synaptic supplied mplayer-plugin and used the epiphany browser. Not sure if that will solve anything or not, Most streams I use are Windows media so I may have the problem with qt and real and just not know it. I cant test it now either since im on the 64bit ver which lacks the w32codecs[/QUOTE]

Windows media streams fail for me as well. Haven't tried epiphany with the mplayer plugin. Should this work, is there be a way to configure FF to launch streams in Epiphany?

---

### Post by Dr. Nick on 2005-11-29
no way I know to launch the epiphany browser when opening a stream in FF, Ive just seemed to have better luck with epiphany for some reason, cant explain why, Its a shame because I like firefox better for regular browsing because of the extensions. I dont know why FF+mplayer dont go together for me as it seems it should

---


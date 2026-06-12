---
title: "MP3s won't play, and other assorted issues. =("
date: 2005-08-25
forum: Desktop Environments
---

### Post by damienx on 2005-08-25
Hi there, I'm using Ubuntu 5.04 (Hoary) and I've got working sound (startup sounds, GAIM IM sounds, you name it, plenty of sound), but for some reason, in any program (Totem, XMMS, Music Player, you name it) MP3s of no sort will play, in fact, I usually get some kind of error, or in XMMS' case, it'll just freeze once the MP3 has been loaded (and freeze it does, only a kill -9 pid will make it go away).  I'm not entirely sure why they won't go, but no music makes me sad. =(  Anyone able to help me out in this situation?  Also, in XMMS, for when it does actually start playing music, where is the file located where I can place a text file with a preset list in it?  If that wasn't vague enough . . . anyway, I've also been having trouble getting nvidia's latest drivers properly installed on this thing, too . . . having trouble all over the place!  If anyone can help on any or all of these notes, that'd rock.  Thanks!

-Damien

---

### Post by Stormy Eyes on 2005-08-25
Looks there's one of these "How do I play MP3s?" posts every day. [The Ubuntu Guide has the answers you need.](http://ubuntuguide.org/)

---

### Post by damienx on 2005-08-25
I just did everything it said about installing xmms, codecs, blah blah blah, and it still does the exact same thing as far as the mp3's go, no difference whatsoever.  Unless I'm missing something from the guide?

---

### Post by Stormy Eyes on 2005-08-25
[QUOTE=damienx]I just did everything it said about installing xmms, codecs, blah blah blah, and it still does the exact same thing as far as the mp3's go, no difference whatsoever.  Unless I'm missing something from the guide?[/QUOTE]

Did you try playing your MP3s with anything *other* than XMMS? (And why are you using that crappy old winamp knockoff, anyway?)

---

### Post by damienx on 2005-08-25
Well, actually, yes, I did, 'Music Player' that comes default installed into Ubuntu says that it doesn't have the 'right plug-in' to play the MP3 files.  I ripped a CD with Sound Juicer CD Ripper into Vogg-Orbis and Music Player plays them just fine, however, MP3s it still doesn't like.  Interestingly enough, XMMS wouldn't play the vogg-orbis, but Music Player would, so I just removed the XMMS package since it pretty much crashed no matter what I did. =P  I am trying to config/install VLC, since that's like a cureall miracle in XP, but I keep getting a ffmpeg header missing (but it's actually there) error, but then again, when I did a search, a LOT of people seemed to get the same error, with no real way around it that *I* could find, but then again, maybe I just wasn't looking hard enough. =P  But even still, I can't play MP3 files, though I've got packages installed that say that they cover MP3s in Synaptic.  Any further advice is appreciated, thanks.

---

### Post by Mustard on 2005-08-25
[QUOTE=damienx]Well, actually, yes, I did, 'Music Player' that comes default installed into Ubuntu says that it doesn't have the 'right plug-in' to play the MP3 files.  I ripped a CD with Sound Juicer CD Ripper into Vogg-Orbis and Music Player plays them just fine, however, MP3s it still doesn't like.  Interestingly enough, XMMS wouldn't play the vogg-orbis, but Music Player would, so I just removed the XMMS package since it pretty much crashed no matter what I did. =P  I am trying to config/install VLC, since that's like a cureall miracle in XP, but I keep getting a ffmpeg header missing (but it's actually there) error, but then again, when I did a search, a LOT of people seemed to get the same error, with no real way around it that *I* could find, but then again, maybe I just wasn't looking hard enough. =P  But even still, I can't play MP3 files, though I've got packages installed that say that they cover MP3s in Synaptic.  Any further advice is appreciated, thanks.[/QUOTE]
 Installing Totem xine allowed me to listen to MP3s.

---

### Post by damienx on 2005-08-25
Well, Totem is installed by default and I installed the xinelib in Synaptic and again, nothing yet . . . I'm actually really hoping to get VLC in, because it pretty much plays anything you can name in XP . . . I can only hope for something that nice for linux. =P  If it'd ever compile, that is . . . I'm having such hell compiling some stuff sometimes, VLC and Tux Racer are both giving me hell trying to compile, giving me errors and telling me they can't find stuff on ./configure that I know goddamn well are installed (ffmpeg for vlc and tcl for tux), and even when I point the ./configures to the right directory they still give me the same errors.  =(  I guess for now I deal with my one ripped CD? =P

---

### Post by woedend on 2005-08-25
[QUOTE=damienx]Well, Totem is installed by default and I installed the xinelib in Synaptic and again, nothing yet . . . I'm actually really hoping to get VLC in, because it pretty much plays anything you can name in XP . . . I can only hope for something that nice for linux. =P  If it'd ever compile, that is . . . I'm having such hell compiling some stuff sometimes, VLC and Tux Racer are both giving me hell trying to compile, giving me errors and telling me they can't find stuff on ./configure that I know goddamn well are installed (ffmpeg for vlc and tcl for tux), and even when I point the ./configures to the right directory they still give me the same errors.  =(  I guess for now I deal with my one ripped CD? =P[/QUOTE]
 that is a bit strange...the ubuntu XMMS should play MP3 out of the box!  Ill ask you this...does XMMS play your other files fine(wav)?  If so, try downloading Xmms-mad from synaptic.  It's an alternative MP3 input plugin.  As for the compiling...certainly is strange.  Have the build essential and the dev packages for the dependencies its asking for?

---

### Post by nihilocrat on 2005-08-25
I'm in the exact same shoes as the original poster. I was able to get things working for a little bit, though.... I told XMMS to use its ALSA plugin rather than the default OSS and it worked fine for awhile, but then it would play only the first few seconds of an mp3. I installed Alsaplayer and was able to play mp3s with no trouble until very recently... it will seem to be playing them in every respect (including visualization output) but will not actually play the file! The beeps and bloops made by GNOME and other things work fine, though. I've tried installing different sound libs and restarting alsa (/etc/init.d/alsa restart) but to no avail.

---

### Post by damienx on 2005-08-27
Pretty much sorted out all of my issues . . . Other than the occasional 'weird noise' when I'm playing an MP3 in X . . . like weird squeaks/pops/etc, which I've heard of before, I think it's just a config file change, but I don't remember what it is . . . I tried searching for it, but I can't seem to find it.  So, anyone else have that problem?

---


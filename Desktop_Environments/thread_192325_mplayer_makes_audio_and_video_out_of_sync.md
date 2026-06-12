---
title: "mplayer makes audio and video out of sync"
date: 2006-06-08
forum: Desktop Environments
---

### Post by jimmyp on 2006-06-08
When I play a .avi or a .vob in mplayer the audio and video are out of sync.  When I use xine, they are in sync.  I installed mplayer and all the codecs with either easy ubuntu or automatix, I'm not sure which.  Has anyone seen this before or know how I can fix it?

Thanks

---

### Post by c-m on 2006-06-08
I have vlc and xine and they play the majority of my videos fine, but i recently tried playing some hdtv stuff encoded in xvid and its out of sync in every player i've tried in ububtu.

---

### Post by kariopto on 2006-06-08
The easy way to fix it is using the + and - keys on your keyboard.. the delay the audio so you can sinc them..

---

### Post by Anduu on 2006-06-08
In Mplayer go to Preferences>video and make sure Enable Frame Dropping is enabled.

Also try using different video output...I get best performance using xv and gl2

---

### Post by jimmyp on 2006-06-09
Thanks for the suggestions guys.  I am using xv and framedrop already.  As for +/-, that's going after the symptoms of the deeper problem that mplayer plays the videos incorrectly.  I'd rather figure out why mplayer plays the videos out of sync in the first place than figure out how many times I have to hit +/- each time.  Any ideas?

---

### Post by helpdeskdan on 2006-06-10
I was able to fix this problem.  But, you're not going to like my answer.  

The only sure way I know how to fix this is to download Mplayer source code and compile!  I was never able to get the blasted mplayer font to work right, but it was great to have thing in proper sync.   

I wish I could tell you the best instructions on doing this but I forgot.  (I should write this stuff somewhere; every time I have to go find it again)  You'll have to google it.   Good luck!

---

### Post by pvossen on 2006-06-10
Hey Guys,

How did you get Mplayer working with Ubuntu? I couldn't find it in Adept or
Synaptic Package Managers to install. I did install Kmplayer in my KDE
however, it still isn't functioning right. It by far was working the best
when I had Kubuntu Breezy previously.

Because of a problem with downloading Kubuntu upgrade and Grub.
I installed from disk Dapper for Ubuntu and installed all the features of
KDE and Kubuntu separately. All is coming together and I'm enjoying it.
Only the fact that Totem hasn't played near what Mplayer did, and
nothing else seems to work as well as far as video has been disappointing.

If anyone knows an efficient way to install Mplayer with appropriate 
codecs with Dapper 6.06 please let me know.

Pat




[QUOTE=jimmyp]When I play a .avi or a .vob in mplayer the audio and video are out of sync.  When I use xine, they are in sync.  I installed mplayer and all the codecs with either easy ubuntu or automatix, I'm not sure which.  Has anyone seen this before or know how I can fix it?

Thanks[/QUOTE]

---

### Post by jatilq on 2006-06-11
How do you complie or enable mplayer with opengl, I compiled it with the --opengl enable option but I dont see it as an option.

---

### Post by w000t on 2006-06-11
Use OSS audio output and your videos will be in sync! These problems are related to the ALSA implentation in mplayer, but they are fixed in latest CVS/SVN. So if you compile it from source with a fresh checkout, everything will be in sync, even with ALSA.
I submitted a bug about this long ago, but got no reply from the package maintainer.

---

### Post by jimmyp on 2006-06-25
I got an ubuntu package of the new mplayer here:
[http://ubuntu-debs.de/app/mplayer/](http://ubuntu-debs.de/app/mplayer/)

It seems to have fixed the sync problems.  But so does playing it in totem.

---

### Post by Jose Catre-Vandis on 2006-10-22
> **w000t said:**
> Use OSS audio output and your videos will be in sync! These problems are related to the ALSA implentation in mplayer, but they are fixed in latest CVS/SVN. So if you compile it from source with a fresh checkout, everything will be in sync, even with ALSA.
I submitted a bug about this long ago, but got no reply from the package maintainer.


Thanks, it didn't make sense that all the other players were in sync and the big daddy, mplayer wasn't. Selected OSS driver and now working fine.

---


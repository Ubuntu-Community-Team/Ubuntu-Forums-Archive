---
title: "Minor sound problem"
date: 2009-06-14
forum: General Help
---

### Post by lhorace on 2009-06-14
Hi everyone, I'm new here and I want to say a few things before I tell you my problem... I have used ubuntu before but I wasn't to impress, it was harder to make configurations to the OS then Fedora and I have stick to Fedora since. Well,I haven't been using Linux for 4 years now and now I returned. I picked to install Fedora 10 KDE, and guess what, Fedora 10 KDE created more problems then it fix, Kubuntu 9.04 made the whole process such simplier that now I'm officially Kubuntu Fan. 

This problem I'm having is the same problem I had in Windows Vista Home Premium, when it played DVD's or any Video, the sound was low, I fix it by going to the Realtek sound configuration and use the louder Equalization. Well this feature of course is not avialiable in linux. Is there any alternative? Like a sound booster?

---

### Post by entikryst on 2009-06-14
I was having the same problem in ubuntu.  I was getting aggravated that my system was not using my desired sound card for all applications.  I went to the gnome control center clicked the sound icon and that did not help.  I soon discovered the default volume program (gmix) was responsible.  I changed the default device and turned up the master, line in, and PC speakers to the maximum and never had to deal with it again.  You need to find the kde equivalent to gmix and that should solve your problem.

---

### Post by lhorace on 2009-06-14
Thanks, it worked for the video, it sounds great but I ran into a problem.... DVD won't work? I remember in fedora I had to have libdvdcss and libdvdnav? Is still required? I know both of them are on livna repo which is for fedora how about ubuntu/Kubuntu?

---

### Post by Mirge on 2009-06-14
Go to your "Mixer" under volume control, make sure "PCM" is turned up.

---

### Post by lhorace on 2009-06-14
Sorry Merge, I fix the sound problem and tested on the video avi and sound was loud but I can't test it on DVD because neither Jragon Player or Mplayer is playing my DVDS, Mplayer crashes and Jragon just doesn't do anything. I'm trying to find how to get them to work

---

### Post by entikryst on 2009-06-14
NixiePixel will take you through codecs.  She uses Medibuntu to install them.

[http://www.youtube.com/watch?v=NT7urt5UcQg](http://www.youtube.com/watch?v=NT7urt5UcQg)

---

### Post by lhorace on 2009-06-14
entiryst, thanks it help allot but now stumble into another problem, DVD works but I get no sound even from AVI now

---

### Post by lhorace on 2009-06-14
By the way, I get sound from Dragon Player and Amorok but no sound from VLC or Mplayer

---

### Post by lhorace on 2009-06-14
norrow the problem to PulseAudio, it says output devices null? Still googeling

---

### Post by lhorace on 2009-06-14
I would think everyone above for the help, with elbow and grease, I got the sound to work and the volume loud by follow this

[http://kubuntuforums.net/forums/index.php?topic=3103407.0](http://kubuntuforums.net/forums/index.php?topic=3103407.0)

Anyone whos reading this, and visit the link above, you need to scroll down and you will find section about how to get pulseaudio to work. It seems that pulseaudio is now going to be the standard, since there are configution files for alsa to modifiy. Thank u

---


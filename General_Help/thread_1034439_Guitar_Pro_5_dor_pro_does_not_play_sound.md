---
title: "Guitar Pro 5 dor pro does not play sound"
date: 2009-01-08
forum: General Help
---

### Post by sam_thepeach on 2009-01-08
Hi, 

Okay so I installed wine, guitar pro opens the files, but plays no sound. I also installed timidity, but still no sound.

Is there some configuration i missed or something else?

Regards

---

### Post by bryncoles on 2009-01-08
i have a poor solution: abandon guitar-pro and install tux-guitar instead! its basically the same, except that its in the repos, and so you wont need wine. 

its a poor solution because rather than solving your issue - getting guitar pro to play sound - im suggesting using different software. that said, i used to use guitar pro with windows. now i use tuxguitar with ubuntu, and its just as good. also, using guitar pro requires wine, which with timidity is three programs to do the work of one (or two, since tuxguitar needs timidity to work anyway). 

also: you might have to run a command to start timidity. have a look at my second post here, [http://ubuntuforums.org/showthread.php?t=1001563](http://ubuntuforums.org/showthread.php?t=1001563) see if it helps you any with timidity. if it does then yay! if not, im out of ideas, sorry!

---

### Post by Jota37 on 2009-01-13
A little heads up (more detailed in the other thread referred to above):

You might have to install the **tuxguitar-jsa** plugin (Synaptic lists it) and disable both ALSA and OSS output plugins. After that, it started working for me.

Good luck! :-)

---


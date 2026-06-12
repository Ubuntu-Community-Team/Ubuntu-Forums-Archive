---
title: "REalPlayer!"
date: 2006-01-13
forum: General Help
---

### Post by KhanArash on 2006-01-13
I have downloaded and installed realplayer 8.! I would ask you if you knew how I could upgrade it to realplayer 10?

---

### Post by dcstar on 2006-01-13
[QUOTE=KhanArash]I have downloaded and installed realplayer 8.! I would ask you if you knew how I could upgrade it to realplayer 10?[/QUOTE]
There is a Breezy Realplayer 10 deb package at this repository (add the line to the end of your /etc/apt/sources.list file):

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

You can then install "realplay" via Synaptic.

---

### Post by KhanArash on 2006-01-13
[QUOTE=dcstar]There is a Breezy Realplayer 10 deb package at this repository (add the line to the end of your /etc/apt/sources.list file):

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

You can then install "realplay" via Synaptic.[/QUOTE]

Thnx for your reply, but I didnt understand realy what you mean! 
I open /etc/apt/sources.list then I add ? and I couldnt download the deb file from ]http://antesis.freecontrib.org/mirrors/ubuntu/plf/...there were just .gz!?
And I have real 8...can I install the 10 too?!

---

### Post by dcstar on 2006-01-13
[QUOTE=KhanArash]Thnx for your reply, but I didnt understand realy what you mean!
I open /etc/apt/sources.list then I add ? and I couldnt download the deb file from ]http://antesis.freecontrib.org/mirrors/ubuntu/plf/...there were just .gz!?
And I have real 8...can I install the 10 too?![/QUOTE]
There already are a lot of similar lines in that file, add the line specified to the end of the file.

Once it is there **in Synaptic**, remove Version 8 and install the new version.

Don't muck around with manual installs, use the deb packages people provide to make things easier.

---


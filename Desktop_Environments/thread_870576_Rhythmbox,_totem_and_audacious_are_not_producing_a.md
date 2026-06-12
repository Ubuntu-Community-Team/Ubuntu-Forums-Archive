---
title: "Rhythmbox, totem and audacious are not producing any sonund in lxde."
date: 2008-07-26
forum: Desktop Environments
---

### Post by jittopjose on 2008-07-26
hello friends,
i have installed lxde on top on my ubuntu installation. its really cool, usable and fast. less choices means less confusion for a user. i didnt ever feel that its a light weight DE
but some problems are still there. in LXDE  rhythmbox, totem and audacious are not producing any sound. i couldnt find what the reason was. and also pidgin crashed once. anybody have such experience before. plz let me know if anybody know anything about this problems.
thanks
jittos....

---

### Post by jittopjose on 2008-07-26
but i tried vlc, mplayer and atunes. there was no problem with these players. what could be the problem of totem and rhythmbox and audacious.?

---

### Post by PCMan on 2008-07-26
> **jittopjose said:**
> but i tried vlc, mplayer and atunes. there was no problem with these players. what could be the problem of totem and rhythmbox and audacious.?

It might be related to pulse-audio, which is known to cause many problems in ubuntu hardy. Check the audio output options in the preference dialog of rhythmbox to see if alsa works (the default should be pulse audio, which is still experimental and unstable but used by ubuntu LTS). I don't know the solution very well, but I'm sure it's not a lxde problem.

---

### Post by jittopjose on 2008-07-27
thank friend.
i changed sound driver to OSS from pulse audio. now rhythm box worked. at first audacious didnt work. i changed audio driver in audacious preference to OSS. now both worked fine. thank friend.

---


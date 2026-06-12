---
title: "rhythmbox still won't load mp3s after trying guide solution"
date: 2005-02-08
forum: Desktop Environments
---

### Post by desperatecoffee on 2005-02-08
i added the debian testing repository to apt and installed gstreamer-0.8mad or whatever it's called. totem plays mp3s now, but rhythmbox does not. i tried logging out and back in, reinstalling both the rhythmbox and gstreamermad packages, and... nothing happened. any help would be greatly appreciated, thanks.

---

### Post by brainstuff on 2005-02-08
Not really a solution to your problem (more of a Microsoft-style solution) - have you tried XMMS? It's a Winamp clone and you can get it on the Universe repositories. I like it - it works uncannily like Winamp 3.

---

### Post by desperatecoffee on 2005-02-08
yeah, i've used xmms before. it's great, thanks for suggesting it... but i was looking for a music library-style app as well. rhythmbox fits the bill perfectly, or would if it would play mp3s.

---

### Post by macewan on 2005-02-08
When you say it will not play mp3 what do you mean? Are you double clicking the mp3 or trying to import into Rhythmbox an mp3 folder that contains your music?

---

### Post by desperatecoffee on 2005-02-08
holy ko-rapp. i used the automatic update thing and now rhythmbox can randomly play mp3s, even though i looked through the updates and none of them seemed to concern audio. haha...but now my ubuntu splash screen changed to a generic debian one.* guess i shouldn't have added the debian repository to sources.list! ah linux, the wild west of operating systems, in a constant state of (brilliantly) controlled chaos.

*this is not a request for help. i don't really care, i'll reinstall anyway when hoary releases.

---

### Post by Saibei on 2005-02-08
You can probably fix the splash by redirecting the proper symlink in /usr/share/pixmaps/splash

not that you asked for it :wink:

---

### Post by desperatecoffee on 2005-02-09
lol... i really wasn't asking, just noting the humorous irony that my "solution" to the problem (which wasn't even a solution) broke something else. but i'll try that symlink, thanks.

---

### Post by valadil on 2005-02-09
Honestly that's not really an unexpected result of blending your repositories like that.  I'm not quite sure how, but I think some of the files in /etc/apt let you set priorities for your repositories.  You could probably have it only use the debian repo if there were no comprable package in ubuntu.

---


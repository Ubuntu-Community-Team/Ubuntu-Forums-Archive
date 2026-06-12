---
title: "Firefox 1.5 Videoplugins"
date: 2005-12-01
forum: Desktop Environments
---

### Post by ossi on 2005-12-01
Hi there!

I manually installed the new Firefox verision under /usr/local/firefox. So far anything seems to work (much faster besides), but I would like Firefox to use the mplayer Video plugin or anything similar, which worked fine for me with the 1.07 version. The plugin manager of Firefox 1.5 itself does not offer any alternatives to install. There is also no option under preferences to tell firefox which package to use, which would be a great feature and I guess is missing.

So can anybody of you tell me how to get videos running without having to start any external application. 

ps: flash works.

greets

---

### Post by Dr. Nick on 2005-12-01
I know you said you didnt want to use external programs but their is an extension called media player connectivity [here]("https://addons.mozilla.org/extensions/moreinfo.php?id=446&application=firefox") which will automatically open an external program fo you.

Another possible fix, Do you still have FF 1.0.7 installed? It may be possible to copy the mplayer plugins from that install to your new one and have it work. copy /usr/lib/mozilla-firefox/plugins over to the same place on your new install and see what happens

---

### Post by ossi on 2005-12-02
With 1.07 I had the mplayer-plugin installed. But I had a look at your first solution and thats much more better I guess, due to it offers the best compatility and you know, what is happening with the stream. I'll guess I stick to that. Thank you!

---

### Post by hw-tph on 2005-12-02
With the mplayerplug-in deb package, the plugins files are in /usr/lib/mozilla/plugins. Simply cd to the "plugins" sub directory of your own Firefox installation and type **ln -s /usr/lib/mozilla/plugins/* .** to create symbolic links to the actual files. Using your new Firefox, type about:plugins in the address bar - et voila! The plugins should all be listed.


Håkan

---


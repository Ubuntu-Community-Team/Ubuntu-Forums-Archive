---
title: "Metacity Broken After Upgrade to Trusty"
date: 2015-12-22
forum: Desktop Environments
---

### Post by von Corax on 2015-12-22
I've just upgraded from Precise to Trusty, and now Metacity has no top bar, no bottom bar and no keyboard shortcuts. The mouse works, but I keep a clean desktop so there isn't anything there for me to click on. (I'm using Unity to post this, but Unity is IMHO a Fisher-Price-looking piece of crap that won't let me see any of my apps or do any sort of system management.)

Can anyone walk me through the process of getting Metacity working again?

Much thanks,
Darwin

---

### Post by Frogs Hair on 2015-12-22
You are now running a different version of gnome and the fallback session has a different name in 14.04 if I remember correctly. Start with the following. ```
sudo apt-get update
``````
 sudo apt-get install gnome-session-flashback
```

Then restart and select the session you want at login

---

### Post by von Corax on 2015-12-22
That didn't change anything that I could see. Still no menu bar, still no status bar, and still no way out except Ctrl+Alt+F1, then shutdown -r.

---

### Post by Frogs Hair on 2015-12-22
Try the following command from Ask Ubuntu in Unity restart and select your session. ```
cp /usr/share/applications/gnome-panel.desktop ~/.config/autostart/ 
```

---

### Post by von Corax on 2015-12-22
Oh, thank you, that looks *so* much better!

I posted this same question on Ask Ubuntu ([http://askubuntu.com/questions/712474/metacity-tahrballed-after-upgrade](http://askubuntu.com/questions/712474/metacity-tahrballed-after-upgrade)). I'd be grateful if you could either pop over there and explain why this worked, or explain it here and I can post the answer over there.

In any case I'm extremely happy to once again have a system I can actually do work on. Thank you.

---

### Post by Frogs Hair on 2015-12-22
The command was not explained ,but  the cp command copies files to directories in this case the gnome panel to the auto start configuration.

~/ = home .config is in your hidden folder and autostart is a sub folder.

---


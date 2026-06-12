---
title: "Composite Manager Question"
date: 2006-05-20
forum: Desktop Environments
---

### Post by S{yndrom}e on 2006-05-20
Hi recently dled and configured xcompmgr for my gnome desktop. Everything is working smoothly without alot of bugs at all.

One thing i can't figure out though is to how to make the window of a particular program remain permantly semi-transparent. With the transset command i can make a session of terminal semi-transparet, but after i close terminal and restart it it is back to 100% opacity.

I also downloaded gcompmgr, a GUI configurer for xcompmgr, but even with i used gcombgr to set transparency, it reverted back to normal. So what i am aimeing for is that everytime i start a new session of terminal, the window will be semi-transparent. I was just wondering if there was a way to achieve this.

Thank you in advance.

---

### Post by 23meg on 2006-05-20
You're looking for [transset-df]("http://forchheimer.se/transset-df/"). In [this thread]("http://ubuntuforums.org/showthread.php?t=81727") you'll find instructions for launching a transparent terminal with it.

---

### Post by ComplexNumber on 2006-05-20
**S{yndrom}e**
also, if you find that your panel disappears when you first log in to your user account, add the following to your sessions:
'killall gnome-panel'.

---


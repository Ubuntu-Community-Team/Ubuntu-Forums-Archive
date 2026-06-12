---
title: "How do I prevent xchat from autostarting?"
date: 2008-12-18
forum: Desktop Environments
---

### Post by neilmanson on 2008-12-18
Hi All

I set xchat to autostart some while ago on my Gutsy machine, and can't remember how I did it. Now I want to turn it off and can't work out how to.

I have tried System > Preferences > Sessions, but xchat is not listed there.

I have also looked in ~/.config/autostart, but it is not listed there either.

I have searched for xchat in System > Preferences > Gnome Configuration Editor, but with no luck.

Where else might the setting be that autostarts xchat?

Any hints/pointers would be greatly appreciated.

Thanks,
  Neil

---

### Post by Tim Sharitt on 2008-12-18
Look in the ~/.gnome2 folder and see if there is a 'session' file. This is created when a gnome session is saved. You can delete this file, but any other startup programs saved here won't start on the next boot either unless they are in System > Preferences > Sessions.

---

### Post by neilmanson on 2008-12-18
Thanks Tim

That's where it was hiding. I just deleted the entry relating to xchat, and updated the numbers of entries that followed, and now it is working great.

---


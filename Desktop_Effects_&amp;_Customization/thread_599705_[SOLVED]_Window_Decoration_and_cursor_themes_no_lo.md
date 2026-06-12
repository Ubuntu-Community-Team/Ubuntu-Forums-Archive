---
title: "[SOLVED] Window Decoration and cursor themes no longer work with Adept"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by tghe-retford on 2007-11-01
I noticed something happened with Adept tonight when it did some updates, the window decoration and cursor theme in the Adept window have looked to have reset to what looks like the default for KDE. This doesn't happen for anything else except for the Adept Update, Adept Manager and Add/Remove programs window.

It's odd... Have I discovered a bug or has something broken? Reinstalling Adept made no difference. :confused: I don't know how to get it back to normal where my window decoration settings and Comix Cursor theme work with Adept.

I currently have Adept 2.1.3ubuntu17.1 installed.

Thanks in advance.

---

### Post by boeing777 on 2007-11-01
it happened to me once with the Mac theme, are you using emerald theme manager, try to replace the emerald with Windows Decorator, i forgot the command for it but that should work.

---

### Post by boeing777 on 2007-11-01
try to remove emerald and see.

---

### Post by tghe-retford on 2007-11-02
The Emerald package isn't installed. I am using Compiz on Kubuntu 7.10 x86_64. I did go back to the standard KDE Window Decorator (there is a bug where the window decorator function of Compiz crashes now and again so I made a link to that command on the desktop) and it made no difference.

EDIT: I also noticed the same problem using the KDE Control Module for the time and date settings.

---

### Post by tghe-retford on 2007-11-10
I just thought that I would add that since I started the thread, it seems to happen when an application window is running in sudo (kdesudo?).

---

### Post by frodon on 2007-11-19
I think you just need to link your theme, icon and fonts directory for the root user :
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by tghe-retford on 2008-02-14
That worked. Thanks for that (and the belated response).

---


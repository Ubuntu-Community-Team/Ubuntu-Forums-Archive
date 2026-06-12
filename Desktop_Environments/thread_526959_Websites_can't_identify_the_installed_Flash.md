---
title: "Websites can't identify the installed Flash"
date: 2007-08-16
forum: Desktop Environments
---

### Post by mesh2005 on 2007-08-16
I'm using Firefox 2.0.6 on Ubunut 6.06  I installed Flash (9). When I browse websites like myspace.com, I get an error message that Flash is not installed! Please advice.

---

### Post by scxtt on 2007-08-16
how did you install it - via the repos?  what do you get if you type "about:config" into the location bar in firefox?  is Flash listed?

---

### Post by mesh2005 on 2007-08-20
I installed it using the source I downloaded from Adobe. mmm, I can't see it on the about:config page. What should I do?

---

### Post by Triorph on 2007-08-20
from what i remember if you install flash via the built in installer, it copies the required plugin module to your ~/.firefox/ directory, what you want to do is have it in your /usr/lib/firefox/plugins directory, i'm not 100% sure that this will work but try in the terminal

```
cd ~/.firefox
```

```
sudo cp libflashplayer.so /usr/lib/firefox/plugins
```

```
sudo chmod 755 /usr/lib/firefox/plugins/libflashplayer.so
```

---

### Post by scxtt on 2007-08-20
just do: sudo aptitude install flashplugin-nonfree

---


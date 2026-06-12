---
title: "not able to watch videos on firefox"
date: 2009-01-29
forum: General Help
---

### Post by jkid on 2009-01-29
im not being able to watch videos...on firefox...a big gray play singed appears and it stars loading .......and it just stays there...plz help

---

### Post by saranam on 2009-01-29
Have you installed ubuntu restricted extras (from add/remove programs)?  You must search All available Applications.

---

### Post by Therion on 2009-01-29
Open a Terminal.
Copy and Paste the following into it:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by doorknob60 on 2009-01-30
Whatr type of videos? Flash (Youtube, Hulu, etc) or embedded (Windows Media, Real Media, QuickTime, etc)?

---

### Post by jkid on 2009-01-30
embedded and java ....like youtube adn others...

---

### Post by sedawk on 2009-01-30
I think you are missing the required plugins.
In my plugin directory for firefox I have:
```

~/.mozilla/plugins$ ls -ld *
... libflashplayer.so
... libjavaplugin_oji.so -> .../jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Check for instructions to install the required plugins.

---

### Post by jkid on 2009-01-30
dont think thats the problem....the problem would be the plugin i have...

---


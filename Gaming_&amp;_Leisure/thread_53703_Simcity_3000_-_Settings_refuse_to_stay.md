---
title: "Simcity 3000 - Settings refuse to stay"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by Flamekebab on 2005-08-01
Having patched Simcity 3000, messed with the settings and things in accordance with these forums, Simcity 3000 now runs.

BUT, when I change the resolution and try and customise the settings in the options menu (640x480 on a 1280x800 screen seems silly..) I click "Apply" and nothing happens. Further more, no settings will stay.

Otherwise the game works fine, but the resolution is an intense pain.

Any advice?

---

### Post by strikeforce on 2005-08-01
Find the config file and manually edit it or issue the command on startup.  I haven't played simcity but thats generally how I do it with other games.

---

### Post by Flamekebab on 2005-08-05
Nah, I couldn't find the file, if there is one.

Does anyone else have this problem, or know where the config file is?

---

### Post by mike998 on 2005-08-05
Try the following at a command prompt:
```

chown -R user:user /usr/local/games/  
``` 
and
```
chown -R user:user ~/.loki
``` 

Where user is your username

That should then allow you to write to these directories.

You could go a little finer and allow write access to the files and directories, but I personally like the above.  (Caveat : I can be really lazy at times!)

---


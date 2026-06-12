---
title: "Fluxbox &amp; syndaemon"
date: 2008-05-08
forum: Desktop Environments
---

### Post by p_quarles on 2008-05-08
I've been using my laptop a lot more recently, and am having trouble figuring out how to do something that should be fairly simple. I can get syndaemon to work perfectly well if I start it manually, but I simply cannot get it to start up automatically. 

Here is what I've tried so far:
1. Placing the command in the ~/.fluxbox/startup file
2. Placing the command in ~/.xinitrc
3. Creating a separate shell script, and calling that from these files

None of these work. I have tried all of these things both with and without the -d option for syndaemon.

If I type the command into a terminal emulator, however, or use ~/.fluxbox/keys to create a shortcut, it does exactly what it is supposed to do.

Any suggestions will be greatly appreciated.

---

### Post by kerry_s on 2008-05-08
could it be it has to start after X? maybe try putting a little wait on it->

**sleep 10;syndaemon -d &**

adjust the time if needed.

---

### Post by p_quarles on 2008-05-08
Could have sworn that I tried that as well, but I'm not sure. I'll give that a try, and will use add the red-face emoticon if that turns out to work.

---

### Post by spupy on 2008-05-08
I have this in my startup file:
```
killall syndaemon
syndaemon -i 0.3 -k -d
```

Works ok...

---

### Post by p_quarles on 2008-05-08
Yup, adding some sleep time to the startup command did the trick. Thanks.

---

### Post by markjensen on 2008-05-09
Just curious here, but wouldn't the **sleep 10; syndaemon -d &** line in startup cause an overall 10 second delay to the desktop?

(I'm not sure how the ampersand would affect the separate sleep command, would the whole process wait that 10, then execute the syndaemon in parallel?)

---

### Post by kerry_s on 2008-05-09
> **markjensen said:**
> Just curious here, but wouldn't the **sleep 10; syndaemon -d &** line in startup cause an overall 10 second delay to the desktop?

(I'm not sure how the ampersand would affect the separate sleep command, would the whole process wait that 10, then execute the syndaemon in parallel?)

it waits 10 then executes syndaemon.
the "&" tells it not to wait for the command to finish, just start it and move on, it's like backgrounding it.
the ";" treats several commands as 1 execute line.

something like that. :)

---


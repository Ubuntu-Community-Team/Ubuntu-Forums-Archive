---
title: "[SOLVED] no graphical interace - how do you edit a config file in terminal"
date: 2008-12-13
forum: General Help
---

### Post by dharkus on 2008-12-13
i currently have no graphical interface because i changed the xorg.conf file to try and make wow work - can't remember the exact change but i remember it was on these forums and it said u could add 2 lines but someone said it was alright for them if you added just one line which i did!! - how do you edit a config file in terminal as this is all i have - i think this is similar to the recovery mode - just have terminal and any command that needs a graphical interface just says no graphical interface
in case ur wondering how i'm typing this without graphical interface i'm dual booted on my desktop and this happened on my laptop where i just have ubuntu - that also means i can't paste anything from there and would have to type it out if u need me to

---

### Post by kerry_s on 2008-12-13
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by dharkus on 2008-12-13
i'e done this now thanks but how do you save the file and exit it - it says ^X - exit at the bottom but what does this mean -typed this and pressed return and nothing happened

---

### Post by Keith Hedger on 2008-12-13
If your stuck on a command try the man page eg:```
man nano
```
I personally prefer vim its a bit easier than nano

---

### Post by dharkus on 2008-12-13
that doesn't help - doesn't seem to accept commands as i'm editing the file

---

### Post by Keith Hedger on 2008-12-13
just looked at the man page for nano not very helpful at all!
in vim use ```
sudo vim /etc/X11/xorg.confp
```
then press "insert" to start editing, press "esc" to stop editing then press ":" to enter commands type "wq" (write and quit) that should do it (leave out the quotes )

---

### Post by sisco311 on 2008-12-13
> **dharkus said:**
> i'e done this now thanks but how do you save the file and exit it - it says ^X - exit at the bottom but what does this mean -typed this and pressed return and nothing happened

^X = Ctrl+X
You can use Ctrl+o, Enter to save the file and Ctrl+x to exit or
Ctrl+x, y, Enter to save the file and exit.

Or F3 to save the file and F2 to exit.

For more help press Ctrl+g (or F1) in nano.

---

### Post by dharkus on 2008-12-13
jsut one problem with that - i'm in nano and can't get out of it - also i don't need to to anything else with the file now - just save and exit then reboot
edit: wrote this post while the above post wasn't there - sorry for that

---

### Post by dharkus on 2008-12-13
i think it wouldn be a lot more helpful if it said ctrl instead of ^  - then everyone would know what to do

---

### Post by dharkus on 2008-12-13
got it fixed guys - put what i was supposed to be editing it to and that didn't work then i reverted changes by deleting everything i'd put in and then it worked - thanx guys

---

### Post by CatKiller on 2008-12-13
Always make a backup of configuration files before you edit them:

```
sudo cp *config.file* *config.file*.backup
``` Then you can easily restore your backup with ```
sudo cp *config.file*.backup *config.file*
```

^ has been shorthand for Ctrl for decades. I don't think it's going to change any time soon.

---


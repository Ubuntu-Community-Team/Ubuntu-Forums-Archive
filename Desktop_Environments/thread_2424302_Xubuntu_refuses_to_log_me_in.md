---
title: "Xubuntu refuses to log me in"
date: 2019-08-06
forum: Desktop Environments
---

### Post by peyre on 2019-08-06
Very strange.  I fired up my desktop last night, it brought up the login screen, and I input my password.  Then it goes to a black screen with an unblinking cursor in the top left of the screen for about a second and a half, then it takes me back to the login screen.  It *doesn't* say login incorrect, Caps Lock is on, or anything like that.  I've tried inputting my password six times in a row and still find myself at the same login screen.  I shut down for the night and tried again in the morning, but still getting the same thing, it's still being a jackass.  Can anyone tell me what to do about it?

---

### Post by Holger_Gehrke on 2019-08-06
Sounds like a problem with starting the GUI or the Desktop Environment. Try logging in on a virtual terminal (hit Ctrl-Alt and a function key between F1 and F6, type the user name, enter, than the password (is not echoed, not even asterisks)). You should get a shell and be able to check the logs in /var/log/syslog and /var/log/Xorg.0.log.

Holger

---

### Post by #&amp;thj^% on 2019-08-06
Also add this if you would.
```
ls -lah | grep -i Xauthority
```
And;
```
sudo ls -lah /tmp
```

---

### Post by peyre on 2019-08-06
Well!  Sorry for this one guys, looks like this was a real tookie mistake.  It seems I filled my drive with an enormous torrent download.  I seem to be back up and running now after deleting some files.

---

### Post by #&amp;thj^% on 2019-08-06
Good to hear, All's well that ends well. :)

---


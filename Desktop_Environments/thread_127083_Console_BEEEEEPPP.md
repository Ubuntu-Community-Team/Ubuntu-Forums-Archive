---
title: "Console BEEEEEPPP"
date: 2006-02-08
forum: Desktop Environments
---

### Post by anders.ostling on 2006-02-08
Hi

Can somebody please help me to kill the very noisy BEEP that the console uses (on TAB'ed file name completition etc.). I am not referring to sound within an X session, but a plain console.

Anders

---

### Post by frodon on 2006-02-08
Use the right click (or the preference tab) and search in the options, there is one to disable the terminal beep sound.

---

### Post by anders.ostling on 2006-02-08
As I said, it not the X/Gnome setting I am looking for but the console beep. I got an answer from a Dapper user, and the obvious solution was to put

setterm -blength 0  

in the /etc/profile

Anders

---

### Post by az on 2006-02-08
I had success removing (blacklisting) the pcspkr module.

---

### Post by bored2k on 2006-02-08
[http://www.ubuntuforums.org/showthread.php?t=127082](http://www.ubuntuforums.org/showthread.php?t=127082)

---


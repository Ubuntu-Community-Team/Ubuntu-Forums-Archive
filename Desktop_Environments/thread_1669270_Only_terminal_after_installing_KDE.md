---
title: "Only terminal after installing KDE"
date: 2011-01-17
forum: Desktop Environments
---

### Post by Code9 on 2011-01-17
I just installed KDE over my default Gnome installation. Upon rebooting however, there is only a terminal on my desktop and nothing else. Any help is appreciated, thanks.

---

### Post by nomiz on 2011-01-17
got the same thing! #-o

first a clean install of ubuntu, and then a
```
sudo apt-get install kubuntu-desktop
```
where kdm was chosen

any ideas? thx!

---

### Post by nomiz on 2011-01-17
got the same thing! #-o

first a clean install of ubuntu, and then a
```
sudo apt-get install kubuntu-desktop
```
where kdm was chosen

any ideas? thx!

---

### Post by nomiz on 2011-01-17
got the same thing! #-o

first a clean install of ubuntu, and then a
```
sudo apt-get install kubuntu-desktop
```
where kdm was chosen

any ideas? thx!

---

### Post by Code9 on 2011-01-17
Mine was a freshly updated version of Ubuntu, but I installed it the same way you did.

---

### Post by Code9 on 2011-01-17
Mine was a freshly updated version of Ubuntu, but I installed it the same way you did.

---

### Post by Code9 on 2011-01-17
And I keep replying multiple times,

---

### Post by ChuckyDuckster on 2011-01-17
Triple Posting?

Try to run
```
sudo kdm
```
To see if you can start it yourself, or you may be in one of your TTY sessions, in which case try CTRL + ALT + F8

Cheers

---

### Post by Code9 on 2011-01-17
I tried the first one, it doesn't seem to do anything. 
The second one blacks my screen, and I can't seem to do anything

---

### Post by Code9 on 2011-01-17
I tried the first one, it doesn't seem to do anything. 
The second one blacks my screen, and I can't seem to do anything

---

### Post by aysiu on 2011-01-17
Try ```
startx
``` If that doesn't work, try ```
sudo service kdm start
```

---

### Post by aysiu on 2011-01-17
Try ```
startx
``` If that doesn't work, try ```
sudo service kdm start
```

---

### Post by Code9 on 2011-01-17
First one says "Server is already active for display 0"

Second one says "Job is already running: kdm"

---

### Post by aysiu on 2011-01-17
Then do ```
sudo service kdm stop
sudo service gdm stop
sudo service kdm start
```

---

### Post by aysiu on 2011-01-17
Then do ```
sudo service kdm stop
sudo service gdm stop
sudo service kdm start
```

---

### Post by aysiu on 2011-01-17
Then do ```
sudo service kdm stop
sudo service gdm stop
sudo service kdm start
```

---

### Post by Code9 on 2011-01-17
I stopped kdm
I tried to stop gdm, it said " unknown instance"
I restarted kdm and it is still displaying the terminal window.

I also tried startx, and it brought me back to my Gnome desktop

---

### Post by Code9 on 2011-01-17
I managed to get it to show the desktop, I had to select the user session I think. There is a button to select, I changed it from default to KDE. It worked.

---

### Post by nomiz on 2011-01-23
Hej guys! What finally worked for me was:
[LIST]
[*]rename my home folder
[*]recreate my home folder (with the right permissions ;))
[*]restart kdm
[*]move all useful folders from my old home folder to the new one 
[/LIST]
\\:D/

---

### Post by DCdavid on 2011-04-04
> **nomiz said:**
> Hej guys! What finally worked for me was:
[LIST]
[*]rename my home folder
[*]recreate my home folder (with the right permissions ;))
[*]restart kdm
[*]move all useful folders from my old home folder to the new one
[/LIST]
\\:D/


Thank you so much.  I was having this problem until I tried this.  It's a rather odd solution, does anyone know why this works?

---


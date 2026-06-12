---
title: "steam update went back to 13.04"
date: 2013-10-22
forum: Gaming &amp; Leisure
---

### Post by MikeCyber on 2013-10-22
Hi
tried 13.10 but couldn't get nvidia to work and went back to 13.04. Now i had steam installed with games located on another partition. Even after copying the steam stuff from my old home it 
says that I've no games installed. How to point steam to my installed games?
Thanks

---

### Post by MikeCyber on 2013-10-22
Solved:

[email]michael@michael-Ubuntu:~/.local[/email]/share$ ln -s /media/DATA/Steam .

---

### Post by dannyboy79 on 2013-10-24
i don't think that command is even complete. isn't the full command the following? make sure you cd into your ~/.local/share/ folder then issue
```
ln -s /media/DATA/Steam Steam
```

all i did was simply move my ~/.local/share/Steam folder to another partition, then within nautilus I right clicked on the Steam folder and choose the "Make Link" option, then I moved that link back to ~/.local/share/ and made sure it was named Steam versus Link to Steam and WALAAAA, MAGIC.

---

### Post by MikeCyber on 2013-10-24
Sure it's complete don't overlook the . 

obivous that I've moved previously the steam folder to where I have enough hd space.

---

### Post by dannyboy79 on 2013-10-24
ah, i see. many new linux users will not see that . just as I didn't

---


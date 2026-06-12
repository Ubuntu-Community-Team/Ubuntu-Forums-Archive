---
title: "I can't start my GNOME"
date: 2006-02-23
forum: Desktop Environments
---

### Post by imiksu on 2006-02-23
Hi, i installed package called yelp. After that i pressed Ctrl+Alt+Backspace and then anytime when the system try to start gnome or X (whatever it is) it output:

I cannot start the X server (your graphical interface). It is likely that it is not set up correctly...

I can press Yes or No but nothing happens after that.

PLS i need help fast as possible... At last i can use console :S

---

### Post by rudiz on 2006-02-23
sudo dpkg-reconfigure xserver.xorg

---

### Post by imiksu on 2006-02-23
Says that xserver.xorg isn't installed, and when i try sudo apt-get install xserver.xorg it tells that there is no such a package :p

---

### Post by lamego on 2006-02-23
It's xserver**-**xorg

---

### Post by imiksu on 2006-02-23
Then it says that xserver-xorg is allready the newest...

---

### Post by lamego on 2006-02-23
You must be using the wrong command, the correct command is:
```
sudo dpkg-reconfigure xserver-org
```

---

### Post by imiksu on 2006-02-23
Yeah I tried it with sudo... Same thing...

---

### Post by mustang on 2006-02-23
[QUOTE=imiksu]Yeah I tried it with sudo... Same thing...[/QUOTE]

That means you're typing 

sudo apt-get install xserver-xorg

That's not the correct command, this is:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by imiksu on 2006-02-24
I think i tried both commands with sudo, but i'm now installing the whole linux again. I have tried everything i can, and read the forums but nothing works... Thank you anyway for helping..

---

### Post by lamego on 2006-02-24
I am sure you have used the wrong command :evil: .

---


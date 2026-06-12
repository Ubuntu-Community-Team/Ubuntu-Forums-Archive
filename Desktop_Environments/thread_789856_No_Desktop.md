---
title: "No Desktop"
date: 2008-05-10
forum: Desktop Environments
---

### Post by waylow on 2008-05-10
I recently from 7.10 to 8.04 but that seemed to break my system

I was getting an error "failed to initialize Hal"
so I tried to remove it - to reinstall

But now I don't have a desktop and can only log into a terminal


I didn't "completely remove" the packages - how can I get them to reinstall from a terminal

I HAVE NO INTERNET CONNECTION so I need to get the packages from the computer itself

---

### Post by Rocket2DMn on 2008-05-11
You can try downloading the .deb installer from one of the mirrors like packages.ubuntu.com/hardy/hal (which seems to be down right now) and then putting it onto a usb flash drive.  However, I'm not sure what other dependencies might need to be met.
Otherwise, if you have an alternate install CD, you can use that as a repository and install from there.
```
sudo apt-cdrom add
sudo apt-get install hal
```

---

### Post by waylow on 2008-05-11
Thanks Rocket2Dmn but I managed to repair my internet connection and reinstalled it from the terminal

So now I have my Desktop back :)

But I am still having a lot of other issues with 8.04

---


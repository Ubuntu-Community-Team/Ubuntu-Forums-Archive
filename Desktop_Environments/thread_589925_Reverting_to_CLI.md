---
title: "Reverting to CLI"
date: 2007-10-24
forum: Desktop Environments
---

### Post by drezha on 2007-10-24
I'm trying to get my PC to only display command lines most of the time as I'm using it as a webserver and file server but at times I will need the GUI to enable me to use some programs on it.

Now what's the command for shutting down the X server so it's command line only? And can I set this to happen on boot?

Run level's aren't really the answer from googling as they stop it from being multi user and my web based stuff is a different user to who I'll logged in as. Unless I'm mistaken about that?

I've also seen random bits on the web that I can actually send the X output to another PC on my network without the server having X on and using the resources. How do I go about this?

Any help would be great.

---

### Post by Golem XIV on 2007-10-24
Have you considered using the Server Edition of Ubuntu?  I think it's CLI-driven and it already has a LAMP environment set up.

---

### Post by taurus on 2007-10-24
```
sudo /etc/init.d/gdm stop
```
And if you want to start X again, do

```
startx
```

---


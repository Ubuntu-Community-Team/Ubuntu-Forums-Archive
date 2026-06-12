---
title: "Script in /etc/if-up.d doesn't run"
date: 2009-03-08
forum: General Help
---

### Post by Dysport on 2009-03-08
Hi!
I have a little problem: I placed a little bash script in /etc/network/if-up.d
Here is the content:

```
#!/bin/bash
sudo -u webcam sh -c "camorama -M"
```

as you can see all the script should do is starting camorama when the computer is connected to a network. but nothing happens :(
Can someone help me please?

Oh I almost forgot: I placed a script in if-down.d with ```
killall camorama
``` and that script works perfectly

---

### Post by lswb on 2009-03-08
I'm assuming you really meant /etc/network/if-up.d

Scripts in these directories are run as root, remove the sudo from your script. Also of course, make sure you have chmod +x the script.

---

### Post by Dysport on 2009-03-08
Thanks for your reply.
You're absolutely right, that was a stupid typo...
I have already tried a lot of variations:
- without sudo: sh -c "camorama -M"
- without everything: camorama
- ...

I think the problem must be something else. I have another script mounting a sshfs volume with the exact same structure: 
```
sudo -u webcam sh -c  "mount /mountpoint"
```
That script works fine.

Another strange thing: If I run the script from a nautilus  browser as root it works (= it's chmodded as +x)
It's just not working if I enable networking/on boot. I'm starting to go crazy ](*,)

---

### Post by lswb on 2009-03-08
If it fails only at boot it may be because your network has completed it's init before the hardware and drivers for your camera are ready. Try putting the command in /etc/rc.local instead. (Make sure it comes before the line "exit 0" which is the default contents of /etc/rc.local)

---

### Post by Dysport on 2009-03-08
Hi! Thanks again for your reply.
It also fails when I disable networking and enable it again.

Nontheless I wanted to try your solution: it didn't work either! :mad:

I am a little confused now :neutral: why does my machine run a mount script without any problems and refuses to start a program? Do I need to add a prefix or option?? Didn't find anything helpful on the man pages.

---

### Post by heindsight on 2009-03-08
Pardon my ingorance, but I've never used camorama. Is it a GUI app? If it is you probably need the DISPLAY environment variable set (DISPLAY is most probably not usually set for scripts run from if-up.d).

Try something like:
```
#!/bin/sh
DISPLAY=":0"
sudo -u webcam camorama -M

```

By the way, this will probably not work as expected at boot, since the network interface is probably brought up long before the X server is started, so camorama won't be able to start...

---

### Post by Dysport on 2009-03-08
Yes it's a GUI app. I already suspected a problem there. 
Unfortunately the DISPLAY=":0" didn't solve the problem, after disabling-enabling networking there was no camorama popping up.

Okay if boot is the only problem left I can solve this via GUI --> System-Sessions and write a little startup script in my home folder. But it would still be great if I could get it to work simultaneously with the network connection.

---


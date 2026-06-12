---
title: "Compiz/Graphics drivers suddenly stoped working"
date: 2009-02-22
forum: General Help
---

### Post by beattyml1 on 2009-02-22
I recently tried logging in as more than one user at a time and when/after I did, compiz/desktop effects no longer worked

when ever I try turning on desktop effects it goes through the searching for drivers dialog and then comes back and says "could not enable desktop effects" 

when ever I try running:
```
compiz
```
in the terminal the following output is displayed
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

any clue as to what went wrong/how I can fix it

---

### Post by DagMan on 2009-02-23
If logging in as 2 users entails having 2 DISPLAY sessions open, and you're doing it on the machine in you sig with the ATI card, then I remember reading on the ATI site, that the fglrx driver doesn't support compiz on more than one session, so for example if you can switch between the two users you can open a terminal and type  
```
echo $DISPLAY
```
and get :0.0 on one of them, and something else on the other :1.0 for example, then this could be the problem.  I don't know if this applies to other cards and if so which ones, or if it applies to the open source ati driver.  It's a thought though, and it might apply to your situation...

---

### Post by beattyml1 on 2009-02-23
The problem is on my laptop (my desktop has worse problems which will soon be solved by getting a nvidia card), and I'm not so much worried about getting it so that I can switch users on the fly, as I don't really need that at all, I just want to get it back to the way it was so that it will work for a single user

---

### Post by DagMan on 2009-02-23
what's the output of ```
fglrxinfo
```

Have you tried this again?  It's a common thing to overlook.```
sudo aticonfig --initial
```

---

### Post by beattyml1 on 2009-02-26
results of first command:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

also to the second command you suggested gave this output when run:
```
Uninitialised file found, configuring.
Segmentation fault

```

---

### Post by johndoe20081026 on 2009-03-29
I have the same problem on 8.10 w/ Nvidia 180.29 drivers. Everything on my system is up-to-date, and I get the same error message as Beattyml1. Using an Nvidia GeForce 6200. Compiz stopped working a few days ago, I think, but I don't really remember anything video/graphics related being updated in that time.

---

### Post by LoREZ on 2009-03-29
I'm getting precisely the same problem, so I'm following this thread.  Got an older AGP nVidia GeForce 7600GS w/512MB Memory.  I'm thinking a security update we all installed around the same time might be to blame.  I've personally had a rash of those lately, right around the time my Compiz failed.  I wonder if others are having a similar problem?  My output for Compiz initialization is exactly the same as beattyml1

---

### Post by johndoe20081026 on 2009-03-31
Just install KDE4 nightly from the launchpad repos. The compositing on that doesn't work either. Maybe that's because it's a nightly build, but it could also be the same reason Compiz isn't working anymore.

---

### Post by johndoe20081026 on 2009-03-31
Okay, Nvidia users, get ready to be all embarrassed and ashamed.

You need to update your drivers. Yeah, that's it.

i386:
```
http://www.nvidia.com/object/linux_display_ia32_180.44.html
```

AMD64:
```
http://www.nvidia.com/object/linux_display_amd64_180.44.html
```

All I had to do. Now I'm back to smooth sailing.

---

### Post by maxclimber1w on 2009-03-31
I'm having the same problem on a ATI radeon 2400 HD Pro. Strange... any ideas?

```
max@dell-desktop:~$ sudo aticonfig --initial
[sudo] password for max: 
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
max@dell-desktop:~$ 

max@dell-desktop:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
max@dell-desktop:~$ 


```

---


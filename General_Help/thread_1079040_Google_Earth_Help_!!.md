---
title: "Google Earth Help !!"
date: 2009-02-24
forum: General Help
---

### Post by spanky1023 on 2009-02-24
ive tried to follow instructions to a T  but its still not working.

after downloading, and installing, i get this:



Could not create directory:

/root/.googleearth/Cache


[I]
the i click Ok[/I]


Google Earth could not write to the current cache or myplaces file location.  The values will be set as follows:

My Places Path: "/home/spanky/.googleearth"
Cache Path: "/home/spanky/.googleearth/Cache"


*then i click ok, Google Earth opens, and nothing happens.*



any help would be great to this total noob to ubuntu.  and by noob i mean like this is my 2nd day.

---

### Post by spanky1023 on 2009-02-24
no help huh??

---

### Post by roccivic on 2009-02-24
Open terminal (Applications > accessories > terminal) and type:

```
ls -Rla ~/.googleearth/
```

Then paste output here.

Peace

---

### Post by Lunx on 2009-02-24
Sorry that I have no answer to your question, just that it is very timely as I was about to ask same question myself. I tried installing day before yesterday (version 5 beta) and got exactly the same error message, then after clicking ok the splash screen for GE runs then crashes a few seconds later. Thought I was onto a winner this time round, but seems no matter which version of GE I try, I can't get it running (three attempts with three versions and no joy so far). Will watch this thread with interest as it is the only app I've had any bother with getting to run on Ubuntu.

---

### Post by spanky1023 on 2009-02-24
spanky@digby:~$ ls -Rla ~/.googleearth/
/home/spanky/.googleearth/:
total 16
drwx------  4 spanky spanky 4096 2009-02-24 08:48 .
drwxr-xr-x 40 spanky spanky 4096 2009-02-24 08:47 ..
drwx------  4 spanky spanky 4096 2009-02-23 21:00 Cache
lrwxrwxrwx  1 spanky spanky   10 2009-02-24 08:48 instance-running-lock -> /proc/8021
drwx------  9 spanky spanky 4096 2009-02-24 08:48 Temp

/home/spanky/.googleearth/Cache:
total 16
drwx------ 4 spanky spanky 4096 2009-02-23 21:00 .
drwx------ 4 spanky spanky 4096 2009-02-24 08:48 ..
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:00 icons
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:00 models

/home/spanky/.googleearth/Cache/icons:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:00 .
drwx------ 4 spanky spanky 4096 2009-02-23 21:00 ..
-rw------- 1 spanky spanky    0 2009-02-23 21:00 lock

/home/spanky/.googleearth/Cache/models:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:00 .
drwx------ 4 spanky spanky 4096 2009-02-23 21:00 ..
-rw------- 1 spanky spanky    0 2009-02-23 21:00 lock

/home/spanky/.googleearth/Temp:
total 36
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 .
drwx------ 4 spanky spanky 4096 2009-02-24 08:48 ..
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:14 ge6019
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:48 ge6741
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:56 ge6794
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:01 ge7797
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:08 ge7855
drwxr-xr-x 2 spanky spanky 4096 2009-02-24 08:47 ge7997
drwxr-xr-x 2 spanky spanky 4096 2009-02-24 08:48 ge8021

/home/spanky/.googleearth/Temp/ge6019:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:14 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

/home/spanky/.googleearth/Temp/ge6741:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:48 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

/home/spanky/.googleearth/Temp/ge6794:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:56 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

/home/spanky/.googleearth/Temp/ge7797:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:01 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

/home/spanky/.googleearth/Temp/ge7855:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-23 21:08 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

/home/spanky/.googleearth/Temp/ge7997:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-24 08:47 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

/home/spanky/.googleearth/Temp/ge8021:
total 8
drwxr-xr-x 2 spanky spanky 4096 2009-02-24 08:48 .
drwx------ 9 spanky spanky 4096 2009-02-24 08:48 ..

---

### Post by spanky1023 on 2009-02-24
i dont know what any of that means, but hopefully someone can tell me!

---

### Post by spanky1023 on 2009-02-24
ok so i have uninstalled  google earth.  it was installed in root.

then i deleted the /.googleearth  file and all its contents.


now i will try a fresh install of google earth.

---

### Post by spanky1023 on 2009-02-24
ok well that got me no where.  its still doing the exact same thing!!

argh!

please help!

---

### Post by jman82s on 2009-02-28
@ Spanky 1023: after google earth sees that you don't have root privileges, it is falling back on your user directory to store settings and cache. Should be okay there. Does google earth crash on you, or simply hang?

@ Lunx and (possibly) Spanky 1023: this crashing is a known bug in google earth. There is a file called "libcrypto.so.0.9.8" in the google directory path that doesn't work properly. The "fix" is to rename or delete this file. Google Earth will then fall back on your system's own version of this file.

The file should be located in /opt/google-earth.

---

### Post by Lunx on 2009-02-28
> **jman82s said:**
> @ Lunx and (possibly) Spanky 1023: this crashing is a known bug in google earth. There is a file called "libcrypto.so.0.9.8" in the google directory path that doesn't work properly. The "fix" is to rename or delete this file. Google Earth will then fall back on your system's own version of this file.

The file should be located in /opt/google-earth.


Thanks for that, will investigate more shortly

(As an aside, I gave up on new flavours of Google Earth and installed v4.2. I found I can get it running by turning Compiz off... It's not perfect, still buggy and crap fonts, but it works)

---

### Post by jman82s on 2009-03-02
I'm glad you have 4.2 working. 5.0 should work great after renaming libcrypto. Google Earth and VLC, among other video and GL applications, often don't play nice with compiz, which is why I usually leave compiz disabled. Sure is nice to have running, though.:cry:

As for the fonts...the fonts have always looked bad no matter what I seem to do. I really wish Google would fix that.

---


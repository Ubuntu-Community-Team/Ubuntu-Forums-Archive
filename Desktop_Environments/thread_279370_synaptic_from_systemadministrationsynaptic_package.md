---
title: "synaptic from system/administration/synaptic package manager will not start"
date: 2006-10-17
forum: Desktop Environments
---

### Post by cmebert on 2006-10-17
from system, i am prompted for my password, and notification appears in the task bar at the bottom stating: starting administrative application. the notification goes away a second or two later, but synaptic never starts. consequently, i am unable to install updates from the updates available icon when new updates or security fixes are made available.

i am able to run synaptic via sudo successfully, and apt-get works fine, too.

i have dumped the cache in synaptic, reloaded, but am still unable to start the app from system...

---

### Post by astoltz on 2006-10-17
Have you installed Compiz / Beryl / XGL?  There is a known issue with Compiz / Beryl causing this problem.  I can't remember the solution but a quick search should give you the answer.

---

### Post by cmebert on 2006-10-17
i have not installed any of those packages.

---

### Post by astoltz on 2006-10-17
OK.  You could try starting synaptic from the command line and see if it spits out any errors that would give you clue.```
sudo synaptic
```

Edit - Sorry, I misread your first post.  Is it just the update manager that is not working?

---

### Post by cmebert on 2006-10-17
i cannot run synaptic from either system/amdinistration/synaptic package manager or from update manager. i can run it from the command line.

---

### Post by astoltz on 2006-10-18
Hmmm, that's wierd.  The only thing I can think of is that maybe the launcher got screwed up somehow.  Start Alacarte Menu Editor (from the accessories menu) and find the entry for Synaptic.  Right click and pick Properties.  In the command, mine says: ```
gksu /usr/sbin/synaptic
```

---

### Post by cmebert on 2006-10-19
i'll check that when i get home tonight.

---

### Post by b0lha on 2008-06-02
Hi!

I've been having the same problem, Synaptic (as well as other apps) is not starting from system in Hardy 8.04.

apt_get update and upgrade are fine, but I'm not able to perform any updates (update manager also) or changes to my packages from the system, only through the console.

This is kind of weird... the update manager starts and lets me see what updates are to be made, but when I tell him to start it does nothing, not even demand for a pass, it just sits there and thinks.....

This has been going on for a week or two. At first I had to start synaptic or other apps that required a pass so that the system would ask for a password and then the update would start, but now Synaptic won't even start; the same happens with Firestarter, with Applications Sources (I think this is the correct name, I have the Portuguese version).

I have been checking the logs to see whether I can find out what's wrong, but I'm a teacher, not a programmer.... :S

Can anyone help?

Cheers, 

David

PS: If I type "sudo synaptic" in the console, it starts...weird.....firestarter as well....Aiaiaiaiai! :S

PS2: The "apt-get upgrade" I made didn't install one file: libmono-cairo2.0-cil, but then I ran synaptic through the console and achieved in installing it from there.

---

### Post by chris_ac on 2008-06-10
the way i fixed is by
rm -rf /var/cache/apt/archives/lock
sudo apt-get update
sudo apt-get upgrade 
and works just fine.
this will restore the file and allow the installer to work

---


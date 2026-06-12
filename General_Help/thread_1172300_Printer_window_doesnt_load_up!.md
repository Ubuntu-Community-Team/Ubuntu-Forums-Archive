---
title: "Printer window doesnt load up!"
date: 2009-05-28
forum: General Help
---

### Post by HyperNight on 2009-05-28
Hi all,

I were trying to connect to my printer today, but when i goto System - Administrator - Printin
nothing comes up...

Ive been waiting like 20 mins and nothing.

Please, help :P

---

### Post by JohnB-nbr on 2009-05-28
Welcome to the forum HyperNight,

Have you tried to reboot your computer?

---

### Post by HyperNight on 2009-05-28
Hmm... Well no, but this have happend to orther apps too =/ but i can try.

EDIT: Nope didnt work :(

---

### Post by HyperNight on 2009-05-29
Some help???

---

### Post by stereomuffin on 2009-05-29
> **JohnB-nbr said:**
> Welcome to the forum HyperNight,

Have you tried to reboot your computer?

I'm no expert myself but this is lousy advice imho and typical Microsoft mentality ;) 
(no offense, but rebooting on linux is rarely needed)

To the TS: open up a shell and type: sudo /usr/bin/system-config-printer
Does the shell output anything?

What other apps won't open aswell? 
Try opening them from the terminal and see what it outputs..

---

### Post by JohnB-nbr on 2009-05-29
> **stereomuffin said:**
> I'm no expert myself but this is lousy advice imho and typical Microsoft mentality ;) 
(no offense, but rebooting on linux is rarely needed)

To the TS: open up a shell and type: sudo /usr/bin/system-config-printer
Does the shell output anything?

What other apps won't open aswell? 
Try opening them from the terminal and see what it outputs..

Sorry but no matter if you use Linux or Windows, if you face a *sudden *problem (application that won't load, weird graphics, freezing computer,etc.) the first and easiest thing to try is to reboot or logout/login. Trust me, it happens, even on Linux.

And it's true that someone could get almost all the benefits of a real reboot, without rebooting, by typing some commands in a console, but the point is not to save 6.3 seconds.

---

### Post by HyperNight on 2009-05-29
> **stereomuffin said:**
> I'm no expert myself but this is lousy advice imho and typical Microsoft mentality ;) 
(no offense, but rebooting on linux is rarely needed)

To the TS: open up a shell and type: sudo /usr/bin/system-config-printer
Does the shell output anything?

What other apps won't open aswell? 
Try opening them from the terminal and see what it outputs..
The output is following:
```
hypernight@WORKGROUP:~$ sudo /usr/bin/system-config-printer
[sudo] password for hypernight: 
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 30, in <module>
    import dbus
ImportError: No module named dbus
hypernight@WORKGROUP:~$ sudo apt-get install dbus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dbus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hypernight@WORKGROUP:~$ 

```

And yes, i tryied to install the dbus but as u see, its already installed. :(

---

### Post by JohnB-nbr on 2009-05-29
Could you try to install python-dbus?

---


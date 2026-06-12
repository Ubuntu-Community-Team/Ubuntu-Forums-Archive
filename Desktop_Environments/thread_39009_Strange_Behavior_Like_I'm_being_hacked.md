---
title: "Strange Behavior: Like I'm being hacked"
date: 2005-06-03
forum: Desktop Environments
---

### Post by cinematography on 2005-06-03
Okay... This is the second time this has happened now. I'll be sitting here surfing the net, and all of a sudden my mouse will start to move around the screen by itself and open and close some things really fast - too fast for me to see what happened. This last time it opened my system monitor. Does anyone know what could be going on?

---

### Post by royg1234 on 2005-06-03
sounds like you're getting pwned.  Really, though, that is wierd.

---

### Post by byen on 2005-06-03
ok.. for some this might look wierd but to me it kinda hits my issue too.. while typing, my cursor jumps over to the point where the mouse-pointer is present! So the blinking cursor ends up at some random place where my mouse pointer happens to be.... I thought this might have to be with the mouse sttings but no one answered my plight.... Wierd! must be a bug!!!!

---

### Post by nocturn on 2005-06-03
I recommend changing your password immediately.

Check to see if something like VNC or remote desktop is running.
Check out your logs if you see any connections.

That said, there are other possible causes:
Hardware malfunction (what kind of mouse do you use?, my laptop sometimes has this issue with the glidpoint).
Do you have a wireless mouse/keyboard?  If so, maybe your neighbour has the same brand and is interfering with yours.

---

### Post by DarkT on 2005-06-03
Also something really worth doing if you haven't already is set up iptables (think firewall) with something like guarddog.
If you: 
sudo apt-get install gaurddog
then: 
gksudo guarddog (necessary because guarddog will work non-root but wont update settings)

Now you can set up which protocols are allowed. Ones you should probably keep allowed are DNS, HTTP, HTTPS & FTP for normal web browsing. I'm sure somone with better knowledge of iptables etc. can give you better advice but that should suffice for now :)

---

### Post by Hardi on 2005-06-03
Also, a good firewall is FireStarter.
you should be able to install it from Applications>Add/Remove programs. Search for firestarter and install it
from the root terminal, type "firestarter" to run it.

---

### Post by DarkT on 2005-06-03
Thanks for that, I've been looking for something more flexible (but still relatively simple) like that for ages.

---

### Post by jeremy on 2005-06-03
This is probably nothing to do with your problem, but have you tried another mouse? I have a mouse with a wheel, and if the wheel is in the wrong position (between clicks as it were), funny things happen (clock changing time-zone, windows changing focus, etc.).

---

### Post by ianbillmorris on 2005-06-03
You arn't using any kind of KVM are you?  We have similar issues with non-networked test boxes here using KVM Switches.

---

### Post by cinematography on 2005-06-03
[QUOTE=royg1234]sounds like you're getting pwned.  Really, though, that is wierd.[/QUOTE]
lol  :razz: 

[QUOTE=nocturn]I recommend changing your password immediately.

Check to see if something like VNC or remote desktop is running.[/quote]
What are the name of these programs in the system monitor? 

> Check out your logs if you see any connections.
Where can these logs be found? :( 

> That said, there are other possible causes:
Hardware malfunction (what kind of mouse do you use?, my laptop sometimes has this issue with the glidpoint). 
HP optical mouse. 

> Do you have a wireless mouse/keyboard?
No.

[QUOTE=DarkT]Also something really worth doing if you haven't already is set up iptables (think firewall) with something like guarddog.
If you: 
sudo apt-get install gaurddog[/quote]
me@ubuntu:~$ sudo apt-get install gaurddog
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gaurddog

:(

[QUOTE=jeremy]This is probably nothing to do with your problem, but have you tried another mouse?[/quote]
This has only happened twice since I started using Ubuntu. 

[QUOTE=ianbillmorris]You arn't using any kind of KVM are you?[/quote]
I don't know what that is so probably not.

---

### Post by lakcaj on 2005-06-03
guarddog

---

### Post by cinematography on 2005-06-03
There appears to be a conflict between shorewall and guarddog. :( Also, guarddog seems to be for KDE. Maybe it would be best if I used Shorewall?

---

### Post by Ranulf on 2005-06-03
[QUOTE=cinematography]Okay... This is the second time this has happened now. I'll be sitting here surfing the net, and all of a sudden my mouse will start to move around the screen by itself and open and close some things really fast - too fast for me to see what happened. This last time it opened my system monitor. Does anyone know what could be going on?[/QUOTE]

I had this problem with my laptop, turned out to be the battery monitor applet running in the taskbar (gnomebar or whatever its called).  Have removed this as my laptop is always plugged in anyway and the problem went away.

I would have a look at this before you start getting too paranoid about hackers  ;-) .


Ranulf

---

### Post by benplaut on 2005-06-03
[QUOTE=cinematography]There appears to be a conflict between shorewall and guarddog. :( Also, guarddog seems to be for KDE. Maybe it would be best if I used Shorewall?[/QUOTE]

i would go for Firestarter... it's a nice GUI frontend to IPtables  ;-) 

Ranulf: gnome-panel  :)

---


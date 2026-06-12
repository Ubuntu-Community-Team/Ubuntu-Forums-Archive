---
title: "run process remotely, display GUI locally"
date: 2010-01-06
forum: Desktop Environments
---

### Post by boondocks on 2010-01-06
There 2 Ubuntu desktops...
The fast.
The slow.

I have accounts on both systems.

Often I need to use the slow system.
How do I run an application on the fast system and display it on the slow system?

I am not talking about VNC or anything like that.

In other words, How do you run Firefox (process) on fast system,
but display the Firefox GUI on the slow?

---

### Post by gradinaruvasile on 2010-01-06
ssh with X screen export.
Install ssh on both machines.
Open a terminal on the slow machine.
log in to the fast machine with:

ssh -X name@ip
Then you can launch your programs, for example Firefox:

firefox &


But dont expect wonders in case of Firefox, its atrociously slow in exported screens - thats because of its xulrunner virtual machine. Go for Chromium or anything GTK based if you want fast.

---

### Post by boondocks on 2010-01-06
> **gradinaruvasile said:**
> ssh with X screen export.
How can I do this?

> **gradinaruvasile said:**
> Install ssh on both machines.
Already done.  I have ssh access on both system.

> **gradinaruvasile said:**
> But dont expect wonders in case of Firefox, its atrociously slow in exported screens - thats because of its xulrunner virtual machine. Go for Chromium or anything GTK based if you want fast.
Ok. Thanks.

---

### Post by gradinaruvasile on 2010-01-06
> **boondocks said:**
> How can I do this?


By logging in from the terminal to the target machine:

ssh -X user@ip

user is he username, ip is the IP address of the target computer.
when logged in, the programs launched in that terminal will be shown on your machine.

---

### Post by boondocks on 2010-01-06
I understand ssh.

I want to know...
How you do the "**X screen export**" ?

---

### Post by gradinaruvasile on 2010-01-06
The -X switch means X screen export. Meaning that graphical apps launched on the target machine will effectively launch on the source machine.

---

### Post by boondocks on 2010-01-06
Thanks that works.


I see the following in the terminal:
> Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

Do I need to do anything about this?

---

### Post by gradinaruvasile on 2010-01-07
If it works, no.

---


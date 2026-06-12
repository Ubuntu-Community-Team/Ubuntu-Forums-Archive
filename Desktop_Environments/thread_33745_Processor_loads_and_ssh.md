---
title: "Processor loads and ssh"
date: 2005-05-12
forum: Desktop Environments
---

### Post by nicholaspaul on 2005-05-12
This is probably a dumb question, but I have to ask. 

I could probably test this, but I'm not sure how.. anyway, my question is this:
If I login to a Ubuntu machine from another using ssh, and run an application, say OpenOffice. Which machine is Open Office using resources from? Could i be sharing processor power by having multiple machines running different apps remotely , all being controlled from one central machine? Or is the 'host' still using its own resources to run those apps?

---

### Post by mirtux on 2005-05-12
Hi,
   in my experience the full load seem attributed to the machine which effectively runs the program, the one in which OO is running....

Regards,
MC

---

### Post by nicholaspaul on 2005-05-12
So does that follow, then, that i can lighten the load on my main machine (the host) by having one app running on a separate remote machine each? or is that just plain silly!?  \\:D/

---

### Post by mirtux on 2005-05-12
Well, in my case it seems so.... i am connected to three different machines (double PIV) that are using quite often their full power, and my laptop runs quietly at 600MHz.... instead of running uo at 1.8GHz.. ;-)

Regards,
MC

---

### Post by nicholaspaul on 2005-05-12
Interesting :) I'll have to have a play at this, i think. 

Thanks for the help!

---

### Post by mirtux on 2005-05-12
No problem, nice to help... ;-)

Regards,
MC

---

### Post by dewey on 2005-05-12
Remote operations using applications such as SSH and Telnet place all of the load onto the server(comuter running the daemon service), your computer simply displays the output.  Technically speaking, your computer does use resources to display and communicate with the server, but it's very minimal, and I've never noticed a speed hit on my own machine.  x11 applications over an SSH tunnel may run slow, but that has to do with the servers load, and the bandwidth/throughput of the link you're on.

---


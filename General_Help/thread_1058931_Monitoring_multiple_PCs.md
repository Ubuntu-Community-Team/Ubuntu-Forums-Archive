---
title: "Monitoring multiple PCs"
date: 2009-02-03
forum: General Help
---

### Post by Xyem on 2009-02-03
I've been thinking for a while about attaching a monitor to my server and having various things displayed on the monitor which would be in a "public" location such as the hallway.

I was thinking about having such things as the weather, live feeds from web(security) camera, date/time etc. etc.

It would also be interesting if I could graph various things about all the PCs attached to the network ( overall/individual CPU usage, RAM usage, network activity ). Does anyone know of a package that will allow me to collate this information from various PCs onto the server and therefore graph it?
It'd also be nice if it was cross-platform so it also displayed statistics when the few multi-boot computers are in Windows but that isn't too much of an issue ( out of 7 computers, 3 multi-boot and only 1 is Windows-only ).

If one doesn't already exist, I may be able to create one in Perl. Would others be interested?

Thanks

---

### Post by RedeyeAce on 2009-02-03
This is actually quite a nice idea, I would use something like this, be handy to see which pc's are hogging network resources etc. especially if it does work cross platform.

---

### Post by chiefbutz on 2009-02-03
I have not heard of anything like that, and it is something that could possibly be programmed, though it would take some effort. Showing the system stats is something that is easier. If you just want to be able to see memory usage and CPU usage and the processes running you might want to look at htop. It runs in the terminal but is very nice.

---

### Post by Xyem on 2009-02-04
htop looks nice but I'm not looking for a monitor of a single machine.

I've just finished a little side project so I can look into this from a "roll my own" point of view. Already put some thought into it ( structure-wise ) so I have some plans, I've even got a couple of name possibilities!

If you'd like to help me test it, make suggestions ( or help develop if you know Perl and are willing to deal with me :P ), you're more than welcome, just let me know :)

---

### Post by Xyem on 2009-04-12
Just came across this while looking for something else. Might be of interest. I'll have to try it out at some point.

[http://munin.projects.linpro.no/](http://munin.projects.linpro.no/)

---

### Post by Chris Musampa on 2009-04-12
I use GKrellm, I believe it can monitor other machines though I've never attempted that with it.

---


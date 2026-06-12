---
title: "Restarts after shutdown"
date: 2009-02-23
forum: General Help
---

### Post by shaker108 on 2009-02-23
I have been running 8.04 on one of my old computers for a long while (and I always install updates) without any problems until now.

It started a few days ago ... every time I shut down it restarts after a few seconds and its getting annoying. Anyone know what it might be?

---

### Post by thomasaaron on 2009-02-23
Are you actually shutting it down, or are you using suspend or hibernate. If you're using suspend or hibernate?

---

### Post by skintythe1andonly on 2009-02-23
check to see if an error comes up when you shutdown from the terminal

```

sudo shutdown -h now

```

change -h to -r to restart

---

### Post by shaker108 on 2009-02-24
I use the red shutdown button and it has been shutting down like it should for at least 6 months. I get no errors when I do "sudo shutdown -h now"

---

### Post by jwdvd on 2009-02-24
what do you get if you do an "init 0"

---

### Post by shaker108 on 2009-02-24
It shuts down with some error "libhal shudown failed - connection closed" + some more network manager related errors and then it restarts after maybe 30 seconds.

---


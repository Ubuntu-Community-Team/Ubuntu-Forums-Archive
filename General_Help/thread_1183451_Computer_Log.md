---
title: "Computer Log"
date: 2009-06-10
forum: General Help
---

### Post by supertails on 2009-06-10
Does Ubuntu have a log that keeps track of all activity?

---

### Post by Lampi on 2009-06-10
/var/log/syslog tracks most of activity - just have a look what else you find in /var/log/

---

### Post by supertails on 2009-06-10
Is there a easy way I can find a date and time?

---

### Post by Lampi on 2009-06-10
sure - just look at some of the files in /var/log - every line starts with date+time stamps

Older files are packed in gzip archives, this happens on a regular base. You can still look at them in nautilus.

---

### Post by supertails on 2009-06-10
Has someone tried to hack into my computer cause I see on June 4 that something failed to happen 518 times. 1 or 2 or 5 seems ok but 518. Makes me wonder if it's some evil machine at work.

---

### Post by colau on 2009-06-10
> **supertails said:**
> Has someone tried to hack into my computer cause I see on June 4 that something failed to happen 518 times. 1 or 2 or 5 seems ok but 518. Makes me wonder if it's some evil machine at work.
What was that failed 518 times?
You can also use
System>Administrator>Log File Viewer

---

### Post by supertails on 2009-06-10
Jun  4 20:57:40 tails-laptop pulseaudio[5075]: protocol-native.c: Failed to push data into queue
Jun  4 20:57:42 tails-laptop last message repeated 12152 times
Jun  4 20:57:42 tails-laptop pulseaudio[5075]protocol-native.c: Failed to push data into queue
Jun  4 20:57:42 tails-laptop pulseaudio[5075]: protocol-native.c: Failed to push data into queue
Jun  4 20:57:46 tails-laptop last message repeated 32289 times

Jun  4 20:57:40 tails-laptop pulseaudio[5075]: protocol-native.c: Failed to push data into queue
Jun  4 20:57:40 tails-laptop last message repeated 586 times
Jun  4 20:57:40 tails-laptop pulseaudio[5075]: asyncq.c: q overrun, queuing locally
Jun  4 20:57:40 tails-laptop last message repeated 112 times
Jun  4 20:57:40 tails-laptop pulseaudio[5075]: protocol-native.c: Failed to push data into queue
Jun  4 20:57:40 tails-laptop last message repeated 128 times
Jun  4 20:57:40 tails-laptop pulseaudio[5075]: asyncq.c: q overrun, queuing locally
Jun  4 20:57:40 tails-laptop last message repeated 107 times
Jun  4 20:57:40 tails-laptop pulseaudio[5075]: protocol-native.c: Failed to push data into queue
Jun  4 20:57:40 tails-laptop last message repeated 912 times
Jun  4 20:57:40 tails-laptop pulseaudio[5075]: asyncq.c: q overrun, queuing locally

---


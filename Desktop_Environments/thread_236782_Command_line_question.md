---
title: "Command line question"
date: 2006-08-15
forum: Desktop Environments
---

### Post by jude999 on 2006-08-15
Hi friends,

I am looking for a command line that would launch 2 programs but 2 second one 10 seconds after the 1st one. Is this possible? what would the line look like?

---

### Post by Ramses de Norre on 2006-08-15
I don't really get your question (strange sentence) but if I'm right you want a command to start one command and then a second one ten seconds later?
That would look like this: ```
command1 && sleep 10 && command2
```

---

### Post by jude999 on 2006-08-15
hehe thanks, that should do it!

it is for sopcast. I'm trying to create a laucher that will lauch the script to get the channel (that take a little less than 10 seconds) and then launch mplayer to view the channel in 1 click instead of 2 now.

On my way to try!

---

### Post by jude999 on 2006-08-15
Got it, playing around with your suggestion, I found out that the line shouls looks like this:
```
command1 sleep 10 && command2
```

Thanks for your help!

---

### Post by Ramses de Norre on 2006-08-15
?? There really should be "&&" or ";" in between two commands.. You now have "sleep 10" as argument for your first command..

---

### Post by jude999 on 2006-08-15
Well it does work like this :S ... I'm not completely familiar with the command line yet...

---

### Post by Ramses de Norre on 2006-08-15
Very strange.. but use it if it works.

---

### Post by coffinsupply on 2008-01-09
Hi,
What command is used in SSH to shutdown sopcast?

---


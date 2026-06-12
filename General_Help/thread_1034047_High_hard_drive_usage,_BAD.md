---
title: "High hard drive usage, BAD?"
date: 2009-01-07
forum: General Help
---

### Post by linuxisevolution on 2009-01-07
I am running a Linux server with apache+mysql+ssh+php+css. It works fairly well. It is a Pentium 3 550mhz 256mb ram and serves the websites in my sig. I checked munin, and it reported this:

[http://71.206.223.52/munin/localdomain/localhost.localdomain-df-week.png]("http://71.206.223.52/munin/localdomain/localhost.localdomain-df-week.png")


The graph shows 100% hard drive usage. If you go [here]("http://71.206.223.52/munin/localdomain/localhost.localdomain.html#Disk") you can see further statistics. Any thoughts?

---

### Post by mssever on 2009-01-07
> **linuxisevolution said:**
> I am running a Linux server with apache+mysql+ssh+php+css. It works fairly well. It is a Pentium 3 550mhz 256mb ram and serves the websites in my sig. I checked munin, and it reported this:

[http://71.206.223.52/munin/localdomain/localhost.localdomain-df-week.png](http://71.206.223.52/munin/localdomain/localhost.localdomain-df-week.png)


The graph shows 100% hard drive usage. If you go [here]("http://71.206.223.52/munin/localdomain/localhost.localdomain.html#Disk") you can see further statistics. Any thoughts?
It appears that your root partition is full. Check the output of df to confirm. You should investigate why it's full and take appropriate action to bring free space to at least 15-20%. baobab is a great tool for finding where all your disk space has gone.

---

### Post by linuxisevolution on 2009-01-07
Thanks! It appears 99% of it is used. about 200mb left. Thanks, I was thinking of usage as in access not in amount. :)

---


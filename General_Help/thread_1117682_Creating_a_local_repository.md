---
title: "Creating a local repository"
date: 2009-04-06
forum: General Help
---

### Post by JFASI on 2009-04-06
I am running a lab, and I've been instructed to create a local repository which I can use to keep all our computers up to date at the same time. They are all connected to the internet, as well as a central server. How can I go about this?

---

### Post by kryptikos on 2009-04-06
This might help you out. It's a pretty good write up / HOWTO with apt-mirror:

[http://www.arsgeek.com/2007/02/14/how-to-set-up-your-own-local-repositories-with-apt-mirror/]("http://www.arsgeek.com/2007/02/14/how-to-set-up-your-own-local-repositories-with-apt-mirror/")

---

### Post by JFASI on 2009-04-06
Well, I was thinking of making a local repository containing all the packages I want installed on each computer in the lab, so that I can have them use that as their only repo, and just update themselves with a cron job. If I place something new in that repository, they will install it when the cron job runs, and if I remove something, they will uninstall it. 

Is this the best way of doing it? I just want to have a way of making all my computers standardized.

---

### Post by kryptikos on 2009-04-07
There isn't anything wrong with the way you are setting it up. Since it is a lab type environment that is the best way to isolate the repository anyways. You can create the repository from the HOWTO but only load on the software you want to have available to the boxes.

---


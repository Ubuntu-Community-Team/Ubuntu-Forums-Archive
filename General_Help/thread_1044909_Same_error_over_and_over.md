---
title: "Same error over and over"
date: 2009-01-19
forum: General Help
---

### Post by Taz. on 2009-01-19
On every command i try in the terminal i get this:

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by oldos2er on 2009-01-19
Do you have Synaptic Package Manager or Add/Remove open? And what commands are you trying to run?

---

### Post by Taz. on 2009-01-19
When open the sypnatic thingy it said the following:

Another synaptic is running

There is another synaptic running in non-interactive mode. Please wait for it to finish first.

---

### Post by oldos2er on 2009-01-19
You can only have one package manager working at a time.

---

### Post by ronelc on 2009-01-19
I think rebooting your system can solve your problem.

---

### Post by iaculallad on 2009-01-19
> **ronelc said:**
> I think rebooting your system can solve your problem.

Not at all, you could just kill the process as another apt-get/dpkg process could be running.

To view running process, issue the command below on your terminal:

```
ps aux | grep apt
```

And use whatever process ID your apt is using and kill it:

```
sudo kill -9 Process_ID
```

As rebooting a system could be so windoooooozzzzeeee :-)

HTH.

---

### Post by Taz. on 2009-01-20
restarting the pc worked. Thanks guys.

---

### Post by snova on 2009-01-20
> **Taz. said:**
> restarting the pc worked. Thanks guys.

Next time (if you are *certain* there are no other package management programs running), you could also simply remove the **/var/lib/dpkg/lock** file.

```
sudo rm /var/lib/dpkg/lock
```

---


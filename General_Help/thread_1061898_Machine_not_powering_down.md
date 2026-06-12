---
title: "Machine not powering down"
date: 2009-02-06
forum: General Help
---

### Post by kooldino on 2009-02-06
I just got a new Dell Optiplex 360.  When I reboot or shutdown the machine, it will just sit there once the "unloading" screen completes.  How can I fix this?

---

### Post by kooldino on 2009-02-13
bump

---

### Post by kooldino on 2009-02-17
Found something interesting...the machine WILL power down if I log out first.

---

### Post by caleb12 on 2009-02-17
I don't want you to feel all left alone, so I thought I would toss in my two cents... I have a similar issue on my HPzd8000. It will sometimes stall completely, freeze and be near unrecoverable... 

And the other sympton, it doesn't fully power down. It will get all way down to the end, and sit there with:

acpid: exiting  - and a flashing cursor. 

This is a completely random event for me though, I haven't been able to narrow down what exactly is causing it. I've gotten closer and it's looking to be something with my video card (ATI), in earlier kernel versions it was causing an ECP Storm which was fixed in 2.6.26 or there abouts. Notably, the ECP storm is apparently a function of the ACPI calls that the ATI card makes during initialization.

Most recently, I installed the FGLRX drivers and used aticonfig --acpi=off and I haven't seen problems since... This has really only been a few weeks, so not a true test and since the problem is not reproduce-able on my end... only time will tell. 

Hopefully, that helps... and is not completely unrelated to your situation...

---

### Post by kooldino on 2009-02-17
> **kooldino said:**
> Found something interesting...the machine WILL power down if I log out first.

...but not always.

*sigh*

---

### Post by cubeist on 2009-02-17
One place to start when something doesn't work is to check the logs (system:administration:system log).  So note the time, try to shutdown...it will fail, then reboot and check the logs from the time you shut down, and then post the relevant results here (errors, segfaults, etc)...

without some data as to what might be causing the problem one guess is to re-configure usplash... try this... (just type this in a terminal)... it may or may not work...

```
sudo dpkg-reconfigure usplash
```

---

### Post by Psyphre on 2009-02-17
Are you sure its not shutting down? I know this may soudn silly but it may just be taking a really long time.

Ever since I installed intrepid on my laptop it takes 5-10 minutes just to shut down. Its excessively long i know and taking that long to shut down is almost as bad as not shutting down at all. But its still worth knowing if that is the case or not.

---

### Post by kooldino on 2009-02-19
> **cubeist said:**
> One place to start when something doesn't work is to check the logs (system:administration:system log).  So note the time, try to shutdown...it will fail, then reboot and check the logs from the time you shut down, and then post the relevant results here (errors, segfaults, etc)...

without some data as to what might be causing the problem one guess is to re-configure usplash... try this... (just type this in a terminal)... it may or may not work...

```
sudo dpkg-reconfigure usplash
```

I'll give that a whirl, thanks.

---

### Post by kooldino on 2009-02-19
> **Psyphre said:**
> Are you sure its not shutting down? I know this may soudn silly but it may just be taking a really long time.

Ever since I installed intrepid on my laptop it takes 5-10 minutes just to shut down. Its excessively long i know and taking that long to shut down is almost as bad as not shutting down at all. But its still worth knowing if that is the case or not.

Well, let's just say it doesn't shut down in 30 mins time.

---


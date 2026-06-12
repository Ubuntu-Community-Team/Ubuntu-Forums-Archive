---
title: "Kdenlive starts up then closes"
date: 2009-02-15
forum: General Help
---

### Post by Lingonet on 2009-02-15
Hello!

I have a little problem with the video editing software Kdenlive. I just installed it and when I try to start it I see the windows but a half second later it closes. I tried to run it in terminal but then both Kdenlive and the terminal closes. What could be the problem here?


Thank you!

---

### Post by johnjohn2 on 2009-02-15
Try reinstalling the software and c if that solves the issue

---

### Post by Lingonet on 2009-02-16
Didn't work. Still the same.

---

### Post by Lingonet on 2009-02-18
Nothing works. What am I going to do?

---

### Post by snova on 2009-02-18
Run it from a terminal (Applications -> Accessories -> Terminal) and post any output.

```
kdenlive
```

---

### Post by Lingonet on 2009-02-19
root@Femmansbuntu:~# kdenlive
kbuildsycoca running...
Error: "/var/tmp/kdecache-henrik" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/var/tmp/kdecache-henrik" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-henrik" is owned by uid 1000 instead of uid 0.
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
root@Femmansbuntu:~#

---

### Post by Lingonet on 2009-02-19
What does this mean?

---

### Post by snova on 2009-02-19
> **Lingonet said:**
> **root**@Femmansbuntu:~# kdenlive
kbuildsycoca running...
Error: "/var/tmp/kdecache-henrik" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/var/tmp/kdecache-henrik" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-henrik" is owned by uid 1000 instead of uid 0.
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
root@Femmansbuntu:~#

I would guess it's because you're running it as root. Is this necessary?

If you *have* to run it as root, maybe kdesudo would work (I think this is what it's for, actually):

```
kdesudo kdenlive
```

(Note that gksu is equivalent here)

---

### Post by Lingonet on 2009-02-20
```
henrik@Femmansbuntu:~$ kdesudo kdenlive

kbuildsycoca running...
Reusing existing ksycoca
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
Unable to start Dr. Konqi
henrik@Femmansbuntu:~$ 
```

Didn't work, as you can see.

---

### Post by Lingonet on 2009-02-20
What the heck is wrong? Can anyone solve this?

---

### Post by Lingonet on 2009-02-21
Can someone take a look at the output?

---

### Post by RockClimb on 2009-02-23
> **Lingonet said:**
> What the heck is wrong? Can anyone solve this?


I have the same problem with BibleTime. A friend of mine found a way to get it running and asked me to post the details. 
It may may work for Kdenlive also. If nothing else, it should help the developers track down the problem.

Open an xterm, run "su" (No Dash) then enter the password. Then run the program from the same terminal.

When running the program as a regular user or with sudo, I get the drkonqi error message. Running "su -" and then the program gives "cannot connect to X server," as it should.

---

### Post by Lingonet on 2009-03-08
> **RockClimb said:**
> I have the same problem with BibleTime. A friend of mine found a way to get it running and asked me to post the details. 
It may may work for Kdenlive also. If nothing else, it should help the developers track down the problem.

Open an xterm, run "su" (No Dash) then enter the password. Then run the program from the same terminal.

When running the program as a regular user or with sudo, I get the drkonqi error message. Running "su -" and then the program gives "cannot connect to X server," as it should.

```
henrik@Femmansbuntu:~$ sudo bash
[sudo] password for henrik: 
root@Femmansbuntu:~# su
root@Femmansbuntu:/home/henrik# kdenlive
kbuildsycoca running...
Reusing existing ksycoca
KCrash: Application 'kdenlive' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
root@Femmansbuntu:/home/henrik#
```

Just like you said: "Could not find drkonqi".

How do I solve this now?

---

### Post by Lingonet on 2009-03-14
I still haven't figured it out. How do I solve this? I need some help!

Thank you!

---

### Post by Lingonet on 2009-03-15
Still no progress. What to do?

---

### Post by RockClimb on 2009-04-27
I don't know if this will fix Kdenlive or not, but I have fixed BibleTime.

I upgraded to 9.04 but still had the same problems and a few new ones. I fixed them by removing their config settings in my home directory. for BibleTime it is the .sword directory. I installed kdenlive and it runs fine. I did not have it installed on 8.04 so I cannot verify that removing its rc file would fix it.

---

### Post by freackout on 2009-07-15
> **Lingonet said:**
> What the heck is wrong? Can anyone solve this?

try builder script for kdenlive ffmpeg and mlt together
available here from kdenlive.org.

[http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard](http://www.kdenlive.org/user-manual/downloading-and-installing-kdenlive/builder-wizard)

./bash kdenlive_builder.sh (runs the script)

---


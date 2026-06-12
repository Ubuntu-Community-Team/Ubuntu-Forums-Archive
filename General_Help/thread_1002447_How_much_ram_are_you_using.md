---
title: "How much ram are you using?"
date: 2008-12-05
forum: General Help
---

### Post by Roasted on 2008-12-05
I just have to ask... I booted this computer up yesterday and it was using 500mb ish on a fresh boot.

I haven't shut the computer off, and after running several programs and whatnot, I closed them all and checked my ram usage.

I'm using 950mb with pidgin open and that's it. Other than that, all programs are closed.

Note - the 950mb was not with a fresh boot. I turned the computer on yesterday however after a day time my ram usage doubles? What?

---

### Post by sdennie on 2008-12-05
What is the output of:

```

free -m

```

My guess is that most of your RAM "usage" is actually cache which can't really be considered "used" RAM and is actually very beneficial to system performance.

---

### Post by Roasted on 2008-12-05
jason@jason-intrepid:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3960       2972        988          0        303       1629
-/+ buffers/cache:       1038       2921
Swap:          996          2        993
jason@jason-intrepid:~$ 

Does that go along with what you said?

---

### Post by mkvnmtr on 2008-12-05
Right now I am using 290MB. I have three browers open and one game. I have never seen it over about 350 MB although I am sure it has probably gone there. Top or HTop should tell you what is using memory.

---

### Post by Roasted on 2008-12-05
Are you running 8.10?

I have 8.10 installed on a computer with 256mb... The first few minutes I'm logged in it's okay... but as I do more things, it slows down drastically... coinciding with what was said earlier about the memory getting cached. Maybe with 256 being a limit (plus it's 100mhz ram) it just bogs up too much?

---

### Post by kerry_s on 2008-12-05
> **Roasted said:**
> Are you running 8.10?

I have 8.10 installed on a computer with 256mb... The first few minutes I'm logged in it's okay... but as I do more things, it slows down drastically... coinciding with what was said earlier about the memory getting cached. Maybe with 256 being a limit (plus it's 100mhz ram) it just bogs up too much?

debian custom on 450mhz 256mb ram. i have pandora.com playing.

---

### Post by OrangeCrate on 2008-12-05
> **Roasted said:**
> I just have to ask... I booted this computer up yesterday and it was using 500mb ish on a fresh boot.

I haven't shut the computer off, and after running several programs and whatnot, I closed them all and checked my ram usage.

I'm using 950mb with pidgin open and that's it. Other than that, all programs are closed.

Note - the 950mb was not with a fresh boot. I turned the computer on yesterday however after a day time my ram usage doubles? What?

**Linux Memory Management or 'Why is there no free RAM?'**

> Traditional Unix tools like 'top' often report a surprisingly small amount of free memory after a system has been running for a while. For instance, after about 3 hours of uptime, the machine I'm writing this on reports under 60 MB of free memory, even though I have 512 MB of RAM on the system. Where does it all go?

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---


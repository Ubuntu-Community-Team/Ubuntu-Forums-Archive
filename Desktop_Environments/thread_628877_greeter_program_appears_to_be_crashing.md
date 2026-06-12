---
title: "greeter program appears to be crashing"
date: 2007-12-01
forum: Desktop Environments
---

### Post by Findarato on 2007-12-01
Hello everyone,
I am having quite a big problem with my greeter atm. I installed a new login theme using a theme found with "Art manager" and I get the error : "the greeter program appears to be crashing: attempting to use a different one" (or something like it, my ubuntu is in french). I tryed reconfiguring xserver, didn't work. Tryed gdmsetup, tells me : gtk warning: cannot open display

I am lost here and my ubuntu won't work :( Please, someone help me with this one

---

### Post by Findarato on 2007-12-01
this is really urgent, I can't do anything with my system right now...

---

### Post by Findarato on 2007-12-01
I need help with this, It can't be I have to re-install my whole system and loose all I have on it...

---

### Post by Findarato on 2007-12-01
I am using this environement professionally, really considering if i should not switch back to windows for stability. Ubuntu is giving me lots of crap... :(

---

### Post by jr.gotti on 2007-12-01
hmm....that's odd. hit ctrl+alt+f1 and login...now type "sudo apt-get remove gdm" and then once thats done do "sudo apt-get install gdm"

if that doesn't work, try removing gdm as listed above, and installing kdm until you can figure out whats going on.

alternatively, hit ctrl+at+f1, login, and then type in startx to skip the greeter.

---

### Post by Findarato on 2007-12-02
I tried removing-installing gdm,but then it tells me changes only take effect once x services are restarted. I restarted my comp, still get the same error. When I type startx, it tells me "fatal error: server is already active for display 0 ... Xlib: connection to ":0.0" refused by server, no protocol selected ... giving up ..."

---

### Post by Findarato on 2007-12-02
installing kgm worked, I still would like a solution to my first problem though, keeping gdm.

---


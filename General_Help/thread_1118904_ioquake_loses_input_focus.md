---
title: "ioquake loses input focus?"
date: 2009-04-07
forum: General Help
---

### Post by akos.maroy on 2009-04-07
I'm having a problem that when playing ioquake on ubutnu 8.10, regularly, the ioquake app (running full screen) all of a sudden turns windowed, and loses the input focus at the same time. actually, nothing gets any keyboard or mouse events afterwards.

the only way to solve the issue is to either kill X (CTRL-ALT-Backspace), or log in via a console, and kill the ioquake process.

I'm gessing that some event notification causes this issue? but I can't find out what..

does anyone else have the same problem?

---

### Post by schmidtbag on 2009-04-07
I've never played this, but check the manual page of it in terminal, and see if you can run it under windowed from terminal.  If you can, try that but make sure terminal is in clear view.  This way you can check if anything is wrong when it causes X to freeze, and, maybe theres just some visual glitch

---

### Post by akos.maroy on 2009-04-08
> **schmidtbag said:**
> I've never played this, but check the manual page of it in terminal, and see if you can run it under windowed from terminal.  If you can, try that but make sure terminal is in clear view.  This way you can check if anything is wrong when it causes X to freeze, and, maybe theres just some visual glitch

I'm running it from a terminal, and I see the output when ioquake becomes windowed. but nothing suspicious shows :(

---

### Post by ad_267 on 2009-04-08
This is an annoying bug that has been around for ages and still hasn't been fixed.

You can disable the screensaver or disable compiz to fix it (I've disabled compiz).

See:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/216154](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/216154)

---

### Post by akos.maroy on 2009-04-08
> **ad_267 said:**
> This is an annoying bug that has been around for ages and still hasn't been fixed.

You can disable the screensaver or disable compiz to fix it (I've disabled compiz).

See:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/157759)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/216154](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/216154)

thanks for the explanation and the URLs!

---


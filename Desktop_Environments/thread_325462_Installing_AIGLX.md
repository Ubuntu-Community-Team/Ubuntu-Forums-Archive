---
title: "Installing AIGLX"
date: 2006-12-25
forum: Desktop Environments
---

### Post by kevinlang21 on 2006-12-25
I'm using the [Beryl guide]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX") on installing AIGLX. i'm at the step where you install AIGLX. when i type > sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r` I get > E: Couldn't find package linux-dri-modules-2.6.15-27-386 I can't find the package in synaptic either.

---

### Post by Patrick-Ruff on 2006-12-25
AIGLX is built into xorg 7.1.  if you upgrade to edgy, it's all there ;).

---

### Post by Patrick-Ruff on 2006-12-25
make sure you sudo apt-get update   before all this. if you have, make sure your sources.list is correct.

---

### Post by kevinlang21 on 2006-12-25
i tried updating. i think i'll just get edgy

---

### Post by NeolineRy on 2006-12-31
Hi there,

Is there any advice that anyone can give apart from 'upgrade to Edgy', as it doesn't work with my laptop (X-Server fails to initialise properly), I'm stuck with Dapper, but would like to be running Beryl.

Compiz/XGL does work; are there any instructions for installing Beryl using XGL rather than xorg-air?

Any help you guys can give would be great.

---

### Post by kevinlyfellow on 2007-01-26
I got the itch to install it on my dapper machine too, but unfortunately...  I'm thinking about dropping down a kernel update since this apparently has been a problem for over a month

---


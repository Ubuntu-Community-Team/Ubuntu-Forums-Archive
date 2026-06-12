---
title: "avant problems in feisty"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by norton1 on 2007-04-30
hi, i was running edgy with beryl and avant window navigator and everything ran perfectly, my only trouble was with jackd and so after weeks of fruitlessly trying to fix it i thought i'd see if i had anymore luck under feisty... so i "upgraded"...

now beryl looks awful, and AVN completely screws up my display, oh and the problem with jackd is exactly the same....

i'm so frustrated i wanna just throw my computer at the wall and scream abuse at its shiny carcass,,,

can anyone help my fix my display or even get me back to edgy?? i really dont wanna do a complete reinstall of edgy 2.6.10 kernel thingy and build it all back up.....

---

### Post by hanzomon4 on 2007-04-30
I don't see how AWN could cause problems with jack, but....

What does beryl look like exactly, no window bars? black box around things like AWN? 

What video card do you have, nvidia? 

For jackd install qjackctl and look for error messages the client spits out.

For the beryl AWN problems the usually suspects I would look at is /etc/X11/xorg,conf, what driver package you installed and how you installed the package.

---

### Post by norton1 on 2007-04-30
hi - AWN isnt causing problems with jack - jack is just against me - the error message is unknown driver - alsa, i've tried changing the settings but cant get past that bit - 
awn problems caused by beryl in feisty - (everything works under compiz) it was working in edgy but i guess the upgrade killed it - i'm guessing there is a specific feisty version that i need to install instead???

---


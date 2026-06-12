---
title: "Closing the lid of Laptop forces me to relogin"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Son Volt on 2005-11-02
Every time I close the lid of my laptop, when I open it back up I have to enter my username and password. How do I disable this? It's not logging me out, it's just a black screen with a small box where I input my user/pass.

---

### Post by tmadsen on 2005-11-02
Ok, I'm not much a laptop man myself ... ain't got the dough ;) Anyway ... isn't there a some sort of button, that'll be pressed when you close your laptop? Maybe it's behaviour is similar to that of the power button?

I don't know, but maybe it's worth trying out. There's is a post about it here: [http://ubuntuforums.org/showthread.php?t=45368]("http://ubuntuforums.org/showthread.php?t=45368")

---

### Post by GrumpyBob on 2005-11-02
I thought this was normal behaviour.  On my laptop, if I suspend the computer I need to enter a password to start again.  Seems to me to be an eminently sensible security precaution.

Robert

---

### Post by Son Volt on 2005-11-02
[QUOTE=GrumpyBob]I thought this was normal behaviour.  On my laptop, if I suspend the computer I need to enter a password to start again.  Seems to me to be an eminently sensible security precaution.

Robert[/QUOTE]


This is a laptop that sits on my couch, security isn't an issue. It's annoying having to enter my password every time I wanna reach for my laptop. How can I disable this?

---

### Post by slaughterc on 2005-11-02
[QUOTE=Son Volt]This is a laptop that sits on my couch, security isn't an issue. It's annoying having to enter my password every time I wanna reach for my laptop. How can I disable this?[/QUOTE]

Look at /etc/default/acpi-support and comment out the following line:

  LOCK_SCREEN=true

---

### Post by Son Volt on 2005-11-02
[QUOTE=slaughterc]Look at /etc/default/acpi-support and comment out the following line:

  LOCK_SCREEN=true[/QUOTE]


thank you

---

### Post by Son Volt on 2005-11-02
Ok I tried commenting out that line and nothing happened. Rebooted with the changes and again, nothing happened. It's still requiring my password when I open up the laptop. Any other ideas?

---

### Post by Son Volt on 2005-11-07
ttt

---

### Post by gmc on 2005-11-08
[QUOTE=Son Volt]Ok I tried commenting out that line and nothing happened. Rebooted with the changes and again, nothing happened. It's still requiring my password when I open up the laptop. Any other ideas?[/QUOTE]

It seems to work on my Toshiba, thought all I've tried was shutdown/suspend. Perhaps re-enabling that option and change it to false, rather than true.

G.

---


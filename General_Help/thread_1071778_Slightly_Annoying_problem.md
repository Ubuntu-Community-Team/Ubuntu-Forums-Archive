---
title: "Slightly Annoying problem"
date: 2009-02-16
forum: General Help
---

### Post by Twitch6000 on 2009-02-16
Well I seen this program called lg3d or something like that and decided hey I like those effects and decided to install it.

Everything went okay until the lg3d-core file it had some sort of error and didn't install.

So I thought okay I just won't install it. I then took out the repos and went on setting up my fresh install of ubuntu.

I then updated and while updating it tried to install again.. and again(I think three times) 

All three times giving me the same error.

So I though okay lets try to force remove it,that failed aswell.

It said I need to configure it first...(which I tried and again it failed...)

So yeah help :(?

---

### Post by sumguy231 on 2009-02-16
Have you tried running
```
sudo apt-get -f install
```
in a terminal? That usually fixes broken packages like that. (The f stands for **F**ix Broken.)

---

### Post by Twitch6000 on 2009-02-16
> **sumguy231 said:**
> Have you tried running
```
sudo apt-get -f install
```
in a terminal? That usually fixes broken packages like that. (The f stands for **F**ix Broken.)

just tried it and got this -

> Setting up lg3d-core (1.0.0) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: No such file or directory
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: No such file or directory
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d-core
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by sumguy231 on 2009-02-16
Where did you download it from? There's a small chance that forcibly reinstalling it before attempting to remove it might help.

---

### Post by Twitch6000 on 2009-02-17
> **sumguy231 said:**
> Where did you download it from? There's a small chance that forcibly reinstalling it before attempting to remove it might help.

I got the repo from their site. However it is no big deal now I forced removed it finally.

Now if I can could get it to install that would be nice.

---


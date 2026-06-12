---
title: "Compiz Shadows 8.04"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by Naatan on 2008-04-03
I'm using Ubuntu 8.04 shadows and am not getting any shadows in compiz.. all the other compiz features seem to work fine.. has anyone else had this problem?

(I know it's in beta, I'm simply wondering if anyones had the problem and if there's a simple solution)

---

### Post by Naatan on 2008-04-03
lil' update: I got them working again using the nvidia drivers from their website, but it defaults to a yellow-ish color, I cannot change it in the window decoration settings..

---

### Post by alexsabree on 2008-04-03
> **Naatan said:**
> lil' update: I got them working again using the nvidia drivers from their website, but it defaults to a yellow-ish color, I cannot change it in the window decoration settings..

I had the same problem with 8.04

Make sure you don't have more than one compiz fusion menu customizer. I had "Advanced Desktop Effects Settings" and "Simple CompizConfig Settings Manager"

I got rid of that second one and I was able to disable/enable windows decorator settings. Don't forget to CTRL-ALT-Backspace to see the settings you change.

---

### Post by Naatan on 2008-04-03
I've only installed Advanced Desktop Effects Settings.. I did have Gnome Compiz Settings but I removed it..

is there something installed by default?

---

### Post by Naatan on 2008-04-05
Am I relaly the only one with this problem?

It's really annoying.. the shadows work at one point and stop working the next.. and they're always brightly colored.. not black

---

### Post by motang on 2008-04-06
> **alexsabree said:**
> I had the same problem with 8.04

Make sure you don't have more than one compiz fusion menu customizer. I had "Advanced Desktop Effects Settings" and "Simple CompizConfig Settings Manager"

I got rid of that second one and I was able to disable/enable windows decorator settings. Don't forget to CTRL-ALT-Backspace to see the settings you change.
Well I am in the same boat, mine was pinkish color.  I also had both installed simple and the regular ccsm.  I took off simple-ccsm and logged out and logged back in but no luck sitll have the pinkish shadown. :-(

---

### Post by Xgen on 2008-04-07
Seems to be a problem with the NVidia 8000's.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851")

---

### Post by FuturePilot on 2008-04-07
That's a duplicate of this bug
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/186382")
I'm in the same boat. It would seem that there's something messed up with one of the Nvidia packages in the repos. (possible the nvidia-kernel-common package) because manually installing the driver seems to fix it.

---

### Post by HanZo on 2008-04-22
the bug has been around for some time... what is it that stops them from squashing it out?
Thing is... you can solve the problem by installing the official Nvidia driver, which takes about 5 min. But every time you get an update and ubuntu gets new restricted modules, you have to reinstall the driver, and that's really bugging.

---

### Post by peddy on 2008-04-25
I have this problem too

---

### Post by Naatan on 2008-04-27
Fixed the bug thanks to this guy :)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37)

It's only a workaround though, since it will probably happen again when nvidia updates their drivers, but then again.. I'm guessing they'll fix this bug soon enough anyway.

So good having regular shadows again :)

---

### Post by dinamo9 on 2008-04-27
> **Naatan said:**
> Fixed the bug thanks to this guy :)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37)

It's only a workaround though, since it will probably happen again when nvidia updates their drivers, but then again.. I'm guessing they'll fix this bug soon enough anyway.

So good having regular shadows again :)

thanks! it sucessfuly fixed the problem

---

### Post by motang on 2008-05-05
> **Naatan said:**
> Fixed the bug thanks to this guy :)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/194851/comments/37)

It's only a workaround though, since it will probably happen again when nvidia updates their drivers, but then again.. I'm guessing they'll fix this bug soon enough anyway.

So good having regular shadows again :)

How do I go about fixing this?  I read your post on Launchpad but I don't how to go about doing it, thanks in advance.

---

### Post by cprofitt on 2008-05-07
[http://ubuntuforums.org/showthread.php?t=772408&highlight=compiz+shadows](http://ubuntuforums.org/showthread.php?t=772408&highlight=compiz+shadows)

---

### Post by ariel on 2008-05-25
> **dinamo9 said:**
> thanks! it sucessfuly fixed the problem

anyone fixed the no-shadow problem with this? (the fix seems to be for the pink-shadow which seems a different issue)

---


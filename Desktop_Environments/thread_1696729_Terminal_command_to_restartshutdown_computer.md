---
title: "Terminal command to restart/shutdown computer?"
date: 2011-02-27
forum: Desktop Environments
---

### Post by nrundy on 2011-02-27
I was playing with the Gnome-shell and my gui crashed. I was stuck in full-screen Terminal (i.e., Ctrl Alt F2) but I could not figure out how to shutdown/restart the computer.

Anybody know if there's a command for this that works from within Terminal?

---

### Post by haveaswiss on 2011-02-27
To restart just type:
```
sudo reboot
```

---

### Post by nrundy on 2011-02-27
thx man :)

makes me feel stupid but I was using Help and everything. just couldn't figure it out :)

---

### Post by doas777 on 2011-02-27
here is some info on the shutdown command.
also note at the bottom links for 'halt', 'poweroff', and 'reboot'.

---

### Post by nrundy on 2011-02-27
hey thanks!

how do you get a prompt to appear? I typed something and a question mark appeared. And whatever I do I can't get the ol Terminal prompt to show again. I press Esc and it says ^[

i suck at Terminal. hehe

---

### Post by nrundy on 2011-02-27
deleted

---

### Post by nrundy on 2011-02-28
someone's gotta know how to get back to command prompt. Anybody? Do you know why how to get back to prompt?

---

### Post by Jose Catre-Vandis on 2011-02-28
Try

```
CTRL+ALT+1  (or 2 or 3 or 4)
```to give you a new virtual terminal login prompt, or you may just need to login from where you are. All else fails, and you can't get control of the machine,its hold the power button in on the PC for a few seconds to do a hard shutdown.

There is another way of pressing a long list of buttons in a row (something to do with elephants???) but it fails me at the moment


Preferred shutdown command is:```
sudo shutdown -h 0
```
Preferred reboot command is:```
sudo shutdown -r 0
```

---

### Post by karmila on 2011-02-28
> **nrundy said:**
> hey thanks!

how do you get a prompt to appear? I typed something and a question mark appeared. And whatever I do I can't get the ol Terminal prompt to show again. I press Esc and it says ^[

i suck at Terminal. hehe

Usually Q or Ctrl+C works for me :D

---


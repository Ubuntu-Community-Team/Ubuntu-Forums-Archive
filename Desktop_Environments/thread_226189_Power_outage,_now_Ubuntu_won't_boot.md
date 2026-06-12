---
title: "Power outage, now Ubuntu won't boot"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Panserbjorn on 2006-07-30
There was a quick power outage 20 minutes ago. Now, Ubuntu goes to a blank screen after the main loading screen. It doesn't even get to the login.

Before the outage, my computer was installing a few programs via Automatix, though I'm pretty sure it was done by then. I had also activated 3D graphics with my Nvidia card.

Any ideas?

---

### Post by adamonduty on 2006-07-30
Can you boot into the ubuntu recovery mode option in grub? If not, can you boot normally then hit ctrl-alt-backspace and kill the x session?

If you can get to a shell you might try viewing .xsession-errors in your home directory, as well as deleting .Xauthority and .ICEauthority . I had problems with breezy where I had to do that occasionally.

You should also check the output from dmesg.

---

### Post by jISh on 2006-07-30
I'd say boot up into recovery mode.
Put
```
sudo apitude dist-upgrade
```
into the prompt, and let it finish then reboot.

---

### Post by Panserbjorn on 2006-07-31
Ctrl-alt-backspace gives me nothing. I get a blank screen and can't do anything. As for the rest of adamonduty's suggestions... well, today's my first day with Linux, and I sure don't know how to do any of that.

After executing jISh's suggestion, it said no packages would be installed, removed, etc. I rebooted and still couldn't get into ubuntu as usual.

Thanks for the help so far.

---

### Post by Panserbjorn on 2006-07-31
Now when it finishes the main boot screen for normal boot, my monitor goes into standby. I think this may have something to do with the Nvidia drivers, how it's acting.

---

### Post by Panserbjorn on 2006-07-31
Ah, success! I had the nvidia-legacy drivers installed, but needed the regular old nvidia drivers. Fixed it in recovery mode.

---

### Post by arnieboy on 2006-07-31
> **Panserbjorn said:**
> Ah, success! I had the nvidia-legacy drivers installed, but needed the regular old nvidia drivers. Fixed it in recovery mode.
can u please paste the results of the following command:
```
lspci -n | grep "0300" | cut -d " " -f3 | sed s/.*://
```
Thanks in advance.

---

### Post by Panserbjorn on 2006-08-01
The output was 0341. Sorry for the late response.

What's that for/what does it tell you? Just curious.

---

### Post by illogical_simmetry on 2006-08-04
I had this same problem too: after a power outage my gnome sessions used to crash right after loggin in and it prompted a message in which it said to check the ./Xsession-errors file in your home folder.
I solved it deleting both the .Xauthority and .ICEauthority files, in my home from the emergency shell loging. Then I logged in again with a gnome session and it worked just fine.
Thanks for the pointer adamonduty! :D :D

---


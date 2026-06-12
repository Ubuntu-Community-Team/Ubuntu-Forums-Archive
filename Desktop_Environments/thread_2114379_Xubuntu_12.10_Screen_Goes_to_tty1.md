---
title: "Xubuntu 12.10 Screen Goes to tty1"
date: 2013-02-09
forum: Desktop Environments
---

### Post by asdf-laptop on 2013-02-09
Randomly, after a few reboots (no installations)--my screen goes black. 

Two things may happen. It will stay black and I will see my mouse pointer and it will just hang there.

The second is it takes me to a virtual terminal (I think that's what its called). Basically a big black screen and at the top says like Ubuntu 12.10 tty1. 

Now before I press enter in GRUB and press e instead to edit. If I remove $vt_handoff or set it =7 (I don't know if the number even matters), then it works fine and the login screen appears. It even works if I remove the dollar sign ($).

Anyone know how to fix this?

EDIT: I also noticed it happened immediately after a reboot of installing restricted-extras. I tested this like 3 times and did 3 reformats. On the final format where I didnt go black for like 6 reboots. I ran boot-repair after updating and installing restricted extras. Running boot-repair again still doesn't fix it.

EDIT 2: Removing the word splash also fixes the problem

---

### Post by asdf-laptop on 2013-02-09
Alright so I did: 

sudo nano /etc/default/grub


removed the word splash. Saved and updated grub. It works. Does anyone else have any other solutions?

I enjoyed my custom splash screen!

---

### Post by movieman on 2013-02-12
I'm having something similar on 12.04 after updating a couple of days ago. Something like 60% of the time it now boots to a text console instead of the graphical desktop.

---

### Post by asdf-laptop on 2013-02-13
Yeah, exactly. What did you do to fix it?

---

### Post by movieman on 2013-02-13
> **asdf-laptop said:**
> Yeah, exactly. What did you do to fix it?

CTRL+ALT+DEL and keep rebooting until it works.

I have a vague suspicion that it's happening any time I don't manually select the kernel to boot in Grub at startup and it just uses the default. But the kernel I select is the default, so that makes no real sense; may just be coincidence that it always works when I do that.

I don't believe I have a custom splash screen, just the default Xubuntu one.

---

### Post by Bashing-om on 2013-02-13
Just a thought guys, Have yall tried a different graphics driver from the Additional Drivers utility ?

---

### Post by movieman on 2013-02-13
> **Bashing-om said:**
> Just a thought guys, Have yall tried a different graphics driver from the Additional Drivers utility ?

I believe it's using the Nvidia driver from there. It's been working OK for about two years, and suddenly stopped working properly with a recent update.

---


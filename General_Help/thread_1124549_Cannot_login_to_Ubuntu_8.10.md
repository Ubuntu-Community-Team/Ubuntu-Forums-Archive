---
title: "Cannot login to Ubuntu 8.10"
date: 2009-04-13
forum: General Help
---

### Post by mrd489 on 2009-04-13
The other day, I accidentally pulled the plug on my laptop (which has no battery, so it shut off).

When I went to restart and login, after I typed in my password the screen froze and would not login.

I then tried logging in without using GDM, and the message "-bash: /dev/null: Permission denied" appeared on screen repeatedly, and I am currently unable to access my computer.

---

### Post by defaultusername on 2009-04-13
mrd489,

[https://answers.launchpad.net/ubuntu/+question/16830](https://answers.launchpad.net/ubuntu/+question/16830)

Is that what you're describing? Reply with your results.

---

### Post by mrd489 on 2009-04-13
I followed these instructions, as provided in the link you posted...

> Open a Terminal open the /etc/rc.local file

sudo nano /etc/rc.local

and put before the exit 0 instruction

chmod 0666 /dev/null <---- insert this

exit 0 <--- don't touch this row

Save and reboot

...and it worked, thank you!

---


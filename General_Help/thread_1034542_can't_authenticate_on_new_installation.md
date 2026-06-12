---
title: "can't authenticate on new installation"
date: 2009-01-08
forum: General Help
---

### Post by rooster78383 on 2009-01-08
I just received a new Dell desktop with 8.04 pre-installed. Whil egoing through the initial setup, I entered my username and password the same as on all my other machines on the network. I suppose I might have made a mistake in entering my username and password (seems so highly unlikely). In any event, I cannot authenticate on this virgin machine.

Is there a way to set up a second user account without having logged in the first time? Or a way to log in as root? 

I really don't want to re-install as I want to back up all the drivers and configs as a first step.

Please help!

---

### Post by lovelyvik293 on 2009-01-08
You have to login as the root for the new user account.

---

### Post by rooster78383 on 2009-01-08
If I boot from a CD I can see the directory structure on the HD. Is there somewhere I can view the usernames? If I made a typing error it is most likely on the username as the password must be entered twice. FWIW I have tried every variation I can think of to no avail.

---

### Post by Loosewheel on 2009-01-08
Reboot, as soon as you see 'grub loading' press 'ESC', hit 'e', arrow down to the kernel line and press 'e', add 'single' to the end of that line, 'Enter', and 'b' for boot.

That will get you in as root. After that I'm not sure. Maybe type 'your user name' and 'passwd', 'Enter' and re-enter your passwd.....(If I remember correctly).

---

### Post by rooster78383 on 2009-01-08
This worked. Thanks so much.

---


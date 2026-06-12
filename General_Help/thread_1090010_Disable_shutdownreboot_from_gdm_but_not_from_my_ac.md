---
title: "Disable shutdown/reboot from gdm but not from my account"
date: 2009-03-07
forum: General Help
---

### Post by Dark Ares on 2009-03-07
Ok, so i went to system->administration->login window and i disabled the "show actions menu". Now I have 50% of the problem solved, because in the gdm there is no way of turning off the pc, but when i log in and go to system->quit, there is no way either. I want it so that no one can turn the pc off from the gdm screen, but once I login i can go to system->quit and be able to. I'm using 8.04. Thanks in advance for all your peoples help.

---

### Post by dcstar on 2009-03-07
> **Dark Ares said:**
> Ok, so i went to system->administration->login window and i disabled the "show actions menu". Now I have 50% of the problem solved, because in the gdm there is no way of turning off the pc, but when i log in and go to system->quit, there is no way either. I want it so that no one can turn the pc off from the gdm screen, but once I login i can go to system->quit and be able to. I'm using 8.04. Thanks in advance for all your peoples help.

[http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/)

---

### Post by beno1990 on 2009-03-07
Try this:

```

sudo nano /etc/gdm/gdm.conf

```

Find the shutdown, reboot, suspend, etc. command lines and comment them out.

---

### Post by Dark Ares on 2009-03-07
> **dcstar said:**
> [http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/)

That guide is now 3 years old, I tried following it but couldn't find the files it mentions. 
I will try beno1990 advice, i will be back to see how it works

EDIT: Once i comment them out do i need to run some command?

---


---
title: "Graphical Interface Problem on boot"
date: 2010-07-02
forum: Desktop Environments
---

### Post by Elsinor on 2010-07-02
Hi,
I've a problem with the Graphical Interface.
Until yesterday everything worked.
This morning turning on my pc, the graphical interface has no longer worked.
I can see only the terminal screen.
Can it be a video driver problem?

Could you help me to find the solution, please?
Thanks in a advance

---

### Post by clrg on 2010-07-02
1. Have you made configuration changes, especially to /etc/X11/xorg.conf?
2. Have you installed updates, especially graphics drivers, X11, GNOME?

What happens if you log in to that terminal and do a "sudo service gdm start", and then check whether it's running by swichting through the other terminals (Ctrl+Alt+F1, Ctrl+Alt+F2, Ctrl+Alt+F3... usually it runs on F7)

---

### Post by Elsinor on 2010-07-02
> **clrg said:**
> 1. Have you made configuration changes, especially to /etc/X11/xorg.conf?

No..

> **clrg said:**
> 
2. Have you installed updates, especially graphics drivers, X11, GNOME?
Graphics drivers... the last updates, but not the recommanded ones..
May this be the problem?

> **clrg said:**
> 
What happens if you log in to that terminal and do a "sudo service gdm start", and then check whether it's running by swichting through the other terminals (Ctrl+Alt+F1, Ctrl+Alt+F2, Ctrl+Alt+F3... usually it runs on F7)
I've logged in all the terminals now... when i press CTRL+ALT+F7 a new screen appears with this text:
```
*Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
*Setting sensons limits
*Speech-dispatcher configured for user sessions
*Starting VirtualBox kernel module
* done.
*Starting the Winbind daemon winbind
```
I don't know if it can be usefull, but the asterisk of "*Speech-dispatcher configured for user sessions" is the only one that's orange.

ps: Thanks for reply

---

### Post by clrg on 2010-07-02
You don't need to log in to all the terminals, just one, in order to start Gnome. It will appear on one of the others, usually the seventh.

To answer your question: If it worked, then you installed the not-recommended-driver, and now its broken, I guess the solution is obvious :)

---

### Post by Elsinor on 2010-07-02
> **clrg said:**
> You don't need to log in to all the terminals, just one, in order to start Gnome. It will appear on one of the others, usually the seventh.

To answer your question: If it worked, then you installed the not-recommended-driver, and now its broken, I guess the solution is obvious :)

Ohh good! 
Thanks for the help anyway.
I'll try to format.

---

### Post by clrg on 2010-07-02
NO! I didn't mean reinstallation of the system! Just install the old version of the driver, the version that worked before.

---

### Post by Elsinor on 2010-07-02
> **clrg said:**
> NO! I didn't mean reinstallation of the system! Just install the old version of the driver, the version that worked before.
Ah, It would be better...! But I don't know how to download it by terminal..

---

### Post by clrg on 2010-07-02
Navigate to the site using a web browser on another computer or using the live cd. Then, right-click on the download link, and select "copy link location" or something like that. In your terminal, type "wget <link>". That will download the specified file.

---

### Post by Elsinor on 2010-07-02
Thanks you!
Finally I've my desktop again :D

---

### Post by clrg on 2010-07-02
Please don't forget to mark the thread as solved.

---


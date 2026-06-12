---
title: "Disturbing on-screen splash"
date: 2005-03-24
forum: Desktop Environments
---

### Post by domo on 2005-03-24
I just install recently kubuntu-desktop on my laptop, everything is fine except that on KDE I have a splash screen who appearred randomly on my desktop with this message:
```
Display changed: lcd on
or 
Diplay changed: lcd off
``` 

I search everywhere on the control panel, but find nothing link with that message.
The same on google, nothing that help.

Any idea about that annoying message ?

---

### Post by Android on 2005-04-09
I am also expriencing this problem. I looked in xorg.conf file to see what it said under monitor and it just said "Default Monitor". I really don't know what to change it too. I'm using a Asus Laptop.

---

### Post by robstockley on 2005-06-07
This same annoying splash had me stumped for a while with my ASUS A2500D. In the end I decided to simply turn kmilo off (stop it being loaded) until either kmilo or the asus_acpi module is updated. I'm not going to pretend I know which (if either) is at fault. 

To make the splash go away do the following;

$ sudo gedit /usr/share/services/kded/kmilod.desktop

And make sure the following two lines are set to false

X-KDE-Kded-autoload=false
X-KDE-Kded-load-on-demand=false

Save the file and restart kde by either logging out and back again or by restarting X. This worked for me. Hopefully I'll get to turn it back on again one day because I quite liked kmilo.

Regards,
Rob (ubuntuforum at mowgli dot net dot nz)

---

### Post by ewerx on 2005-06-28
I have an Asus Z71V and I also have this problem. I am running Kubuntu 5.04.
What functionality will I lose if I disable kmilo?

---

### Post by N!co on 2005-12-11
Same problem on my Asus l3400tp with Kubuntu 5.10. But disabling kmilo solved it. Whatever kmilo is for......:confused:

---


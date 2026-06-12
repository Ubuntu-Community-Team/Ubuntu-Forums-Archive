---
title: "Cant not login to GUI."
date: 2008-07-31
forum: Desktop Environments
---

### Post by ynilesh on 2008-07-31
Hello, 

few days before i installed xubuntu packages in my laptop but after that i cant login to GUI directly. I do get command prompt when it boots that i have to manually specify which desktop player.
like, 
```
startx 
```
OR 
```
startxfce4
```

I tried to change runlevel from 2 to 5 but it dint help.

- nilesh

---

### Post by ibutho on 2008-07-31
On Debian based distros, changing runlevels from 2 to 5 generally will not help. You need to setup a login manager e.g. gdm to start at boot time. To do this, install the login manager and then run
```
sudo update-rc.d gdm defaults
```
Hope that helps.

---

### Post by ynilesh on 2008-08-01
sudo update-rc.d gdm defaults
 System startup links for /etc/init.d/gdm already exist.

Seems its already exist. 

- nilesh

---

### Post by ibutho on 2008-08-02
Can you run GDM manually e.g. by doing
```
sudo /etc/init.d/gdm start
```
Does it startup without any errors?

---

### Post by p_quarles on 2008-08-02
GDM is controlled in this case by the symlinks in /etc/rc2.d. To disable it, you would run something like this:
```
sudo mv /etc/rc2.d/S21gdm /etc/rc2.d/D21gdm
```
The "S" tells the system to run the target script, whereas "D" tells it to disable. The number indicates the level of priority given to the script. The only thing you need to change is the letter. Simply change it back to re-enable the display manager.

---


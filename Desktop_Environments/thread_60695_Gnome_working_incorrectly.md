---
title: "Gnome working incorrectly"
date: 2005-08-28
forum: Desktop Environments
---

### Post by umdzig on 2005-08-28
Ok i just changed the name of my computer (network name) to ubuntu from the original settings. Apparently my computer didnt like that. I now have no access to root terminal or anything that i need to access. I can not write anything to my hard drive. 

Everytime i log in i get the error:

"Could not lookup internet address for ubuntu. This will prevent Gnome from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts"

I would have added ubuntu to the file but i cant figure out how to do that when i do not have any write privileges.

Thanks for your help!!

---

### Post by cwaldbieser on 2005-08-28
[QUOTE=umdzig]Ok i just changed the name of my computer (network name) to ubuntu from the original settings. Apparently my computer didnt like that. I now have no access to root terminal or anything that i need to access. I can not write anything to my hard drive. 

Everytime i log in i get the error:

"Could not lookup internet address for ubuntu. This will prevent Gnome from operating correctly. It may be possible to correct the problem by adding ubuntu to the file /etc/hosts"

I would have added ubuntu to the file but i cant figure out how to do that when i do not have any write privileges.

Thanks for your help!![/QUOTE]
Try hitting CTRL+ALT+F1.  You should be taken to a console screen (all text-- no graphics).  There should be a login prompt.  Log in this way (note-- the password characters will not echo.  This is normal.).  Once you are in type hte command:
```
$ sudo nano /etc/hosts
```
This will start up the nano editor and let you edit the file.  Change your old computer name to the new one.  Hit CTRL+ALT+F6 (you may need to try different function keys if F6 is not the correct one) to take you back to the graphical login.  Try logging in now.

---

### Post by umdzig on 2005-08-28
I tried editing th file with the nano editor however that did not solve the issue. Can somome post a copy of their /etc/hosts file so i can see how it is supposed to be set up? Or if you have any other suggestions please post because now ubuntu is pretty much worthless since i am unable to do anything.

---

### Post by cwaldbieser on 2005-08-29
[QUOTE=umdzig]I tried editing th file with the nano editor however that did not solve the issue. Can somome post a copy of their /etc/hosts file so i can see how it is supposed to be set up? Or if you have any other suggestions please post because now ubuntu is pretty much worthless since i am unable to do anything.[/QUOTE]
Here is my /etc/hosts
```

127.0.0.1 localhost.localdomain localhost kepler

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
"kepler" is the hostname of my computer.
If that doesn't work, you can always try to reconfigure the gnome desktop from the commandline with dpkg instead of synaptic.  I think something like:
```
$ sudo dpkg --reconfigure gnome-desktop
```

---

### Post by umdzig on 2005-08-29
I decided to just re-install ubuntu completely.  I have everything working now that i have reinstalled.

Thanks for your help.

---

### Post by cardo on 2005-10-19
I had the same problem and  found in the internet a less drastic solution than the re-installation of OS.

Type as root
# cat /etc/hostname

Your machine name will be displayed, mine is 'bargie'. Now backup your existing hosts file.

 # cp /etc/hosts /etc/hosts.backup

Now type this, be sure to use your machinename and TWO (2) of the '>'!!

 # echo "127.0.0.1 bargie" >> /etc/hosts

 Try restarting X to see if the error message is gone. If you fsck'd things up , then:

# cp /etc/hosts.backup /etc/hosts

to restore the hosts file. Hope this helps!

---


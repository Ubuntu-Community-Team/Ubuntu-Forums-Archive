---
title: "Gnome startup"
date: 2005-04-13
forum: Desktop Environments
---

### Post by gstamp on 2005-04-13
I've got a problem with my gnome startup.  When I login it starts the apps for the session but the menu, icons and bottom panel are blank for about 5 minutes.  Something then seems to timeout and they come up and everything is fine.

It's almost as if it's waiting for an internet connection to timeout.  Any idea's?

---

### Post by gstamp on 2005-04-24
ping?

---

### Post by Knome_fan on 2005-04-24
I'm not really sure, but I think people where having this problem when something was wrong with their host file, so you might want to check /etc/hosts.

Good luck!

---

### Post by ShaneAu on 2005-04-25
I have the same problem.

/etc/hosts
```

127.0.0.1 localhost.localdomain localhost server

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by captainboog on 2005-05-08
i have this problem too
and then when it finally comes up, it asks if i want to delete every app that was loading on the bottom tray.  THEN, it doesnt display those apps (except show desktop) until i add another app to the bottom tray.

/etc/hosts:

127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by born_confused on 2005-05-08
aahhh, so Im not the only one with this problem. For a while I thought I was just special  O:) 

What im doing now is removing the card modules and laoding them once gnome has loaded.

its supposed to be a /etc/hosts problem. Im sure theres something deeper.
Gnome gives me an error. Just to see if it was gnome-related I installed xfce, same problem.

I had my /etc/hosts  and host.conf and resolv.conf kind of  'checked out'. Its not that. While I know you aint supposed to do this changing hostname to localhost seems to make the problem go away. :|

---

### Post by captainboog on 2005-05-09
well my problem went away (hope) after i installed the **nvidia-glx libs**. (i have an nvidia card)

i dont know what was the problem, but i tried so many combinations of compiling from source and different /etc/X11/xorg.conf configurations to get that nvidia driver to work properly.  

it's voodoo.  :)  
i guess it was searching for that glx library (even though i know i had it installed for some of the combinations that didnt seem to work)

for what it's worth, i checked, and do have a loopback interface.  my network isn't up until i run a script (shitty wireless card) after gnome boots.

---


---
title: "Switching from X to tty restarts gdm!!!"
date: 2005-11-18
forum: Desktop Environments
---

### Post by psypher on 2005-11-18
Hey all, before anybody flames me for not searching the forum for this just know that I have tried my best to find info on this. 

Whenever I switch from gnome to tty1 using ctrl-alt-f1 and try switch back to tty7 (X session) my gdm restarts, killing EVERYTHING I had running in that sessiosn. WTF??? Where did this come from, this never happened before in 4.10 or 5.04. 

I am running 5.10 and this happens on various PC's ranging from AMD Athlon's to  P4's.

Please help, this is not cool!

thanks in advance.

---

### Post by Kyral on 2005-11-18
How are you switching back? The only reason GDM would restart is if you hit ```
sudo /etc/init.d/gdm restart
```

---

### Post by psypher on 2005-11-21
[QUOTE=Kyral]How are you switching back? The only reason GDM would restart is if you hit ```
sudo /etc/init.d/gdm restart
```[/QUOTE]

ctrl-alt-f7, same way I have always done it in every other linux distro including ubuntu, before breezy. 

I found out I was wrong, it does not restart on an AMD box. Just my dell optiplex 170 with the 686 kernel. I haven't tried on 386, I will shutdown quick and give it a go.

---

### Post by llebegue on 2005-11-21
Same problem here. It was fine during the few weeks before Breezy went out. Then it didn't work no more. Every time the computer reboots when I try tu use ctrl+alt+Fx and switch back to ctrl+alt+F7 .... Could it be related to keyboard layout ? (mine is a French layout...)

---

### Post by SwePete on 2005-12-07
Using linux-image-2.6.15-7-amd64-generic and xorg-driver-fglrx I have a similar but even worse problem. When i try to switch tty my monitor blacks out and i cant get back to any tty (starting/switching between vterms or back to x). I have the same problem when I logout for anny of the Actions "Log out" "Shut down" "Reboot" and the shutdown sequense just stops dead.
As im using dapper i know im in the wrong forum section but I just did a search for "switching tty" and this thread showed up.
I have removed the splash boot up option (as sugested in another thread) with no change. 
Dose anybody have the same problem or a fix for it?

---


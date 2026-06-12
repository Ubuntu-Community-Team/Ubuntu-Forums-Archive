---
title: "Help... my ubuntu (Edgy) become very slow"
date: 2006-11-09
forum: Desktop Environments
---

### Post by ryurhrt on 2006-11-09
i don't know why , after add some software and update the ubuntu, it become very slow, slow in the way when starting a new gnome application, e.g: even when run the terminal, it show "starting terminal" about 10 second, and then invisible, and i have to wait about minute to wait it really started. other gnome base application also got this problem,but when the program is fully started up, work fine.What's wrong? It is the gnome problem or wat?


i install nvidia-glx, and some multimedia,internet s/w...

i try to restart GDM, and even restart the ubuntu, the same problem occur, loading from login screen to gnome desktop also take a few minute, the loading bar hanging there about 1-2 minute only disappear... :(

did any one also face the same problem? HELP HELP HELP !!!
Thanks.. :)

---

### Post by ryurhrt on 2006-11-10
I found out this problem seem to have some relation with the Network, when my ubuntu start program very slow, i deactivate & Re-activate the NIC, then system return normal.

i got installed firestarter, is it related?

---

### Post by ubuntpku on 2006-11-11
> **ryurhrt said:**
> i don't know why , after add some software and update the ubuntu, it become very slow, slow in the way when starting a new gnome application, e.g: even when run the terminal, it show "starting terminal" about 10 second, and then invisible, and i have to wait about minute to wait it really started. other gnome base application also got this problem,but when the program is fully started up, work fine.What's wrong? It is the gnome problem or wat?


i install nvidia-glx, and some multimedia,internet s/w...

i try to restart GDM, and even restart the ubuntu, the same problem occur, loading from login screen to gnome desktop also take a few minute, the loading bar hanging there about 1-2 minute only disappear... :(

did any one also face the same problem? HELP HELP HELP !!!
Thanks.. :)

I also have this problem. It just occurs several days after installation of Edgy. I tried reinstall the whole system and the same problem repeated.
It is really slow when starting applications: I need 7+ seconds to enter terminal on a Core Duo and 1G Memory laptop. Running applications after starting, however, is acceptably fast.

Could anyone give some advice?

---

### Post by ubuntpku on 2006-11-12
> **ryurhrt said:**
> I found out this problem seem to have some relation with the Network, when my ubuntu start program very slow, i deactivate & Re-activate the NIC, then system return normal.

i got installed firestarter, is it related?
Hi,ryurhrt. You're absolutely right. It is something because of networking.

Tried your idea and found everthing fast and fine.

---

### Post by jobou on 2006-11-14
Have the same problem! Did you guys solved it and how ?

Thanks

---

### Post by lavazza on 2006-11-15
I installed EdgyEft a couple of days ago and experienced the same problems, i.e. starting applications, no matter whether they are i-net related or not, took between 20 to 30 seconds in case I had no connection. If I was connected everything worked out nicely.

In my case some small changes in the /etc/hosts file solved the problem. Now the first lines are:

127.0.0.1 localhost <hostname>
127.0.1.1 <hostname>

where you put your hostname in the angular brackets. This way the window manager can quickly connect to the X server (without having to timeout a non-existent connection) and things are cool.

Cheers!!

---

### Post by ryurhrt on 2006-11-17
Thanks for yours solution, this help a lot man... :)

---

### Post by NiksaVel on 2006-11-17
this solved my problem too...  just needed to add the hostname at the end of the first line...  thanks!

---

### Post by brodock on 2006-11-25
did not work for me...
i can get nice speed at startup until gdm screen...
after that is a hell...
i got like 2 minutes to have gnome first load...
after that i can login again with acceptable speed

---

### Post by undefined on 2006-12-05
Didn't work for me either, the /etc/hosts trick, i mean. When i deactivate my nic everything returns 
to normal and works fast, but if i reactivate it everything becomes slow again. Any possible solutions?

---

### Post by Dezzy08 on 2007-01-02
I had the same problem with applications starting slowly and setting the /etc/hosts file to:

127.0.0.1 localhost <hostname>
127.0.1.1 <hostname>

worked for me as well. The application starting slowly problem started when I added a domain using System -> Administration -> Networking -> General (tab). Adding a domain changed the entry in the host file to:

127.0.1.1 <hostname>.<domain>

I removed the domain and everything is working fine.

---

### Post by sergeiline on 2007-02-14
The reason for this problem is that the hostname is /etc/hostname is differ to hostname in /etc/hosts. System cannot resolve its hostname to its ip address. Check your /etc/hostname and compare it to /etc/hosts.

---

### Post by Khaos on 2007-03-18
Worked fine for me, thanks for the tip :)

---


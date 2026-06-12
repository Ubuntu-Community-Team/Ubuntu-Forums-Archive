---
title: "Can't Get Gnome PPP or KPPP To Work"
date: 2006-03-25
forum: Desktop Environments
---

### Post by dirtaholman on 2006-03-25
Greetings All, 

  Recently I decided to try (K)Ubuntu as my knowledge of linux is very limited, and managed to get my Intel 536EP win-modem working courtesy of the DialupModemHowTo @ [https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4](https://wiki.ubuntu.com/DialupModemHowto#head-068a426acfdc8518889ea095253c50b665bce5d4)
   However, I can only get it to work through pppconfig, pon, and poff. Whenever I would try to use wvdial or Gnome PPP before i switched to Kubuntu it would dial, connect, immediately drop the connection, and try again. I have the same issue with KPPP. 

  Anyone have any suggestions? The only thing i can think of off the top of my head is the Init strings, but I've never playing with those before, so i have no clue. If i could get KPPP working I'd be exstatic, but if i can get some kind of graphical interface to tell me about my connection so I dont have to listen to my modem I would be happy. 

Thanks in advance!

EDIT: Sorry I didn't think to include this earlier, but this is what i get when I "sudo kppp" from konsole and try to  connect:

shorn@Steve2:~$ sudo kppp
Password:
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received ExecPPPDaemon
In parent: pppd pid 10447
Couldn't find interface ppp0: No such device
Kernel supports ppp alright.
pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.
pppd: (None of the available passwords would let it use an IP address.)
It was pppd that died
pppd exited with return value 1
Sending 10443 a SIGUSR1
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received RemoveLock
Opener: received PPPDExitStatus
Opener: received SetSecret
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received KillPPPDaemon
Opener: received RemoveLock
shorn@Steve2:~$

---

### Post by dirtaholman on 2006-03-26
Sorry Everyone,

  After banging my head against the wall and alot of searching, I finally found out that the problem was that I needed the noauth agurement (at least with KPPP anyway, dunno about wvdial or Gnome PPP).

  This link shows how to do it where you need to use sudo:
[http://www.linuxheadquarters.com/howto/networking/kppp.shtml](http://www.linuxheadquarters.com/howto/networking/kppp.shtml)

 And this link shows how to do it so you don't need sudo priveleges:
[http://ubuntuforums.org/showthread.php?t=81216](http://ubuntuforums.org/showthread.php?t=81216)

Hope this helps!

---

### Post by towsonu2003 on 2006-04-14
for wvdial, does adding these lines at the end of wvdial.conf work for you?

Carrier Check = no
Stupid Mode = yes

just curious.

Note: may be this should be added to the wiki?

---

### Post by dirtaholman on 2006-04-14
[QUOTE=towsonu2003]for wvdial, does adding these lines at the end of wvdial.conf work for you?

Carrier Check = no
Stupid Mode = yes

just curious.

Note: may be this should be added to the wiki?[/QUOTE]

I'm currently messing with Kubuntu's Dapper release, so I'm not sure if it's installed at the moment...I'll try to install it this weekend and get back to you.

Note: I noticed a few things that should be added to the wiki, and a typo that needs to be fixed in the part about the symlink, but I haven't learned how to edit wiki's yet.. I'd be more than happy to contribute the few things I've learned though.

Cheers

---

### Post by towsonu2003 on 2006-04-14
you can just open an account  (register), login to wiki, and hit "edit" (left upper corner.

---

### Post by dirtaholman on 2006-04-19
Sorry for the delay,

Adding those options to the end of wvdial.conf did the trick!  Thanks for the info, I'll keep it in mind the next time I use Ubuntu, and I'll add the info to the wiki as soon as i have a chance...feel free to add it if you would like if you have a moment before I do.

Thanks again for your help :D

---

### Post by towsonu2003 on 2006-04-19
[QUOTE=dirtaholman]
Thanks again for your help :D[/QUOTE]
you're most welcome :) have fun =D>

---


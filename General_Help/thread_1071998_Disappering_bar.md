---
title: "Disappering bar"
date: 2009-02-16
forum: General Help
---

### Post by socomhacker239 on 2009-02-16
well it all started when i tried to install limewire when i tried to install it, It froze so i turned the computer off and back on. I opened the limewire up and tried to install it again and it said to turn all the managers off and they all were off so i trieed to close it out and the is no way and on the internet there is no close sighn or minimize bar or anything sorry if im not explaining it good.

---

### Post by dzark on 2009-02-16
Huh? You what now?

---

### Post by socomhacker239 on 2009-02-16
ok the bar at the top of any program is gone the minimize and the thing that lest you close the program or make it smaller or bigger and when i tried to install limewire again it said i can only run one software thing at a time and i cant move a program where it is is where it stays

---

### Post by dzark on 2009-02-17
In all programs or just "Limewire"?


If you're using a plain flavour of ubuntu, try opening a terminal and running ```
metacity --replace &
```

and posting the results..

---

### Post by socomhacker239 on 2009-02-17
It does it in all programs like i cant even close or minimize the mozilla. it says this [1] 5722

---

### Post by dzark on 2009-02-17
any chance you've been playing around with other window management software like compiz? KDE?

You are running Ubuntu not Kubuntu/Xubuntu/etc?

Try restarting your window manager. Press Ctrl-Alt-F2 to switch to another console, then enter
```

sudo /etc/init.d/gdm restart
```

Note: This will kill any programs you're running on your desktop without warning so save first

---

### Post by socomhacker239 on 2009-02-17
ok i will try it i was deleting programs that i didnt need in the manager thats all i can think of. I have ubuntu.

---

### Post by dzark on 2009-02-17
Ha ha :)

Try

```
sudo aptitude install ubuntu-desktop
```

which should install the program you're missing :)

You may still have to restart gdm after that's done..

There's a little saying about linux - If you break it, you get to keep BOTH pieces ;)

---

### Post by gettinoriginal on 2009-02-17
If you have no "Title Bar", hit F11 twice, then manually minimize the window, then close the window, reopen and maximize with the maximize button, it should work after that.  :p

---

### Post by socomhacker239 on 2009-02-17
ok thanks for the replies im going to try them right now but what do you mean manually resize the window? No luck i tried it and it said( E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. )

---

### Post by socomhacker239 on 2009-02-17
okay thank you for all the help.
i have decided to just format beacause this is not working.

---

### Post by dzark on 2009-02-17
Hold up buddy :)

Did you run "sudo dpkg --configure -a" like it told you to?

and then "sudo aptitude install ubuntu-desktop" after that?

---

### Post by socomhacker239 on 2009-02-17
No okay i will try it.

---

### Post by dzark on 2009-02-17
The "sudo dpgk --configure -a" is to fix the broken aptitude/apt-get/"Add/Remove"/Synaptics... Its a lot nicer fix then some of the problems i've had after powercuts when install Photoshop on WinXP.

Next time let it finish running (and dont delete programs you dont know what they do ;)

---

### Post by socomhacker239 on 2009-02-17
this is what i got and yes i typed the other command i just didnt copy it.
socomhacker239@socomhacker239:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  linux-headers-2.6.27-7{u} linux-headers-2.6.27-7-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 52.0MB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download
socomhacker239@socomhacker239:~$

---

### Post by dzark on 2009-02-17
What linux are you running?!?!?!? Remember an hour ago when i asked what you're running and you replied 'ubuntu'... It's clearly not

So.. is it 64bit, ARM, PowerPC, etc?

What version is it? 8.10, 8.04, 7.10 etc?

---

### Post by socomhacker239 on 2009-02-17
i have this iso [http://www.ubuntulinux.org/getubuntu/download](http://www.ubuntulinux.org/getubuntu/download).
so far to my understanding i have ubuntu 8.10 32 bit version.

---

### Post by socomhacker239 on 2009-02-17
okay thanks for all the replies but im just going to format

---


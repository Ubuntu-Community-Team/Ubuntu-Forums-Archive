---
title: "Network Problem - Software problem?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by blacktorch on 2006-06-29
Hey, I'm having problems with the network, after installing Dapper Drake. whenever I boot Ubuntu, Internet isn't working. For it to work, each time I start the PC I have to go to System -> Administration -> Networking, then I have to deactivate and then activate eth0 again. Then it works fine. This is **really** annoying, can anyone help me?

---

### Post by Maggot on 2006-06-29
I use to have that problem too, sadly I cannot remember what I did to fix it. Have you applied all updates yet seeing as you just installed dapper?

---

### Post by blacktorch on 2006-06-29
[QUOTE=Maggot]I use to have that problem too, sadly I cannot remember what I did to fix it. Have you applied all updates yet seeing as you just installed dapper?[/QUOTE]
That was the first thing I did, after I figured out how to get the Internet working. Hope you, or anyone else remember how to fix it, and I hope the devs will fix the bug as well.

---

### Post by blacktorch on 2006-06-29
No one? :(

---

### Post by blacktorch on 2006-06-29
OK, so I still haven't fixed this problem. I thought I'd post my /etc/network/interfaces, so if you see a problem, tell me.

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
```

... and here's my /etc/hosts

```
127.0.0.1 localhost kaka
127.0.1.1 kaka

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by blacktorch on 2006-07-01
I'm still having this problem.

---

### Post by blacktorch on 2006-07-02
Still having problems.

---

### Post by Eazy© on 2006-07-05
I also have the same problem. Sometime it works after I reboot, I dont have to inactivate  and activate from kcontrol but mostly I have to. This was the same problem I had when I tried Ubuntu (using Kubuntu now), so perhaps this is a bug in Dapper. I didnt have these problems in Breezy. If anyone know of a solution I would be grateful :)

---

### Post by notepad on 2006-07-05
blacktorch, im having this ^*(%$& problem too. i want to know what maggot did. i think hes making it up. 

i would put up with this problem if i could make a script for my wife to run when she boots linux and internet isnt working but writing a script for a normal user without admin privs to run programs such as /etc/init.d/networking is proving to be incredibly difficult. 

maggot: think back to what you did. we all want to know.

---

### Post by Eazy© on 2006-07-08
This command: "sudo /etc/init.d/networking restart" (without the " ") fires up my network. Can I put this line somwhere in some startup file other than making a script and put it in .kde/Autostart ?

I guesse that I have to do the trick: "sudo without promt for password" if I make a script and put it in Autostart, but I dont want to do that. So if anyone knows what file I could put the command: "sudo /etc/init.d/networking restart" I would be gratefull!

---

### Post by bartbes on 2006-07-08
I have about half of the problem, but mine is worse. It can't see my network card anymore :(

BTW Eazy you can put your script in /etc/rcX.d (and X is the runlevel) or /etc/init.d
(it can also be /etc/rcX)

---

### Post by Eazy© on 2006-07-08
Thanx for the suggestion bartbes!

What I did was:
open kate and put this in:

```
#!/bin/bash
/etc/init.d/networking restart
```

Named it "networkrestart" and saved it on my desktop (don't need to chmod a+x the file as Kate seem to do it for you).

Then I opend a console and wrote "sudo konqueror" and moved my file "networkrestart" to /etc/init.d. Then I made a symbolic link from "networkrestart" and puted that in /etc/rcS.d and then renamed the symbolic link "networkrestart" to "S49networkrestart"

I rebooted to see if it worked, and it did. I have only rebooted once to test, so I dont know if it will work as my network did work sometimes before I did this.

Sorry to be a bit rambeling, but I have a bad english writing day :P

I'm sorry that I dont have a suggestion for your problem bartbes, but I'm still kind of a noob on linux.

Edit:
Have rebooted lots of time since I did this and it's still working, so this seem to be the solution :)

---

### Post by zool2005 on 2006-07-12
I had a similar problem with Dapper and often had to restart networking manually through the GUI.
This is a simple but effective workaround, at least until the underlying cause is found!
Thanks

---

### Post by chill on 2006-07-12
I have this problem too.

After I boot up I too need to Deactivate->Activate my network card in order to get to net. :)

I have [Epox 9NPA+Ultra](http://www.epox.com.tw/eng/products_content.php?ps=335) mobo with nForce4 Ultra chipset.

---


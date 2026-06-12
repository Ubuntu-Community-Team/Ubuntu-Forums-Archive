---
title: "Linux Effecting Windows Bandwidth"
date: 2005-12-12
forum: General Help
---

### Post by donvella on 2005-12-12
since i installed ubuntu, i have had major problems with my Telstra Cable bandwith on windows. I get over 1mb/sec on ubutuntu, but when i restart into windows i barely manage 1kb/sec, can someone please explain to me a solution to this problem.

-=THE ISSUE IN THIS TOPIC HAS BEEN RESOLVED=-

---

### Post by daller on 2005-12-12
I have a hard time seeing that this should be ubuntu's fault!

If I were you, I would delete the windows partition, and merge the free space into the ubuntu partition. :D

---

### Post by Chris Tucker on 2005-12-12
this is most likely not caused by your ubuntu, just fix windows, you might need to reinstall, but dont forget to reinstall ubuntu if windows eats it too ;)

---

### Post by localzuk on 2005-12-12
[QUOTE=donvella]since i installed ubuntu, i have had major problems with my Telstra Cable bandwith on windows. I get over 1mb/sec on ubutuntu, but when i restart into windows i barely manage 1kb/sec, can someone please explain to me a solution to this problem.[/QUOTE]

There is no feasible way that Ubuntu/Kubuntu could be affecting the bandwidth of your cable in Windows as they are separate OS's and as such do not share any of the components  - ie. they cannot see each other further than knowing that there are different partitions on a disk/multiple disks.

The most likely cause of your issues are:

1. Spyware
2. Viruses
3. Over zealous firewalls incorrectly configured
4. Windows Networking components are broken

The normal solution that I advise to customers with similar issues is to re-install as it will save pain later.

There is another possibility - you just happen to be using Windows at the same time everyday and that time happens to be the peak time for your cable cell (as cable is a shared connection). This is probably unlikely though.

---

### Post by Chris Tucker on 2005-12-12
[QUOTE=localzuk](as cable is a shared connection)[/QUOTE]
not common anymore

---

### Post by Aryxa on 2005-12-15
I am with Telstra bigpond, and I never had any problems with Ubuntu effecting windows, especially cable connection.

---

### Post by fannymites on 2005-12-15
What modem do you have?  When switching between ubuntu, windows and other linux flavours it has various problems from slowing down the connection to not even working at all.
The developers of the eciadsl driver I'm using are aware of problems and their advice is to unplug the modem, wait and plug it back in again.

---

### Post by donvella on 2005-12-15
Unfortunately I have since formatted reinstalled everything multiple times, and come to the conclusion that it is just massive amounts of bugs and such due to the fact of having Windows, laughable.

---

### Post by guice on 2005-12-15
It's not (k)ubuntu. It's something else that's causing your problem. For one, you're the only one I see with this problem and two, you're definalty not the only one with dual boot. My XP partition has no net slow down issues.

---

### Post by donvella on 2005-12-16
You must have misunderstood me.
When i formatted/reinstalled windows it was fine until i FIRST installed the internet, and then i get flooded with spyware, worms, viruses. Its because i didnt have a firewall setup due to the fact that its not permitted on this machine. Its fixed now using Zone Alarm firewall when installing for the first time. Future warning to anyone using windows, make sure you have a very good firewall before activating your internet.

---

### Post by daller on 2005-12-16
[QUOTE=donvella]You must have misunderstood me.
When i formatted/reinstalled windows it was fine until i FIRST installed the internet, and then i get flooded with spyware, worms, viruses. Its because i didnt have a firewall setup due to the fact that its not permitted on this machine. Its fixed now using Zone Alarm firewall when installing for the first time. Future warning to anyone using windows, make sure you have a very good firewall before activating your internet.[/QUOTE]

Again, what does this have to do with ubuntu?

---

### Post by codejunkie on 2005-12-16
[QUOTE=donvella]since i installed ubuntu, i have had major problems with my Telstra Cable bandwith on windows. I get over 1mb/sec on ubutuntu, but when i restart into windows i barely manage 1kb/sec, can someone please explain to me a solution to this problem.[/QUOTE]
i had similar problems with my cable modem and it was the cable modem/providers  fault not ubuntu, what happend is between switching os's the modem had trouble renewing the ip address via dhcp. the only thing that fixed it temporarly was shutdown the pc, power cycle the modem wait for it to get a stable connection turn on the pc and boot into windows i got tired of that real quick, and went and bought a cheap router and never had the problem again because the router obtaine's the ip from my cable modem and handles providing the ip addresses to the computer and now it works great.

---

### Post by teaker1s on 2005-12-16
most win modems install firmware each time they load, eg bt voyager 105- If your modem doesn't power down say 10 sec then the firmware will still be there when you reboot.
I'd suggest you unplug the usb modem for 10 sec.
 plug in and boot windows and see if it works. 
You could be having firmware/os issues if the modem isn't powered down:KS

---

### Post by guice on 2005-12-16
[QUOTE=donvella]You must have misunderstood me.
When i formatted/reinstalled windows it was fine until i FIRST installed the internet, and then i get flooded with spyware, worms, viruses. Its because i didnt have a firewall setup due to the fact that its not permitted on this machine. Its fixed now using Zone Alarm firewall when installing for the first time. Future warning to anyone using windows, make sure you have a very good firewall before activating your internet.[/QUOTE]
Never EVER connect to the Live internet on a windows system, EVER. Use a hardware firewall/router at ALL times. It protects you from 100% of all the random floating crap on the open net.

I don't use a software firewall. I have a LinkSys router that works as a hardware firewall. It blocks all incoming ports (except ones I open up) and just allows traffic I request in. I recommend getting one.

And also, I do agree with others, what does this have to do with Ubuntu?

---

### Post by Cromie on 2005-12-17
About your window problem you are having, Im taken into account that you use a NIC card. All you really need to do is get a driver update to that nic card , then reinstall the driver for that card, this has been a long time problem with windows due to the REG getting screwed up...  SCrewed up and windows ,,hmm sounds like a common thing,,,, 

Its the number one money making thing i can do for any customer...

---

### Post by donvella on 2005-12-17
I tried to explain to you guys earlier, i will now put it up on the subject title: i explained that after reformatting and losing Ubuntu and Windows i noticed my internet speed was perfectly fine UNTIL i unistalled Ubuntu. So naturally process of illimination shows that ubuntu was effecting windows, which in turn i found out was not. So thanks for your help, this topic is closed.

---


---
title: "Dell XPS M1530's wireless problem to be solved?"
date: 2009-10-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jasonkirk2006 on 2009-10-01
Hello,

I've been using Dell XPS M1530 for more than a year. From the first day, i'm having difficulty with wireless card Intel Pro/Wireless 3945ABG. Not even one suggestion solved my problem such as modprobing with disable_hw_scan or keeping rfkill hardware button at 0 for all times.

Now my Jaunty uses kernel version 2.6.28. I also use another linux distro [Pardus]("http://www.pardus.org.tr") which uses kernel version 2.6.30. The wireless problem has vanished in Pardus, where as my Jaunty is still suffering from it (besides, Vista never had such a problem). I took a quick look at the modules loaded and i noticed that there are modules **dell_laptop** and **rfkill** in Pardus, which i suppose are the solutions of the problem.

Can anyone of you, Ubuntu Masters, please confirm my diagnosis? Will my problem go away with the new kernel version, that will problably have the **dell_laptop** and **rfkill** modules?

---

### Post by mikewhatever on 2009-10-03
I am surprised there is a problem with that wireless card. Mine has been working on an HP for a few years without tweaking, ndiswrapper or anything else. I don't have the modules you mentioned loaded.
What is the problem exactly? What happens when you try connecting using an unmodified installation or a live cd?

As for other OSs, I don't think you can draw conclusions based on Pardus or Windows. Pardus is not a Debian distro, so that it's likely to have it's own modules, and Windows is just Windows.

Just out of curiosity, have you tried another release of Ubuntu?

---

### Post by jasonkirk2006 on 2009-10-06
> **mikewhatever said:**
> I am surprised there is a problem with that wireless card. Mine has been working on an HP for a few years without tweaking, ndiswrapper or anything else. I don't have the modules you mentioned loaded.
What is the problem exactly? What happens when you try connecting using an unmodified installation or a live cd?

As for other OSs, I don't think you can draw conclusions based on Pardus or Windows. Pardus is not a Debian distro, so that it's likely to have it's own modules, and Windows is just Windows.

Just out of curiosity, have you tried another release of Ubuntu?

Hi mikewhatever,

I've tried Kubuntu 8.04, Ubuntu 8.04 8.10 (live and install) and 9.04, Fedora, OpenSuse and Pardus with ipw3945, iwl3945 or ndiswrapper. They all had problems with the wireless card. I suspect that the problem is with the rfkill switch, according to my [previous thread]("http://ubuntuforums.org/showthread.php?t=90075").

My problem is something like that:

Independent of the position of the wireless kill switch (which is a sliding hardware switch on my machine, not a Function+F4 combination or something) when i boot linux, i get output similar to this (dmesg | grep 3945):

```

iwl3945: MAC is in deep sleep
iwl3945: Unable to int nic

```

or sometimes:

```

iwl3945: Detected Intel Wireless WiFi Link 3945ABG
iwl3945: Error: saturation power is -1, less than minimum expected 40
iwl3945: Invalid power index
iwl3945: initializing regulatory failed: -5
iwl3945 0000:0b:00.0: PCI INT A disabled
iwl3945: probe of 0000:0b:00.0 failed with error -5

```

After applying some recommendations such as:

```
	sudo rmmod -f iwl3945 && sudo modprobe iwl3945 disable_hw_scan=1

```

or installing backports modules or upgrading kernel version i got nothing! Turning the wireless switch on and off several times was not a fix neither.

I should say that this is not always the case. Sometimes I can scan the wireless networks around me and connect without any problem in linux.

I can simply check the output of

```
ifconfig -a
```

or

```
sudo lshw -C network
```

and if the MAC address of my wireless card goes 00:00:00:00:00:00 then definitely there will be no wireless connection. But if the MAC address is correct, then everything will be alright (By the way, this is nothing to do with the Ubuntu's default action of disabling wireless card when the machine is connected to a wired network, since disabling a network card never resets it MAC address, as this was argued at some point).

This was the summary of what i've experienced, hoping it was clear enough. My machine is a Dell. Not all 3945 cards has this problem. But this is not a hardware failure, since Windows works perfectly, as i said.

By looking at the number of replies to this thread, i can see that this is not a frequently met problem in the community so i will be celebrating this alone :)

Thanks for your reply anyway.

---

### Post by omarly on 2009-10-07
I got the same box and - yes all the same problems. Sometimes i have to boot 3-4 times to get it working. Same problem with Open Suse, witch I tested after the fatal update of 9.10. I wish it would be a better way than rebooting

I am running 9.04 and not as it says in my signature 9.10

---

### Post by &gt;hankim&lt; on 2011-09-16
I leave you there this link that seems to solve the problem, it hasn't  worked for me as I don't know how to install with make install from the  console yet, if anyone tries it and works for him, I beg please send me a  clue! thx! I'll try to research anyway but its good to make things easier!
 
 [http://debii.curtin.edu.au/~pedram/t...-on-ubuntu-810]("http://debii.curtin.edu.au/%7Epedram/thoughts/linux/80-howto-solve-dell-xps-m1330-freeze-problem-on-ubuntu-810")
 
 farewell!

---


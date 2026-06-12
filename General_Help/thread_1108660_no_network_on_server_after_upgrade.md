---
title: "no network on server after upgrade"
date: 2009-03-27
forum: General Help
---

### Post by Linux&amp;Gsus on 2009-03-27
I just upgraded the server (Debian 4.0 (Etch) to 5.0 (Lenny)). As far as I can tell all seems well, except that I don't get any network connection anymore.

So, I connected to the server (ssh) from my laptop and followed the following guide:
[http://www.debianadmin.com/howto-upgrade-from-debian-etch-40-to-lenny-50.html]("http://www.debianadmin.com/howto-upgrade-from-debian-etch-40-to-lenny-50.html")
Then after reboot I didn't get any connection to the server and dragged a screen over.

On the server, when I try to ping I get "connect: network is unreachable" for basically any kinda ping except "127.0.0.1".

After searching around for a while I found a lot of people seem to have problem after upgrade with IPV6, which, apparently, it defaults to in Lenny. However, what ever fix (disabling IPV6) I tried, it doesn't make any difference.

I know it's not Ubuntu Server, but since it's based on Debian I was hoping that someone here has an idea.


Thanks in advance,
L&G

---

### Post by hyper_ch on 2009-03-29
how do you connect the server to the net? wifi or ethernet?

---

### Post by Linux&amp;Gsus on 2009-03-29
Ethernet, there is no wifi.

---

### Post by hyper_ch on 2009-03-29
pastebin the output of

```

cat /etc/network/interfaces

```

---

### Post by lykwydchykyn on 2009-03-29
Can you post the output of lscpi -- most pertinently, what network adapter you have?

Certain network firmware was removed from the main repos and put in non-free.  I very nearly rebooted one of my servers after upgrade before noticing this tidbit in the upgrade output.  You just have to install the appropriate package for your network card.  Of course, you need a network connection to do this, which means booting back to the old kernel for a bit.

---

### Post by Linux&amp;Gsus on 2009-03-30
> **hyper_ch said:**
> pastebin the output of
```

cat /etc/network/interfaces

```

Here it is...
```

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
allow-hotplug eth0
iface eth0 inet static
[INDENT]address 192.168.0.4
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1[/INDENT]

```

To me it looks OK, but who knows...

Cheers,
L&G

---

### Post by Linux&amp;Gsus on 2009-03-30
> **lykwydchykyn said:**
> Can you post the output of lscpi -- most pertinently, what network adapter you have?
I assume you mean "lspci"? Anyways, strangely enough this command does not work, the output I get is:
-bash: lspci: command not found

I can't recall to have ever installed anything specific to make "ls" or "lspci" work. :confused:
Is there another way to get to this information. Other than searching for the manual and hope to find the (correct and up-to-date) information about the hardware.

> **lykwydchykyn said:**
> Certain network firmware was removed from the main repos and put in non-free.  I very nearly rebooted one of my servers after upgrade before noticing this tidbit in the upgrade output.  You just have to install the appropriate package for your network card.  Of course, you need a network connection to do this, which means booting back to the old kernel for a bit.
In case that is what happened to me here. Well, and figuring out what my ethernet card is, of course. What would I need to do to make it work again?

Cheers,
L&G

---

### Post by hyper_ch on 2009-03-30
lspci should work... what's the output of
```

ifconfig

```

maybe set your interfaces to dhcp and then run ifconfig.

---

### Post by lykwydchykyn on 2009-03-30
> **Linux&Gsus said:**
> I assume you mean "lspci"? Anyways, strangely enough this command does not work, the output I get is:
-bash: lspci: command not found


Yeah, sorry, typo.  
> 
I can't recall to have ever installed anything specific to make "ls" or "lspci" work. :confused:
Is there another way to get to this information. Other than searching for the manual and hope to find the (correct and up-to-date) information about the hardware.

It's in package pciutils.  Not sure why that's not installed for you.  dmidecode or lshw might help you, but they may not be installed either.  There might be a way to get the information from /proc or /sys/devices, but I'm not certain.

> 
In case that is what happened to me here. Well, and figuring out what my ethernet card is, of course. What would I need to do to make it work again?

Cheers,
L&G

Well, if you have your old kernel, you should be able to boot to it, and the network card should work under the old kernel.  If that does indeed work, then you can install pciutils and figure out what firmware to install.

If it doesn't work under the old kernel, the problem may lie elsewhere.  Are you sure the upgrade completed?

---

### Post by Yashiro on 2009-03-30
Try changing allow-hotplug eth0 to auto eth0.
Save and reboot. (or just run init.d/networking, or whatver they call that in debian these days.)

---

### Post by Linux&amp;Gsus on 2009-03-31
> **hyper_ch said:**
> lspci should work... what's the output of
```

ifconfig

```

maybe set your interfaces to dhcp and then run ifconfig.

ifconfig output:
```
lo[INDENT]Link encap:Local Loopback
inet address:127.0.0.1  Mask 255.0.0.0
inet6 address: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:504 errors:0 dropped:0 overruns:0 frame:0
TX packets:504 errors:0 dropped:0 overruns:0 carrier:0
collusion:0  txquelen:0
RX bytes:40756 (39.8 KiB)  TX bytes:40756 (39.8 KiB)[/INDENT]

```

Setting interfaces to dhcp? Sorry, you lost me there. No clue how to do that. I'm not afraid of console work, and I do some, but I'm really not too knowledgeable about that.

---

### Post by Linux&amp;Gsus on 2009-03-31
> **lykwydchykyn said:**
> Yeah, sorry, typo.
No worries, just wanted to be sure since I'm not the most knowledgeable person about this. You never know if there are 2 very similar commands...  


> **lykwydchykyn said:**
> It's in package pciutils.  Not sure why that's not installed for you.  dmidecode or lshw might help you, but they may not be installed either.  There might be a way to get the information from /proc or /sys/devices, but I'm not certain.
lshw is working either. dmidecode is giving a heck of a lot output. But since I have a screen plugged in on the machine directly I can only see what ever fits on the screen. So, I can't tell if there is anything useful.
/proc and /sys/devices didn't help me either. Don't know where I should look for the relevant information.


> **lykwydchykyn said:**
> Well, if you have your old kernel, you should be able to boot to it, and the network card should work under the old kernel.  If that does indeed work, then you can install pciutils and figure out what firmware to install.
AFAIK there is still the old kernel on the machine. But will that work even though I upgraded the OS?
I'll try to boot that and see what happens.


> **lykwydchykyn said:**
> If it doesn't work under the old kernel, the problem may lie elsewhere.  Are you sure the upgrade completed?
Well, at least in /etc/debian_version it says "5.0", the latest version. I admit that it feels a bit slow when booting the machine. But other than that I wouldn't have any hint that it would have not upgraded completely.
Is there any other way to verify that it completed the process? What would happen when I run "apt-get dist-upgrade" or "apt-get upgrade" again?


Cheers,
L&G


EDIT:
I *quickly* tried to boot the old kernel. It feels like that one would boot at the very least 4x faster than the new one. Network is working with that older one, internet access no problem.

pciutils wasn't installed... for what ever reason. Anyways, I installed it and this is the Ethernet card I have there:
Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
It's a dual Gigabit card.

Also, just for the record, the old kernel is: 2.6.18-5-amd64
The new one is: 2.6.26-1-amd64

---

### Post by Linux&amp;Gsus on 2009-03-31
> **Yashiro said:**
> Try changing allow-hotplug eth0 to auto eth0.
Save and reboot. (or just run init.d/networking, or whatver they call that in debian these days.)

Hi,
I tried that but unfortunately it didn't make any difference. So, I guess I revert that again.

Cheers,
L&G

---

### Post by lykwydchykyn on 2009-03-31
> **Linux&Gsus said:**
> But since I have a screen plugged in on the machine directly I can only see what ever fits on the screen. So, I can't tell if there is anything useful.

For future reference, you can hit shift-pageup and see the previous screen(s).
> 
Well, at least in /etc/debian_version it says "5.0", the latest version. I admit that it feels a bit slow when booting the machine. But other than that I wouldn't have any hint that it would have not upgraded completely.
Is there any other way to verify that it completed the process? What would happen when I run "apt-get dist-upgrade" or "apt-get upgrade" again?

If your upgrade were interrupted, you would know from running apt-get dist-upgrade.  It would either install more packages, or give you an error indicating you need to run "dpkg -configure -a".
> 
EDIT:
I *quickly* tried to boot the old kernel. It feels like that one would boot at the very least 4x faster than the new one. Network is working with that older one, internet access no problem.

pciutils wasn't installed... for what ever reason. Anyways, I installed it and this is the Ethernet card I have there:
Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet (rev 12)
It's a dual Gigabit card.

Yep, that's one of the ones you need to get firmware for.  I had the same NIC in my server.  You need to install the package "firmware-bnx2" from the non-free repositories, then boot back to your old kernel.  It should be fine after that.

BTW:  free piece of advice from someone who has been running Debian servers through 3 releases now: Always read the release notes before upgrading.  They aren't terribly long, and are usually very informative about things like this.  I have learned this the hard way myself.
EDIT: to be fair, though, this particular issue was NOT mentioned in Lenny's release notes.  Should've been.

---

### Post by Linux&amp;Gsus on 2009-04-01
> **lykwydchykyn said:**
> For future reference, you can hit shift-pageup and see the previous screen(s).
Sounds so simple that everyone should know it... That says a lot about my level of knowledge about working with the console, I guess.
Thanks for the hint. I hope I can remember it until next time when I need that.


> **lykwydchykyn said:**
> If your upgrade were interrupted, you would know from running apt-get dist-upgrade.
Tried that, nothing to install, so I assume that the upgrade work just fine.


> **lykwydchykyn said:**
> Yep, that's one of the ones you need to get firmware for.  I had the same NIC in my server.  You need to install the package "firmware-bnx2" from the non-free repositories, then boot back to your old kernel.  It should be fine after that.
OK, so that did the trick. Thanks everyone for your help and advise. I'm happy that it turned out to be so easy fixable. First I thought the upgrade was messed up or at least a strange configuration problem.
But now I added the non-free repo and installed the firmware and it works fine.

Thanks again for the help.
I'm the happiest man on earth right now.


> **lykwydchykyn said:**
> BTW:  free piece of advice from someone who has been running Debian servers through 3 releases now: Always read the release notes before upgrading.  They aren't terribly long, and are usually very informative about things like this.  I have learned this the hard way myself.
EDIT: to be fair, though, this particular issue was NOT mentioned in Lenny's release notes.  Should've been.
After that... I guess, ya, I'll do that. I've never done that, not for server nor for desktop/laptop. Might be good to start doing that, though.


Cheers,
L&G

---


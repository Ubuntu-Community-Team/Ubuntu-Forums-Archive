---
title: "no connection to the internet"
date: 2005-11-01
forum: Desktop Environments
---

### Post by nautilu on 2005-11-01
i just installed the breezy from DVD and can't connect to the internet not with firefox and not with synaptics.
the odd thing is that i can ping internet domains.

my computer is connected through ethernet DSL modem wich runs DHCP and NAT.
there's no problems whatsoever in Windows.

---

### Post by suRoot on 2005-11-01
From a console:

```
telnet www.google.com 80
```

What happens?

---

### Post by mips on 2005-11-01
You should post in the networking forum....

---

### Post by nautilu on 2005-11-01
[QUOTE=suRoot]From a console:

```
telnet www.google.com 80
```

What happens?[/QUOTE]

i can't run the computer right now but i already did this.
i got the usual output with google.com ip address
in other words that part is just fine

---

### Post by mips on 2005-11-01
Looks like DNS problems. Please move this thread to the Networking forum or repost there and i'll respond.

Please post the following info in this thread:

1) Router Make & Model
2) Did you buy it or was it provided by the ISP
2) Connection type, Ethernet, USB or Wireless
3) Running in Bridged or Routed mode
4) Country you live in.
5) Your ISP and/or Broadband provider
6) What service are you subscribing to from them
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)

Please provide links where possible to the above questions.

---

### Post by nautilu on 2005-11-01
well:
it's eci b-focus 312+ DSL modem.
it's connection is LAN over DSL (bridged) and not satndard with static ip.
the connection to the PC is LAN with DHCP + NAT and firewall.
that's all i can tell u, cause it works fine in Windows

---

### Post by nautilu on 2005-11-01
another starnge thing happen:
i ran wget and ping commands, the output is in the attached file.
plz take a look

---

### Post by mips on 2005-11-02
Why are you running in bridged mode ? Rather setup the router for 'routed' mode. Let it handle the PPPoE, Login, DHCP, DNS etc

The simply set your pc's up for DHCP & auro dns.

Make sure you are running the latest firmware on your router.

also try:
In the firefox address/URL space type "about:config" , scroll down to network.dns.disableIPV6 = false ,double click this line to change it to true.
In the above do NOT type in any quotes.

---

### Post by nautilu on 2005-11-02
the bridge is for the connection to the ISP not for my LAN, and i can't change it.

i'll check this tweak for firefox, but even if it'll work, what about other programs, like synaptic?

did u check the attachment file?

---

### Post by mips on 2005-11-02
[QUOTE=nautilu]the bridge is for the connection to the ISP not for my LAN, and i can't change it.
did u check the attachment file?[/QUOTE]

Ok, let me see if I understand this correctly.

You have a ADSL router  [http://www.ecitele.com/b-focus/](http://www.ecitele.com/b-focus/)
Your PC connects to it via Ethernet
The router acts as a DHCP & DNS server to the PC
There is NO PPPoE client running on the PC.
So your PC is just configured for DHCP & autoDNS.
So your router is actually in routed mode and not bridged mode if the above is correct.

Check your routers firewall. 
Did you install a firewall on Breezy ?
Some routers like D-Link for example dont work properly with linux (even though windows is fine) and require a firmaware upgrade or other work arounds on linux. So maybe check if there are any firmaware updates available.

Someone else out there has the same problem: [http://www.linuxquestions.org/questions/showthread.php?threadid=289397](http://www.linuxquestions.org/questions/showthread.php?threadid=289397)

By the way, your router has a security problem:  [http://www.datastronghold.com/archive/t15721.html](http://www.datastronghold.com/archive/t15721.html)

---

### Post by mips on 2005-11-02
Look at  [http://mirror.hamakor.org.il/archives/linux-il/06-2005/15777.html](http://mirror.hamakor.org.il/archives/linux-il/06-2005/15777.html)

---

### Post by nautilu on 2005-11-02
[QUOTE=mips]
also try:
In the firefox address/URL space type "about:config" , scroll down to network.dns.disableIPV6 = false ,double click this line to change it to true.
In the above do NOT type in any quotes.[/QUOTE]

i disabled the IPV6 option and IT WORKED!!! now i'm finaly surfing with my Ubuntu

now the question is how do i disable IPV6 for all programs?

---

### Post by mips on 2005-11-02
Double post

---

### Post by mips on 2005-11-02
Did you follow this thread  [http://mirror.hamakor.org.il/archive...005/15777.html](http://mirror.hamakor.org.il/archive...005/15777.html)  ???

You are one of the hardest people to get any feedback out of, so i ask again;

Ok, let me see if I understand this correctly.

You have a ADSL router [http://www.ecitele.com/b-focus/](http://www.ecitele.com/b-focus/)
Your PC connects to it via Ethernet
The router acts as a DHCP & DNS server to the PC
There is NO PPPoE client running on the PC.
So your PC is just configured for DHCP & autoDNS.
So your router is actually in routed mode and not bridged mode if the above is correct.

---

### Post by nautilu on 2005-11-02
[QUOTE=mips]Did you follow this thread  

You are one of the hardest people to get any feedback out of, so i ask again;

[/QUOTE]
sorry for some reason i couldn't get the forum.

the answer is : i did follow the thread you suggested, there's only one problem with it: there's no such thing /etc/modules.conf
but there's /etc/modprobe.d/aliases
where i changed ```
alias net-pf-10 ipv6
``` 
to 
```
alias net-pf-10 off
``` and rebooted
the system catched all the updates but i still can't download anything with synaptic

---

### Post by mips on 2005-11-02
Sorry did not see your post above.

[QUOTE=nautilu]i disabled the IPV6 option and IT WORKED!!! now i'm finaly surfing with my Ubuntu

now the question is how do i disable IPV6 for all programs?[/QUOTE]

Open a terminal and enter:
> mips@box:~$ sudo gedit /etc/modprobe.d/aliases
Password:********


Look for:
> alias net-pf-10 ipv6

Change to:
> alias net-pf-10 off #ipv6

**Save file and reboot.**

---

### Post by nautilu on 2005-11-02
that's exactly what i did

---

### Post by mips on 2005-11-02
Is Synaptic the only thing not working or are there other network apps also not working ?

---

### Post by mips on 2005-11-02
[QUOTE=nautilu]sorry for some reason i couldn't get the forum.

the answer is : i did follow the thread you suggested, there's only one problem with it: there's no such thing /etc/modules.conf
but there's /etc/modprobe.d/aliases
[/QUOTE]

Correct, things change over versions.

---

### Post by nautilu on 2005-11-02
can't say about other progs, and i don't know what i just did but it suddenly began to work.

i ran 
apt-get install -f
got a lot of errors
then: apt-get update
and it worked (didn't work few minutes ago)

---

### Post by mips on 2005-11-02
Funny thing is if it got the updates then it should work.

Maybe just reboot and check if all is OK. Also ensure your repositories are up to date.

---

### Post by nautilu on 2005-11-02
ok it's not the funniest thing.

after my last post i tried another download of a sowtware and it stucked again.

then i ran 
wget 
for the repositorie. it worked fine (as it should) and only then ran synaptic again successfully.

i realy thank you for your time.

---


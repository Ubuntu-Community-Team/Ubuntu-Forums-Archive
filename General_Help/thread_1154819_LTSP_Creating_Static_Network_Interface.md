---
title: "LTSP Creating Static Network Interface"
date: 2009-05-10
forum: General Help
---

### Post by vahnx on 2009-05-10
I'm trying to set up LTSP on my existing Ubuntu install by following the [official Ubuntu guide]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall#Installing%20on%20top%20of%20an%20already%20running%20desktop%20system") but it says *You need to set up one static network interface where you will attach the thin clients, install two packages and run one command. * They only give information on installing the packages, and not setting the static interface. I already have a static IP as 192.168.0.2 and my routers address is 192.168.0.1, so I'm a bit confused on what I'm supposed to do now since it says the thin client should be 192.168.0.1 which is my router.

Do I go to Network Connections and just create a new one with say 192.168.0.5 (isn't being used on my network) and then edit my server file with the IP 192.168.0.5 and restart it and I'll be set to boot?

---

### Post by Peter09 on 2009-05-10
I have not installed this but on reading the documentation it appears to be saying that it expects the server to have two network cards, one normal IP address and one which is not within the IP range of your LAN.

---

### Post by vahnx on 2009-05-10
I actually solved it. Didn't set up any extra Ethernet profiles or anything. All I did to enable this LTSP is I ran those two commands, then /etc/init.d/openbsd-inetd start
to start the server and I was PXE booting!

---


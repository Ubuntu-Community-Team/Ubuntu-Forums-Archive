---
title: "resolv.conf reverts on reboot"
date: 2005-06-27
forum: Desktop Environments
---

### Post by pompeyjohn on 2005-06-27
This is a minor annoyance, but if someone from here can help me to sort it out it would be much appreciated. Whenever I shut down my machine, or reboot it, the resolv.conf file reverts back to 192.1.whatever. All works well again once I have put in my ISPs dns, but it is frustrating having to do this again and again. Problem is, I am not too sure where to start looking in tracking down what is causing this. Any help much appreciated.

Also, super quick question. Can anyone recommended a decent program for getting into (and fixing) corrupt tar.gz files? Thanks again.

John

---

### Post by Arthemys on 2005-06-27
What's probably happening is that whatever DHCP server you have running is issuing out information for the DNS server IP addresses and puts them in there. An example of a DHCP server in most homes is their own router or NAT box.

If you're using static addressing I'm not real sure what could be causing this, it seems unlikely but my guess would be a dhcp server overwriting it each time you ask for an IP address lease.

---

### Post by pompeyjohn on 2005-06-28
[QUOTE=Arthemys]What's probably happening is that whatever DHCP server you have running is issuing out information for the DNS server IP addresses and puts them in there. An example of a DHCP server in most homes is their own router or NAT box.

If you're using static addressing I'm not real sure what could be causing this, it seems unlikely but my guess would be a dhcp server overwriting it each time you ask for an IP address lease.[/QUOTE]

That sounds likely - I am using a Dlink 504t router. Any idea how I could stop it sending out that info. Thanks for your help, it is most appreciated.

---

### Post by Arthemys on 2005-06-28
Check in the manual regarding DHCP settings, I'm not sure in the dlink models where that would be. Or you could try setting your IP to be static, there's no harm in that.

---


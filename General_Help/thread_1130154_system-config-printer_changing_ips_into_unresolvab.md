---
title: "system-config-printer changing ips into unresolvable hostname"
date: 2009-04-19
forum: General Help
---

### Post by bones0 on 2009-04-19
I am running ubuntu 8.04. Today I tried to connect it to my cups server I already use for printing with debian and Windows (XP, Vista). system-config-printer 0.7.8.1 let me connect to the server and everything worked OK until it decided to change the IP-adress into the hostname of the remote cups-server (making ipp://hostname/... out of ipp://ip/...). That hostname isn't resolvable since I don't have an internal DNS. This leads to the problem that trying to print anything from the document viewer makes the whole system firing DNS-queries and the whole gnome desktops is freezing.

I have seen that there is a newer version of this tool in 8.10. Is it fixed there?

Personally I would never change an IP-address into a hostname in a system configuration. Most likely the IP has been entered on purpose. IMHO it's the administrator's decision what he wants to be in there.

Of course it was easy to workaround that problem by editing /etc/hosts. But I don't like to "spoil" my hosts-files.

Regards
    Peter

---

### Post by cariboo on 2009-04-19
I don't get what you mean by spoil your /etc/hosts file, but if you don't won't to edit it, have a look at dnsmasq, it is perfect for smaller networks. Dnsmasq is in the repositories.

Jim

---

### Post by bones0 on 2009-04-19
/etc/hosts has some drawbacks if you have more than one machine. I had some nasty problems with that some time ago. But it's not a real problem now because I have only one active Ubuntu client. The others run windows and are able to access the print server using the IP-Address.

Setting up a DNS is not my problem. I know bind well enough. dnsmasq would need more time because I (currently) don't have the slightest idea what it is and how it works. But I don't want to set up anything like that just because a setup tool is not able to store the information I entered exactly the way I entered it.

Regards
   Peter

---


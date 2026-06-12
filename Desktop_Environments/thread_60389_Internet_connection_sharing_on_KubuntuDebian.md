---
title: "Internet connection sharing on Kubuntu/Debian"
date: 2005-08-27
forum: Desktop Environments
---

### Post by vedro on 2005-08-27
ellow

I have setted up a server which I will use for some server activities (apache, ftp) and for sharing the internet connection to other computers in the house. So, the machine has two ethernet cards, switch..etc.. 
eth0 is connected to dsl modem
eth1 for passing the internet connection

So now, how/what should I configure in the Kubuntu, that it will work?

have a nice day,
vedro

---

### Post by incinerator on 2005-08-27
First the basics:

On the server:
sudo apt-get install ipmasq

I haven't used this package for a while since my gateway box has been running OpenBSD for a while now. IIRC you should get asked some questions during installation of this package and it will get configured.

On the client:
You can go with static setups as described in the [wiki](https://wiki.ubuntu.com/ShareInternetConnection)

However, I don't like the way this wiki page deals dns, I would rather do:

sudo apt-get install dnsmasq
(on the server byraway)

That is a proxy dns server, you may need to read its man pages in order to find out how to configure it, but it is quite easy. Once that thing is running, you can adjust to dns server setting for the client to use your gateway as dns server.

However, dnsmasq also comes with an integrated dhcp server. Once you set it up propery, which is not to difficult when reading the man pages (iirc there many examples in the sample config file, too), client side configuration becomes unneccessary as you can use dhcp (in ms-speak: "configure internet automatically") on the clients to get their network interfaces configured.

Now, if I only could be bothered to re-write that wiki page *ggg*.

Regards,
Dominik

---


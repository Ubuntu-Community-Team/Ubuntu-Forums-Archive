---
title: "Installing a human Linux distro on an Inspiron 2500"
date: 2009-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by searchesend on 2009-05-19
I've been trying to breathe life into a Dell Inspiron 2500 (128MB / 700Mhz / 40 GB) but I can't get the installer to connect to the network. The error message is 'network autoconfiguration failed; your network is probably not using DHCP protocol ...' I've tried the installation with an Edimax wireless PCMCIA and an Edimax Ethernet PCMCIA to no avail.
I'm looking for a work around this so I can get going on the minimal install (following a guide that supposedly works on low RAM systems), but if there's another OS that should work and will recognise the Edimax hardware I'd like to know.
Puppy Linux runs brilliantly in RAM but I can't get it to connect to the internet?
Sorry if this is posted under the wrong section - my computer knowledge is crap.

---

### Post by coffeeaddict22 on 2009-05-21
Ubuntu needs a minimum of 256 MB, Xubuntu would be the lightest pure Ubuntu distro and you might get away with 128 MB [- have a look here.]("http://www.xubuntu.org/get")  The problem you've got is the lightweight distros will only have basic drivers, and if that doesn't suit your network card you're in for a ride.  
You're probably better going for a true lightweight distro, and I've got no experience with them but Puppy certainly gets mentioned as a good one.  The driver for your card will almost certainly be an add on.

---

### Post by searchesend on 2009-05-21
The minimal install CD I'm using purports to work on 64MB RAM systems. The thing that's really getting my goat is I can connect using a newer PC, using the very same PCMCIA card and same installation CD? If all the drivers being used are on the install CD, what's different on the 2 computers that makes one successful? I can type out a

cat /var/log/syslog|grep -i eth0

for both computers if that's of any use?

---

### Post by coffeeaddict22 on 2009-05-22
Do ```
lshw -C network
``` when you've got the card working; that'll give you the driver you need.  Run it when you've got the new install running, and see what's happened.

---

### Post by searchesend on 2009-05-22
Thanks for your help, I tried lshw but it doesn't work on this version of BusyBox. After trying to make it work for 3 days I think I'll just upgrade the RAM and try a bigger install CD. Thanks again!

---

### Post by ugm6hr on 2009-05-22
Minimal install won't work with wifi.

It should work with wired ethernet; don't know why it works on one and not the other.

Another option is to install  Xubuntu using AlternateCD, then strip XFCE etc, and add LXDE.  See the link re: Ubuntu+LXDE for details.  I haven't tried this with Jaunty, but no reason it shouldn't work.

---

### Post by searchesend on 2009-05-27
Hey ugm6hr, I was trying the install using a wired ethernet connection to a PCMCIA card. During the install it correctly identifies the card type as Realtek ... etc but it won't connect on this particular computer but works fine using the same connection to the same PCMCIA card on different PCs? I've just upgraded my RAM to 384MB but this hasn't helped. I'll try a normal Xubuntu install and see if that works. Can you shed any light on what the problem could be? Thanks

---

### Post by ugm6hr on 2009-05-27
> **searchesend said:**
> Hey ugm6hr, I was trying the install using a wired ethernet connection to a PCMCIA card. During the install it correctly identifies the card type as Realtek ... etc but it won't connect on this particular computer but works fine using the same connection to the same PCMCIA card on different PCs? I've just upgraded my RAM to 384MB but this hasn't helped. I'll try a normal Xubuntu install and see if that works. Can you shed any light on what the problem could be? Thanks

Extra RAM won't help ethernet connection problems.

If the same install CD detects the PCMCIA device with a different laptop, there must be a BIOS setting, or a hardware problem with that particular laptop.

---

### Post by searchesend on 2009-05-29
I guess the minimal install just doesn't like something about the Dell Inspiron 2500. I've successfully installed Xubuntu and it's working great. Thanks again to all for your help.

---

### Post by ikokol on 2009-07-20
> **searchesend said:**
> I guess the minimal install just doesn't like something about the Dell Inspiron 2500. I've successfully installed Xubuntu and it's working great. Thanks again to all for your help.
Which resolution you got the highest? I'm having several problems configurating xorg.conf file on my Dell i2500!

Also, I can't get my wireless usb to work... As you see I'm pretty newbie, but anyways I'm trying my best to fix it.

Help needed! Thanks in advance!

---

### Post by uconvert on 2009-07-20
I had a similar problem with a Compaq Presario 900, the earlier Ubuntu distros worked great, but with every distro since Feisty 7.04, the PCMCIA wireless has been broken. 

I always ended up reinstalling 6.06 LTS, but support for that just ended. 

I got PCLOS 2009 working on it, but I don't like KDE.

---

### Post by rgb1701 on 2009-07-20
> **searchesend said:**
> I've been trying to breathe life into a Dell Inspiron 2500 (128MB / 700Mhz / 40 GB) but I can't get the installer to connect to the network. The error message is 'network autoconfiguration failed; your network is probably not using DHCP protocol ...' I've tried the installation with an Edimax wireless PCMCIA and an Edimax Ethernet PCMCIA to no avail.
I'm looking for a work around this so I can get going on the minimal install (following a guide that supposedly works on low RAM systems), but if there's another OS that should work and will recognise the Edimax hardware I'd like to know.
Puppy Linux runs brilliantly in RAM but I can't get it to connect to the internet?
Sorry if this is posted under the wrong section - my computer knowledge is crap.

For the memory/CPU you describe, the hands-down best Linux distro is PuppyLinux

[http://www.puppylinux.org/downloads/official-releases/latest-production-version](http://www.puppylinux.org/downloads/official-releases/latest-production-version)

...at least until Xubuntu goes to LXDE and really trims down ;)

---


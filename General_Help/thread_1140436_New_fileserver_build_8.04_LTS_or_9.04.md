---
title: "New fileserver build: 8.04 LTS or 9.04?"
date: 2009-04-27
forum: General Help
---

### Post by sej7278 on 2009-04-27
I'm building a new fileserver (for home) well rebuilding an old one really, Pentium4 class hardware so no fancy new hardware support needed.

As I don't really want to reinstall the OS until I buy a completely new box in a couple of years or until the next LTS is released, I was looking at the supported lifecycle: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) and [http://www.markshuttleworth.com/archives/146](http://www.markshuttleworth.com/archives/146)

It seems that 8.04 LTS (I need Desktop to run my scanner with xorg, Server won't do, and I'd like it to be a backup desktop machine anyway) will be unsupported after April 2011 and 9.04 will be unsupported six months earlier.

So I'm trying to decide if its worth using a year older 8.04 LTS and getting 6 months more support, or go with the more up-to-date 9.04

I'm normally a RedHat guy, but getting fed up with CentOS 5.3 and pretty impressed with the 8.04.2 Server I've been using lately for work. RHEL5 goes EOL in 2014, but realistically it will get no new development after April 2011, just security patches, by which time it will already be 4 years old with a 2.6.18 kernel.

So what do you think - 8.04 for another 2 years, or 9.04 for 18 months? What are the major differences other than kernel version 2.6.24 vs 2.6.28?

The server will need to do/run the following things:

* Epson RX425 scanner/printer (so PIPS, CUPS and iScan);

* Handle JFS partitions (CentOS needs a non-RHEL kernel for this);

* Run NFSv4;

* Handle mode 0 NIC bonding;

Plus the usual Samba server, sshd, iptables etc.

Firewire support that actually works would be nice too, RedHat hasn't had working 1394a in years!

I may even want it to run a Hauppauge WinTV Express PCI card via tvtime and mencoder - I assume codecs aren't an issue like with RedHat?

Do LTS releases maintain kernel compatibility like RedHat - i.e. is it stuck with a 2.6.24 kernel forever?

What about upgrades - can you "apt-get dist-upgrade" from 9.04 to 9.10 in October or does it break horribly like Fedora?

Cheers from a potential RHEL escapee :lolflag:

---

### Post by matt the destroyer on 2009-04-27
There are two reasons to use a newer version:

[LIST=1]
[*]New software
[*]New hardware
[*]New eye candy.
[/LIST]
Otherwise, always go with the stable branch (this my professional opinion as a systems administrator).

For one, server software does not change that quickly, for the desktop (OO.o, firefox, etc ) there are usually backports available.  For two, it should not be a problem unless your scanner is new. Three should not be a concern on a machine as old as yours.

For me, codecs were easier with 8.04.  Be sure to read the restricted formats page in the wiki.

You can update the kernels, but you need to specify them.

Personally, my p4 would still have warty if they had not eol'd it.

Take care,
mat

EDIT: JFS should work out of the box in both releases.

EDIT EDIT:  It sounds like you are the kind of person who will get more out of debian.

---

### Post by sej7278 on 2009-04-27
> **matt the destroyer said:**
> 
EDIT EDIT:  It sounds like you are the kind of person who will get more out of debian.

well i'm very impressed with debian 5, but after the nightmare that was trying to support debian4 at work for three years, i think i'm done with that distro - also not many closed-source vendors support it, everyone like epson support ubuntu and to some degree rhel.

i'm also leaning towards 8.04, as it gives me two years from now, by which time i'd have probably got fed up and gone onto rhel6, or bitten the bullet and bought new hardware.

good news about jfs by the sounds of it, although i could be a maniac and try ext4 (is that in 9.04, i assume not 8.04?)

---

### Post by sefs on 2009-04-27
Out of an abundance of laziness when it comes to servers I like to go with LTS versions as I only need to update them every x years when the LTS expires :)

---

### Post by sej7278 on 2009-04-27
> **sefs said:**
> Out of an abundance of laziness when it comes to servers I like to go with LTS versions as I only need to update them every x years when the LTS expires :)

well yes exactly, *normally*, but my point is that as of now 8.04 only has 2 years left in it - only 6 months more than 9.04

---

### Post by Iowan on 2009-04-27
I usually stick with LTS for servers, too.  There is a direct upgrade (or so I've read) between LTS versions.  Jaunty would need to upgrade to 9.10 (Karmic Koala), then 10.04 (next "scheduled" LTS).

---

### Post by matt the destroyer on 2009-04-27
Wow.  That is the first time I have _ever_ heard somebody complain about supporting Debian.  I have a few boxes: http server, db server, mail server, file server, my workstation and the machine that makes the backups (nothing serious but still enough to get your feet wet).  Except for my workstation, they all did the sarge->etch->lenny upgrade cycle and I never once had any issue with any of them.  For me, debian is truly "install and forget" for every task I have ever tried.

Seriously, though, for all intents and purposes, ubuntu is debian with cosmetics on.  If you hate debian, you won't like ubuntu.

Our workstations are Ubuntu because, honestly, users get scared when they see a text boot like in debian.  Administration and support is exactly the same, though: point apt at a local repository and set up a cron job to update from there, ldap user auth and ssh listening just in case I need to do something, and that is it.  

For updating, in Ubuntu in the past updating between non-LTS versions has sometimes been problematic.  However, cannonical, wary of its server customers, always makes the LTS to LTS updates smoother.  Debian is better with upgrades, though.

As for proprietary software, I am curious what runs in Ubuntu that does not run in Debian.  I checked, and the driver for the printer you mentioned is part of Gutenprint, so it is in both debian and ubuntu.  Heck, even Oracle will run on debian.  What are you looking for?

---

### Post by sefs on 2009-04-27
> **Iowan said:**
> I usually stick with LTS for servers, too.  There is a direct upgrade (or so I've read) between LTS versions.  Jaunty would need to upgrade to 9.10 (Karmic Koala), then 10.04 (next "scheduled" LTS).

This is good news!  I now feel warm and toasty in my laziness when it comes to this matter of server upgrades.

---

### Post by Wiebelhaus on 2009-04-27
> **matt the destroyer said:**
> There are two reasons to use a newer version:

[LIST=1]
[*]New software
[*]New hardware
[*]New eye candy.
[/LIST]
Otherwise, always go with the stable branch (this my professional opinion as a systems administrator).

For one, server software does not change that quickly, for the desktop (OO.o, firefox, etc ) there are usually backports available.  For two, it should not be a problem unless your scanner is new. Three should not be a concern on a machine as old as yours.

For me, codecs were easier with 8.04.  Be sure to read the restricted formats page in the wiki.

You can update the kernels, but you need to specify them.

Personally, my p4 would still have warty if they had not eol'd it.

Take care,
mat

EDIT: JFS should work out of the box in both releases.

EDIT EDIT:  It sounds like you are the kind of person who will get more out of debian.

I agree with this post 100% And the edits.

---

### Post by sej7278 on 2009-04-27
ok so now its a toss-up between ubuntu 8.04.2 desktop and debian 5.0.1 !!!

the lts-to-lts upgrade sounds good, as 10.04 lts is due in a year or so iirc.

how good is debian with multimedia though - as i might use it as a backup desktop machine too, and i might be recording the odd tv show using a wintv card, normally i'd think if ubuntu has the packages then debian does, but i don't know about multimedia (nvidia, flash, mplayer, tvtime etc.)

---

### Post by eeperson on 2009-04-27
> **sej7278 said:**
> well i'm very impressed with debian 5, but after the nightmare that was trying to support debian4 at work for three years, i think i'm done with that distro - also not many closed-source vendors support it, everyone like epson support ubuntu and to some degree rhel.


Drivers support for hardware is added to the kernel.  In general, hardware manufacturers do not support specific distributions they support Linux as a whole.

You were probably having hardware issues because of the older kernel in Debian 4.

---


---
title: "Immediate help required"
date: 2009-01-23
forum: General Help
---

### Post by bconover on 2009-01-23
So, I wanted to have a nice GUI config tool for my firewall. I installed Guarddog, from the Repos...

AND IT BROKE MY ******* INTERNET. I CAN NOT CONNECT.

It connects to my router, but BLOCKS ALL INTERNET CONNECTIONS.

Tell me, why the HELL is something that does that, after only running the program once, IN THE FREAKING REPOS? So much for ******* trust.

I love Linux and all, but this just pisses me off. No, I would never switch back to Windows, but Ubuntu is kind of killing my Linux experience with this.

Please, PLEASE help me fix this, ASAP. I was in the middle of some important work when my Internet broke on my one machine, and am already infuriated by the fact that I'm going to have to start it all again. I need this fixed right away!

I'm running Ubuntu 8.10 (obviously I'm posting this from a different computer though).

I'm sorry if I seem overly angry, but I'm really getting tired of some of this BS.

---

### Post by bconover on 2009-01-23
Please help.

---

### Post by bgerlich on 2009-01-23
Uninstall what you have installed and just in case run this script:
```

#!/bin/sh
# 
# rc.flush-iptables - Resets iptables to default values. 
# 
# Copyright (C) 2001  Oskar Andreasson &lt;bluefluxATkoffeinDOTnet&gt;
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; version 2 of the License.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program or from the site that you downloaded it
# from; if not, write to the Free Software Foundation, Inc., 59 Temple
# Place, Suite 330, Boston, MA  02111-1307   USA

#
# Configurations
#
IPTABLES="/sbin/iptables"

#
# reset the default policies in the filter table.
#
$IPTABLES -P INPUT ACCEPT
$IPTABLES -P FORWARD ACCEPT
$IPTABLES -P OUTPUT ACCEPT

#
# reset the default policies in the nat table.
#
$IPTABLES -t nat -P PREROUTING ACCEPT
$IPTABLES -t nat -P POSTROUTING ACCEPT
$IPTABLES -t nat -P OUTPUT ACCEPT

#
# reset the default policies in the mangle table.
#
$IPTABLES -t mangle -P PREROUTING ACCEPT
$IPTABLES -t mangle -P POSTROUTING ACCEPT
$IPTABLES -t mangle -P INPUT ACCEPT
$IPTABLES -t mangle -P OUTPUT ACCEPT
$IPTABLES -t mangle -P FORWARD ACCEPT

#
# flush all the rules in the filter and nat tables.
#
$IPTABLES -F
$IPTABLES -t nat -F
$IPTABLES -t mangle -F
#
# erase all chains that's not default in filter and nat table.
#
$IPTABLES -X
$IPTABLES -t nat -X
$IPTABLES -t mangle -X

```
Save the code to a file, run chmod +x filename.sh , and run it: sudo ./filename.sh

---

### Post by bconover on 2009-01-23
Calling it script.sh:

$ sudo ./script.sh
sudo: Unable to execute script.sh: No such file or directory

But it is there!

I did this instead:

sudo sh script.sh

And got a whole lot of errors about not finding "iptables" or something. But the script did seem to execute.

---

### Post by bgerlich on 2009-01-23
Have you ran: sudo chmod +x script.sh  
?

---

### Post by bconover on 2009-01-23
> **bgerlich said:**
> Have you ran: sudo chmod +x script.sh  
?

Yes

---

### Post by bgerlich on 2009-01-23
type in "locate iptables" and change the location in the line 24 of the script.

---

### Post by bconover on 2009-01-23
> **bgerlich said:**
> type in "locate iptables" and change the location in the line 24 of the script.

What? I get a whole lot of results... what do I change it to?

---

### Post by bgerlich on 2009-01-23
I am certain it should be "/sbin/iptables", check if you have iptables installed: sudo apt-get install iptables

---

### Post by Circus-Killer on 2009-01-23
cant help with current problem. but for future reference, i use **firestarter** instead of gaurddog. its probably the easiest firewall gui i've come across in linux.

---

### Post by bconover on 2009-01-23
> **bgerlich said:**
> I am certain it should be "/sbin/iptables", check if you have iptables installed: sudo apt-get install iptables

I do have /sbin/iptables... sudo apt-get confirms this.

---

### Post by bgerlich on 2009-01-23
If you don't and the package is not in cache (doesn't install) you can download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by bconover on 2009-01-23
When I do sudo sh script.sh, I get lines like:

: not found20:
: not found25:
: not found29: /sbin/iptables

And a lot of other lines like that, most containing /sbin/iptables, but some not.

---

### Post by bconover on 2009-01-23
apt-get says I have iptables.

Also, browsing through /sbin/iptables shows a file called iptables.

---

### Post by bgerlich on 2009-01-23
Check if there were no errors while copying/pasting  the script. If that fails you can type in the commands by hand, go into super user mode (sudo -i) and type in all the commands from the script (lines starting with $IPTABLES), exchanging the $IPTABLES to iptables

---

### Post by bconover on 2009-01-23
Disabling firewall in guarddog doesn't seem to fix anything!

What the heck is going on here?

---

### Post by bconover on 2009-01-23
How do I uninstal guarddog? I uses sudo apt-get remove, but even after "removing" it it is still working?

---

### Post by bconover on 2009-01-23
Okay, guarddog appears gone for good. Script still isn't working.

---

### Post by bconover on 2009-01-23
WAIT! CAN IT BE!

HALLELUJAH! The internet works again!

Seems when I used sudo apt-get remove guarddog the first time it didn't fully kill guarddog. But 2 times the charm, I guess ;)

Thanks for the help! Guess that is why the script wasn't working?

As a final note:

I noticed, as I removed guarddog this time, that a little message showed up in the console that said "Stopping iptables firewall". Was this perhaps what was causing the trouble?

Well, I sure as heck am never installing Guarddog again :P Once again, thanks for your support. While this event has left me somewhat distrusting of the repos (:mad:), at least I know that the Ubuntu support will always be good! :D

---


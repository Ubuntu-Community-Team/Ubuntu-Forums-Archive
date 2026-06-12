---
title: "Dansguardian and Firehol Proxy Problems"
date: 2006-07-19
forum: Desktop Environments
---

### Post by andytof47 on 2006-07-19
Hi I followed this guide to the letter and although it kind of works it kind of doesn't.
What i mean is that it blocks all browser traffic, but lets other things like GAIM, Email and UPDATES thru.

Any ideas?

(this was the HOWTO i followed)
Dansguardian does an outstanding job of web content filtering to protect from rubbish on the internet. This howto is a synthesis of information taken from:
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)

Setting up Dansguardian using Tinyproxy and Firehol on Ubuntu/Edubuntu

1. Ensure "universe repository" is activated and install packages:
sudo apt-get update
sudo apt-get install dansguardian tinyproxy firehol

Note: will probably need to reinstall dansguardian to overcome clamav config errors.

2. Edit: sudo gedit /etc/dansguardian/dansguardian.conf

a) Add comment (#) to:
#UNCONFIGURED

b) Turn off virus checking (if not wanted):
virusscan=off

c) Check that the following are set:
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

d) Save & exit.

e) Run:
sudo dpkg-reconfigure dansguardian

3. Edit: sudo gedit /etc/firehol/firehol.conf

Add all of the following at the start of the document:

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept

Note: will need to remove "interface any world . . ." further on in the document.

4. Edit: sudo gedit /etc/default/firehol

START_FIREHOL=YES

This is to allow restarting of the firewall.

5. Edit sudo gedit /etc/tinyproxy/tinyproxy.conf

Change/add the following lines (by scrolling through the document):
User root
Group root
Port 3128
ViaProxyName "tinyproxy"

6. Restart each program:

sudo /etc/init.d/tinyproxy restart
sudo /etc/init.d/firehol restart
sudo /etc/init.d/dansguardian restart

7. Dansguardian should now be operational blocking objectional sites using any browser! 

ALSO I WANT TO APOLOGISE FOR POSTING IN THE HOW TO SECTION!!!!!](*,)

---

### Post by tonhou on 2006-07-26
Did you check back at the original howto - I made some suggestions there. Also the other poster who said he had this problem has it working fine now. Apparently he had missed something when setting it up.

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)

--Tony

---


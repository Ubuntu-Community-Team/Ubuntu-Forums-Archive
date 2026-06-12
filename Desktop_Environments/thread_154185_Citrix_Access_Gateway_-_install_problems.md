---
title: "Citrix Access Gateway - install problems"
date: 2006-04-02
forum: Desktop Environments
---

### Post by olecg on 2006-04-02
Hi,

I really can't say if Ubuntu is the real deal for me, because I have only been using Linux for about 24hrs and never ever before touched anything in this world.
I want to see if I'm able to swap my XP with Ubuntu  and use it at work and home.
After about 10 hours reading different stuff, I have been able to install the 5.10 release, install the Java plugin for Firefox anf even installed the regular CItrix ICA-client. I can now use my published applications form the internet side. We're using WebInterface and Secure Gateway.

Instead of using only publis app's all the time, I REALLY want some kind of VPN access to work. I have the CheckPoint option, but all articles I've read so far states I should drop the try. We also have a universal SLL VPN gateway installed: Citrix Access Gateway. Cool! The loginpage on the gateway instructs me to download the file, do some chmod to it, go SU and install it. Here is the problem. When I dig into the script, I see that the script checks for $DISTRIBUTION. The script carries on assuming it is Red Hat, Fedora, Mandrake and another one, NOT Deboan or Ubuntu. So here is my problem:

I know where the install fails and here is a pasting of the file:

install -s -m 0755 ${TMP}/net6vpnd /usr/sbin
install -m 0755 ${TMP}/net6vpnd.${DISTRIBUTION}.init /etc/init.d/net6vpnd
install -s -m 0755 ${TMP}/net6vpn /usr/bin
install -m 0644 ${conffile} /etc/net6vpn.conf

The second line pasted above fails. I think this has something to with that the $DISTRIBUTION variable is not set a little earlier in the script. After reading some more here in this forum, my guess is that this install command should do something like putting the net6vpnd (deamon) in a file or catalog so it starts automatically when reloading. Is this true ?
The result after running these four lines is that I do get the net6vpnd in the /usr/sbin catalog. I do get the net6vpn in the /user/bin catalog and the net6vpn.conf is located in the /etc catalog. The only file missing is the net6vpnd in the /etc/init.d catalog. Because of very poor knowledge I even don't know if its supposed to be a file in there or a link pointing to the /usr/sbin catalog.
If someone could give me a tip to do this manually, I will be very happy!!!

BUT, I can say that the result is that I start the net6vpnd in its own terminal-windowand just leaves it there. In another window I do the net6vpn --login command. Put in username and PW and voila! it gets me connected to work. At the same time I monitor my FIrewall and the real-time-monitor on the Access Gateway, and I'm given an ip from a pool I have setup. So far so good, but its not working. Even if I'm successful in authenticating, nothing happens, ie. my "traffic" isn't going in the direction I want. When trying to access a private IP inside my company's network, it just get routed to the internet. But this is another issue and I should start with getting the net6vpnd running by itself.

Any help is highly appreciated, and if I only can get connected to work, I really think my XP box will go down the drain. Remember: only about 24hrs since I touched Linux for the first time in my life!

olecg

---

### Post by olecg on 2006-04-06
[QUOTE=olecg]
I know where the install fails and here is a pasting of the file:

install -s -m 0755 ${TMP}/net6vpnd /usr/sbin
install -m 0755 ${TMP}/net6vpnd.${DISTRIBUTION}.init /etc/init.d/net6vpnd
install -s -m 0755 ${TMP}/net6vpn /usr/bin
install -m 0644 ${conffile} /etc/net6vpn.conf
[/QUOTE]

Before these install commands, the script unpacked everything to a /tmp/.net6 catalog. I just put EXIT in the script after the unpacking, so I was able to see what went in the tmp-catalog.
There were some files, e.g. net6vpnd.mandrake.init and the others.
I just played around a bit, trying the different files and cp'ed them to the /etc/init.d/ catalog as net6vpnd. All of them failed because of some function-calls, byt by looking in other stuff at the .../init.d/ catalog, I saw that they all called another library with functions. So i just replaced the net6vpnd with the correct function call, and the net6vpnd starts. I can now login with net6vpn, and when I monitor the connection, everything seems to be fine.

There is only one problem; Its not working. All attempts trying to reach some of the resources behind the access gateway, will result in being routed to the internet instead of through the "tunnell". I have read some and understand that the net6vpn should "listen" to traffic going to the specific subnets and route it to the correct gateway. That doesn't happen.
It should not alter any routing tables according to the doc.

Any guess?

rgs.
olecg

---

### Post by SysKoll on 2006-08-24
I have a similar problem. After modifying the citrixvpn-linux-2.4-i386.sh script, I was able to extract the required net6vpn client and net6vpnd daemon executables, as well as the /etc/net6vpn.conf file.

However, when I try to start the net6vpn client, I get an error:

net6vpn: failed to parse config.
net6vpn: failed to parse config file.

olecg, have you been able to solve this problem?

---

### Post by Bengaul on 2007-03-16
I would like to bump this, as I am also having difficulties! This is my output:

ben@bengaul:~/Desktop$ sudo net6vpn
net6vpn: net: socket: socket hung up.
net6vpn: failed to connect to daemon. [Operation now in progress]
net6vpn: failed to do network io.
net6vpn: failed to get connection id.

Any help?

---

### Post by Ac1D on 2007-12-12
I have the same problem, has someone already found a solution for this?

---


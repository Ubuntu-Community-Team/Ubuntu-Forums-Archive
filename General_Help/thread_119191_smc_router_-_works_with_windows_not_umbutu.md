---
title: "smc router - works with windows not umbutu"
date: 2006-01-18
forum: General Help
---

### Post by robswi on 2006-01-18
I've just installed obuntu on my a8n-e athlon 3200 machine and I'm having some weird internet/network issues.  I'm brand new to Linux so any suggestions need to be geared to someone with almost no knowledge of how to do anything with a Linux system.

It may just be that my older SMC router is a little bit flaky and windows copes with it better but, mostly I don't have any problems either connecting to the internet or using the network with windows.  With ubuntu I have found that I can connect to the internet if I go to an ip # but not a url??  That applies when trying to connect with Firefox or pinging out.

However, if I plug the computer directly to the cable modem it works as expected.


Any suggestions?

Also, I've downloaded Firefox 1.5 but can't figure out how to install the upgrade.:( 

thanks

Rob

---

### Post by shakin on 2006-01-18
Sounds like your router isn't providing correct DNS servers. Check to see what they are by going to System->Administration->Networking and clicking on the DNS tab.

There should be at least one IP in the DNS Servers box. Make sure these IPs match your Windows DNS server configuration. If you don't have any DNS servers listed you can either use the ones listed in Windows or plug your computer directly into the modem and see what shows up when the network is working. Copy those servers and enter them again when you put the router back in place. You may also be able to use your router's IP as your DNS server, but that functionality depends on if the router supports it.

As for Firefox 1.5, either run the normal Linux installer and select a custom installation directory (I chose /opt/firefox) or install it with [Klik](http://klik.atekon.de/).

If you want to use klik you must first install it by running the following line in a terminal:

```

wget klik.atekon.de/client/install -O -|sh

```

Restart your browser and go to [the klik web site](http://klik.atekon.de/). Right at the top is a Firefox 1.5 link. Click the link and klik will install Firefox 1.5 and drop an icon onto your desktop.

---

### Post by stream303 on 2006-01-19
[QUOTE=robswi]
With ubuntu I have found that I can connect to the internet if I go to an ip # but not a url??  That applies when trying to connect with Firefox or pinging out.

However, if I plug the computer directly to the cable modem it works as expected.
[/QUOTE]

Hmm. what does your /etc/resolv.conf show?

I'll bet Ubuntu's dhclient is looking at the DNS server inside your router and not your isp's nameservers.  Easy fix, but let's look at /etc/resolv.conf first...

---

### Post by nocturn on 2006-01-19
[QUOTE=robswi]I've just installed obuntu on my a8n-e athlon 3200 machine and I'm having some weird internet/network issues.  I'm brand new to Linux so any suggestions need to be geared to someone with almost no knowledge of how to do anything with a Linux system.

It may just be that my older SMC router is a little bit flaky and windows copes with it better but, mostly I don't have any problems either connecting to the internet or using the network with windows.  With ubuntu I have found that I can connect to the internet if I go to an ip # but not a url??  That applies when trying to connect with Firefox or pinging out.
[/QUOTE]

This means your DNS is not being set up correctly.  Are you using DHCP?

---

### Post by NullPointer_ on 2006-01-19
Please help!

I have Paradyne 6212 ADSL modem as router. Device eth0 is fully configred via DHCP sever of the router.

WindowsXP has no problems with network or internet access using the same settings.

Ubuntu 5.10: all hosts are resolved as 1.0.0.0 in any application, but FireFox works fine after disabling ipv6-dns usage in about:config.
Commands "ping", "host" do work in a proper way. After using "host" command dns record is cached and host would be resolved OK.

> [SIZE="1"]np@NullPointer:~$ telnet
telnet> open umail.ru 25
Trying 1.0.0.0...

np@NullPointer:~$ host umail.ru
umail.ru has address 195.34.32.101
;; Warning: Message parser reports malformed message packet.
np@NullPointer:~$ telnet
telnet> open umail.ru 25
Trying 195.34.32.101...
Connected to umail.ru.
Escape character is '^]'.
220 umail.ru ESMTP CommuniGate Pro is glad to see you!
QUIT
221 umail.ru CommuniGate Pro SMTP closing connection
Connection closed by foreign host.
np@NullPointer:~$[/SIZE]

I have disabled ipv6 fully (even removed ipv6.ko as described in WiKi and HOWTOs). No luck, it still keeps resolving hosts as 1.0.0.0.. :(

Is it possible to configure resolver somehow to make it work correctly? It requests IP # in ipv6 "A.A.A.A" format but MUST request in ipv4 "A" format.

PS: resolver.conf has only "nameserver 192.168.1.1" string in it (192.168.1.1 - address of router, it's OK).

---

### Post by solkar_saruman on 2006-01-19
I solved this problem after some time looking around. My solution is to put correctly your dns servers direction. I had 192.168.1.1 (the address of my router) set as default DNS. 

I changed it by my prefered DNS and now works great. 

They're stored in /etc/resolv.conf

Hope this may help you.

---

### Post by robswi on 2006-01-19
Thanks for all the help.  I went into my router admin through firefox and did a renew and that seems to have done it.  Haven't tackled the update of Firefox yet, but that's next on my agenda.

Thanks again

Rob

---

### Post by robswi on 2006-01-19
[QUOTE=shakin]

As for Firefox 1.5, either run the normal Linux installer and select a custom installation directory (I chose /opt/firefox) or install it with [Klik](http://klik.atekon.de/).

If you want to use klik you must first install it by running the following line in a terminal:

```

wget klik.atekon.de/client/install -O -|sh

```

Restart your browser and go to [the klik web site](http://klik.atekon.de/). Right at the top is a Firefox 1.5 link. Click the link and klik will install Firefox 1.5 and drop an icon onto your desktop.[/QUOTE]

I ran the line.  Got the message "Your /etc/fstab isn't set up to use cmg files. run /home/rob/klik-cmg-install-root as root"

I did that, restarted Firefox, went to Klik and kliked on the Firefox1.5 icon and got "Please install ar in order to use klik"

Can someone tell me how to do that.  I've tried searching for ar without much luck . . . .

Rob

---

### Post by NullPointer_ on 2006-01-19
[QUOTE=solkar_saruman]...
I changed it by my prefered DNS and now works great.[/QUOTE]
This is right solution, but it's not acceptable. Resolver MUST work properly and user _should not_ set real dns server's address. Thx anyway.

Any other ideas?.. :???: :(

---

### Post by robswi on 2006-01-19
[QUOTE=robswi]Thanks for all the help.  I went into my router admin through firefox and did a renew and that seems to have done it.  Haven't tackled the update of Firefox yet, but that's next on my agenda.

Thanks again

Rob[/QUOTE]

Whoops, not quite solved.  I don't really want to have to renew my router every time I reboot which seems to be necessary at the moment.  I tried going in to network settings - dns - dns servers and adding the 2 possible settings from my router config, but when I reboot it just reverts back to my router ip???

Any help?

Rob

---

### Post by NullPointer_ on 2006-01-19
[QUOTE=robswi]...but when I reboot it just reverts back to my router ip???

Any help?[/QUOTE]

Here: [http://www.ubuntuforums.org/showthread.php?t=11544](http://www.ubuntuforums.org/showthread.php?t=11544)

---

### Post by robswi on 2006-01-19
[QUOTE=NullPointer_]Here: [http://www.ubuntuforums.org/showthread.php?t=11544](http://www.ubuntuforums.org/showthread.php?t=11544)[/QUOTE]

Thanks but when I try to follow the instructions there and enter "/etc/resolv.conf" or rather " sudo /etc/resolv.conf" I get "command not found" which I assume means there is some other utility that isn't installed automatically by ubuntu.  It would be good to know how to get the bulk of them (missing utilities or whatever they are called in linux) all installed . . . . but at least what is the process to allow me to use this one.

Thanks

Rob

---

### Post by stream303 on 2006-01-20
[QUOTE=robswi]Whoops, not quite solved.  I don't really want to have to renew my router every time I reboot which seems to be necessary at the moment.  I tried going in to network settings - dns - dns servers and adding the 2 possible settings from my router config, but when I reboot it just reverts back to my router ip???

Any help?

Rob[/QUOTE]

No problem since you know what your real nameservers are.  Just edit

**/etc/dhcp3/dhclient.conf** 
 (from the command line: sudo gedit /etc/dhcp3/dhclient.conf)

and right before the line that starts with "request" add this line (using your real nameserver addresses of course)

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**

Just separate the addresses with a comma and don't forget the semicolon at the end.

Now, just bring your ethernet interface down and up again: (or reboot but this is more elegant)

sudo ifdown eth0
sudo ifup eth0

This should help!

---

### Post by nocturn on 2006-01-20
[QUOTE=robswi]Whoops, not quite solved.  I don't really want to have to renew my router every time I reboot which seems to be necessary at the moment.  I tried going in to network settings - dns - dns servers and adding the 2 possible settings from my router config, but when I reboot it just reverts back to my router ip???

Any help?

Rob[/QUOTE]

It reverts back to your router IP because you are using DHCP and your router says it is the primary DNS server.  You could use a static IP and that should fix it.

The issue is that your router is not working properly as a DNS server.

---

### Post by NullPointer_ on 2006-01-21
Ppl, please help. The problem is described in my earlier posts in this thread, and the problem still present.

---

### Post by robswi on 2006-01-25
[QUOTE=stream303]No problem since you know what your real nameservers are.  Just edit

**/etc/dhcp3/dhclient.conf** 
 (from the command line: sudo gedit /etc/dhcp3/dhclient.conf)

and right before the line that starts with "request" add this line (using your real nameserver addresses of course)

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**

Just separate the addresses with a comma and don't forget the semicolon at the end.

Now, just bring your ethernet interface down and up again: (or reboot but this is more elegant)

sudo ifdown eth0
sudo ifup eth0

This should help![/QUOTE]


That did help! thanks.

I'm still trying to figure out how to update Firefox  - Kilk isn't working for me and the application install program doesn't seem to have an update facility.  Do I have to uninstall the old version first?

Rob

---


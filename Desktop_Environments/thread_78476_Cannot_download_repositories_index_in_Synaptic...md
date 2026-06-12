---
title: "Cannot download repositories index in Synaptic.."
date: 2005-10-18
forum: Desktop Environments
---

### Post by michaelharg on 2005-10-18
Ive tried to add the universe etc repositories to synaptic following the instructions given in the wiki, everything goes fine till i have to reload the repositories, then i get the following messages:
-------------------------------------------------
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)
[http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)
------------------------------------------------

and

------------------------------------------------
The following problems were found on your system:

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
-------------------------------------------

I am connected to the internet however and can use firefox.

I am well confused...

Thanks very much..

---

### Post by mlomker on 2005-10-18
> I am connected to the internet however and can use firefox.


It might be temporary.  I've had troubles with the Ubuntu repositories over the last couple days and have switched to a mirror.  Many of the download sites [listed on this page]("http://www.ubuntu.com/download/") are likely to be a mirror--just change gb.archive.ubuntu.com in your /etc/apt/sources.list to whatever the servername is in their URL.

---

### Post by michaelharg on 2005-10-18
I think the problem is a lot more system wide than just synaptic as i cannot connect to GAIM or use wget. To get firefox to work i had to change the ipV6 settings, my router cannot be configured properly. Is there a simple guide to doing this?

Thanks very much

MIchael Hargreaves

---

### Post by mlomker on 2005-10-18
> Is there a simple guide to doing this?


I don't think so.  The problems that you are seeing aren't typical.

I wonder if your DNS is working well?

```

cat /etc/resolv.conf

```

Try to verify whether or not the DNS server entries are correct.

---

### Post by michaelharg on 2005-10-18
I get:
-------------------------------------------------
michael@ubuntu:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
-------------------------------------------------

There were no error messages...

Is there anything else it could be?

---

### Post by mlomker on 2005-10-18
> Is there anything else it could be?

That means that your router is proxying DNS service.  If you ping things by name at a command-line do the responses come back quickly?

Ctrl-C to stop these:
```

ping www.mpr.org
ping www.cnn.com

```

---

### Post by michaelharg on 2005-10-18
this is what happens:
---------------------------------------
michael@ubuntu:~$  ping [www.cnn.com](www.cnn.com)
PING [www.cnn.com](www.cnn.com) (64.236.24.20) 56(84) bytes of data.

--- [www.cnn.com](www.cnn.com) ping statistics ---
45 packets transmitted, 0 received, 100% packet loss, time 43992ms
----------------------------------------
I assume that the 0 recieved means somethings up?

---

### Post by mlomker on 2005-10-18
> PING [www.cnn.com](www.cnn.com) (64.236.24.20) 56(84) bytes of data.


No.  DNS' job is to convert names into numbers.  It did that, so that seems okay.  I'm not sure what's going on with your setup.  What does gaim do when you try to use it?

---

### Post by michaelharg on 2005-10-18
I'll let you know my setup, that might help.
Im using a D-link dsl G604t Router, connected to my computer through a bridged(i think) ethernet adaptor.
When i use gaim i get a Connection Error from Notification Server after i have left it for a while (2-3mins)
When i try to update the repositories in Synaptic i get messgaes saying that theres no such file or directory..
When i use wget i get a message saying unable to resolve host..

Its like my computer doesnt know im conected to the internet... bahh.

Thanks very much

---

### Post by trellis on 2005-10-18
hi 
This is the  same problem as I have and I also have the same router as you too, help!

---

### Post by mlomker on 2005-10-18
It sounds to me like the DNS proxy built into your router is flaky (or the DNS server at your ISP).  Go into the web interface for your router and somewhere it should tell you the TCP/IP numbers for the ISP's DNS servers.

The next time things stop working try first to ping something by name, like before, and if that doesn't return the number then try pinging your ISP's DNS servers by number.

I think what I'd try is downloading the **resolvconf** package and plug in the numbers for the DNS servers that your router is using.  [Check out this post.]("http://www.ubuntuforums.org/showthread.php?p=423723#post423723")

---

### Post by zenodaddy on 2005-10-18
Well since two users are having the same issue with the same router I would seriously doubt that it is going to be an issue with the ISP.. go into your router and check your dhcp settings.

---

### Post by fheinsen on 2005-10-18
Hi -- I've had the same DNS problem with cheap routers when using DHCP.  These two solutions work for me:
 
1. Go to Applications -> Accesories -> Terminal and type "sudo install resolvconf pump dnsmasq" (see [http://www.ubuntuforums.org/showthread.php?t=5690]("http://www.ubuntuforums.org/showthread.php?t=5690"))

2. Follow the instructions here: [https://wiki.ubuntu.com/StaticDnsWit...ight=%28dns%29]("https://wiki.ubuntu.com/StaticDnsWithDhcp?highlight=%28dns%29")

---


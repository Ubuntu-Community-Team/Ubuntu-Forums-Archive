---
title: "Accessing Ubuntu Machine from Work"
date: 2009-03-15
forum: General Help
---

### Post by mojo_man on 2009-03-15
Hello,

I would like to access my Ubuntu home box from work. Can someone suggest a good web resource I can use to get things set up?

---

### Post by Herman on 2009-03-15
Well, this one might be a little too basic for you, especially where it begins at the top.
If you skip to somewhere further down the page and read some of the links, there should be enough information available there to help you get that set up, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")** **

---

### Post by martrn on 2009-03-15
> **mojo_man said:**
> Hello,I would like to access my Ubuntu home box from work. Can someone suggest a good web resource I can use to get things set up?

[http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html]("http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html").

---

### Post by Peter09 on 2009-03-15
installing openssh-server on your home machine will give you the ability to run applications remotely. Have you a windows machine at work? if so you will need something like Putty to use ssh on windows.

---

### Post by mojo_man on 2009-03-15
> **Herman said:**
> Well, this one might be a little too basic for you, especially where it begins at the top.
If you skip to somewhere further down the page and read some of the links, there should be enough information available there to help you get that set up, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")** **

Okay I did the following.

I installed open ssh server
I allowed my router to forward any traffic incoming on port 22
I enabled ufw and allowed anything incoming for port 22
I put UsersAllow mohit so just I can ssh in

When I do ssh localhost. It says connection refused on port 22?
What is going on?


I have

---

### Post by mradem on 2009-03-15
[http://www.nomachine.com/products.php](http://www.nomachine.com/products.php)

I've been using the free version to access my home machine from multiple computers including windows and other linux installations.  With a decent internet connection it's as if you're sitting at your home computer.

---

### Post by Peter09 on 2009-03-16
ssh -v <username>@localhost will give you more information.

---

### Post by jtb_90 on 2009-03-16
Do you know if this is the same as LogMeIn for Windows? I've been using that for a while with no problems, if this has the same strengths I'll switch and stop trying to get LogMeIn to work with WINE lol.

Cheers

---

### Post by sanemanmad on 2009-03-16
Basically you are needing to remotely connect to your home pc from work, right?. in that case you are almost there with ssh, now you need to get the ip address of your router/gateway and use that.

EX. 1. I am at work and ssh into my server at home. I use "putty" and i connected using the external ip of my router which was 79.236.xx.xxx, even though my server i actually using 192.168.x.x,(The internet should not know of your internal network) hence the reason you forwarded 22 to your pc.

EX. 2

If you are already on the same network as your pc then you would use the internal ip, 192.168.x.x, since your router knows of those IP's

---

### Post by Herman on 2009-03-16
> EX. 2
If you are already on the same network as your pc then you would use the internal ip, 192.168.x.x, since your router knows of those IP'sIt's best to try SSH out within the LAN and make sure you have it working well there before progressing to getting it working over the internet.
> Okay I did the following.
I installed open ssh server
I allowed my router to forward any traffic incoming on port 22
I enabled ufw and allowed anything incoming for port 22
I put UsersAllow mohit so just I can ssh in
When I do ssh localhost. It says connection refused on port 22?
What is going on?The most common problem is caused by SSH's tight security sensitivities.
The SSH client records certain details about every host the client connects to in a file named [COLOR=#000000]'known_hosts', which is [/COLOR]located in a hidden folder in your /home/username directrory called '.ssh'.

[COLOR=#000000]If an operating system on the LAN's details have been changed in any way since the first time an SSH connections was made with that host, that [/COLOR][COLOR=#000000]it can upset SSH's security sensitivities and SSH can get cranky and refuse to connect. [/COLOR][COLOR=#000000]
For example, if the IP number doesn't match the MAC address, or if certain other differences are detected.

It's important to realize that it's your own computer, (the one you're connecting from), and not the host that you're trying to connect to, that's blocking the connection.

If that's what the problem is (I'm only guessing), you can fix that simply by deleting the [/COLOR].ssh/known_hosts file.
Don't worry about it, you can safely delete the file because SSH will automatically create a brand new .ssh/known_hosts[COLOR=#000000] file for you automatically the next time you make a new connection.
[/COLOR]```
sudo rm -rf .ssh/known_hosts
```I'm not sure if that could be your problem, but I hope that helps you anyway.

Other than that, if the host has any firewall, check that you have it configured to allow the connection, (of course). You don't need your firewall (IPTables) configured in Ubuntu if the only service you install is SSH. If you install any other services, then you should install a firewall editor such as Firestarter or something similar, unless you know how to set your IPTables up manually.

---

### Post by mojo_man on 2009-03-16
I am work right now and I am running Ubuntu 8.04, at home I am trying Ubuntu 8.10. I installed OPENSSH at work.

When I try and run ssh localhost it works. I think the problem is that openssh did not install properly on the home machine. 

I will go home and try again tonight and keep you guys posted.

These are the lines I get when I install OPENSSH at work:

```
mohit@mohit-desktop:~/.ssh$ sudo apt-get install openssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwww-ssl0 libwxgtk2.6-0 m4 procmail expect libwxbase2.6-0 expectk liblockfile1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openssh-blacklist
Suggested packages:
  molly-guard rssh
The following NEW packages will be installed:
  openssh-blacklist openssh-server
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 2378kB of archives.
After this operation, 4870kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com hardy-updates/main openssh-blacklist 0.1-1ubuntu0.8.04.1 [2124kB]
Get:2 http://archive.ubuntu.com hardy-updates/main openssh-server 1:4.7p1-8ubuntu1.2 [254kB]                                                
Fetched 2378kB in 8s (292kB/s)                                                                                                              
Preconfiguring packages ...
Selecting previously deselected package openssh-blacklist.
(Reading database ... 203948 files and directories currently installed.)
Unpacking openssh-blacklist (from .../openssh-blacklist_0.1-1ubuntu0.8.04.1_all.deb) ...
Selecting previously deselected package openssh-server.
Unpacking openssh-server (from .../openssh-server_1%3a4.7p1-8ubuntu1.2_i386.deb) ...
Setting up openssh-blacklist (0.1-1ubuntu0.8.04.1) ...
Setting up openssh-server (1:4.7p1-8ubuntu1.2) ...
Creating SSH2 RSA key; this may take some time ...
Creating SSH2 DSA key; this may take some time ...
 * Restarting OpenBSD Secure Shell server sshd     
```

---

### Post by Herman on 2009-03-16
:D Port 22 is the default port for SSH. [COLOR=#000000]If [/COLOR][COLOR=#000000]an operating system has SSH server installed[/COLOR][COLOR=#000000] it should have [/COLOR][COLOR=#000000]port 22[/COLOR][COLOR=#000000] showing as an open port when we run a scan from another computer in the LAN.

First [/COLOR][COLOR=#000000]you need to know the IP number for the computer that you want to scan.
[/COLOR][COLOR=#666666][COLOR=#000000]Y[/COLOR][/COLOR][COLOR=#666666][COLOR=#000000]ou can [/COLOR][/COLOR][COLOR=#666666][COLOR=#000000]easily[/COLOR][/COLOR][COLOR=#666666][COLOR=#000000] find that out  by typing the ifconfig command in 'terminal' of your (host) computer.[/COLOR][/COLOR]
```
ifconfig
```
example output,
```
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:37:21:88  
          **inet addr:192.168.0.106 ** Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe37:2188/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1084562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1040098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:975849564 (975.8 MB)  TX bytes:679710856 (679.7 MB)
          Interrupt:23 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```[COLOR=#000000]
Then in your client computer, go to 'System'-->'Administration'-->'Network Tools', and click on the 'Port Scan' tab.
In the 'Network address field, type in the LAN IP number for the computer to be scanned.
The scan only takes a few seconds and port 22 should show up right away.

If the scan keeps running, you can cancel it because probably it hasn't been successful in finding any open ports.
In that case, check your IPTables filter editor (firewall), to make sure port 22 is allowed, you can set restrictions on it later.

[/COLOR][COLOR=#000000]If port 22 is open, you should be able to connect to a user account in the host computer from an SSH client in your LAN, providing you know the username and password for the host account.

[/COLOR]

---

### Post by sanemanmad on 2009-03-23
why not ```
netstat -tl
``` on the machine in question? or ```
ps -ef|grep -i sshd
```

---


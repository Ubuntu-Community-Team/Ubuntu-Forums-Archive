---
title: "Internet requires root access"
date: 2009-01-07
forum: General Help
---

### Post by Michael_TSM on 2009-01-07
SOLVED: Okay the problem was related to a previous install of Dansguardian CE that was not completely removed. Running this as root in the terminal should solve the problem:

apt-get --purge remove --assume-yes "dansguardian"
apt-get --purge remove --assume-yes "tinyproxy"
apt-get --purge remove --assume-yes "clamav"
apt-get --purge remove --assume-yes "firehol"
apt-get --purge remove --assume-yes "dansguardian-gui-ubuntu"

For some reason the solution took a while to kick in after running it...but it eventually worked.

ORIGINAL PROBLEM:
After I upgraded to Ubuntu 8.10 none of my users despite having the permissions to do so could access the internet. When they open up firefox it fails to connect, in other words Firefox runs but cannot load a webpage as if I was not connected to the internet.
Firefox only works when you go through the terminal by typing sudo firefox...
The same exact problem happens if I install Opera a different browser.
Everything else works fine. Any ideas?


EDIT: Uninstalling and Reinstalling through synpatic didn't solve the problem. I also tried installing Opera and it had the same problem as firefox.

---

### Post by gettinoriginal on 2009-01-08
Alt F2 and type in```
 gksudo nautilus
```, that will open your file browser in root.  From there go to file system /home/<username>/mozilla/firefox and check the permission tab, if it says root, then change it to <username>

Sorry, I don't know how to do it via command line :(

---

### Post by Ahadiel on 2009-01-08
```
 sudo chown -R username:username ~/.mozilla
```

---

### Post by Michael_TSM on 2009-01-08
Thanks for quick response, much appreciated.

I gave your suggestion a try, however I do have permissions to that folder and I can run Firefox as a user, the problem is that once the user has opened firefox they cannot connect to any websites, as if my computer wasn't connected to the internet.
Firefox can only connect to websites when I open it in the terminal > i.e. sudo firefox

I'm thinking perhaps I will try uninstalling firefox and then reinstalling it.
EDIT: Uninstalling and Reinstalling through synpatic didn't solve the problem. I also tried installing Opera and it had the same problem as firefox.

---

### Post by gettinoriginal on 2009-01-08
Might check the others permissions in users and groups to make sure they can share applications.

---

### Post by mssever on 2009-01-08
Using Firefox is a poor way to test Internet connectivity. ping and/or tracert give better results.

For example, try this:
```
ping -c5 google.com
```And try it with sudo. If rootless ping doesn't work, messing with Firefox is just wasting time, because your problem is elsewhere. If rootless ping does work, you might try curl or wget and see what happens. The idea is to use command-line programs for troubleshooting because they tend to be smaller with less to go wrong, and they tend to provide as good or better information when something does go wrong.

---

### Post by Michael_TSM on 2009-01-09
Thanks for the replies,

gettinoriginal:
My user has all the correct permissions in 'users and groups' that would allow it to access the internet unhindered.

mssever:
Do you know of a good guide to using curl or wget?
I did as you said, first as a user then as root, and received identical results.

As user:
> michael@michael-desktop:~$ ping -c5 google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=243 time=233 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=243 time=235 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=243 time=232 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=243 time=236 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=243 time=231 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4014ms
rtt min/avg/max/mdev = 231.011/234.071/236.648/2.051 ms


Then as root:
> root@michael-desktop:/home/michael# ping -c5 google.com
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=243 time=231 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=243 time=230 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=243 time=235 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=243 time=230 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=243 time=233 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4013ms
rtt min/avg/max/mdev = 230.403/232.264/235.052/1.879 ms


It should be noted that all other applications can access the internet fine like email & upgrade manager, it's only web browsers that require root access to operate properly, namely firefox and also opera when I tried it.

---

### Post by mssever on 2009-01-09
> **Michael_TSM said:**
> Do you know of a good guide to using curl or wget?
Both have man pages, but the basics are simple enough. wget is a tool to download a file. So, if you type ```
wget http://google.com
```you should end up with a file containing the contents of Google's home page. ```
curl http://google.com
```should print the raw HTML of Google's home page to your terminal window. Of course, there's a lot more you can do with these tools, but the basics I gave you should be sufficient for troubleshooting.

Something else that might be worth trying: delete your firefox profile (after making a backup if you want to keep your settings and bookmarks) by deleting or renaming $HOME/.mozilla . It's possible that your Firefox profile got hosed--though that doesn't explain why Opera also gives you trouble.

You might also try epiphany (the "official" Gnome browser) or elinks (a terminal-based, text-only browser).

---

### Post by Michael_TSM on 2009-01-09
Thanks again for the reply, but alas no progress. It seems both epiphany and Wget also require root access to work properly.

Wget gives me the following response as user:
> michael@michael-desktop:~$ wget [http://google.com](http://google.com)
--2009-01-09 19:04:24--  [http://google.com/](http://google.com/)
Resolving google.com... 72.14.205.100, 74.125.45.100, 209.85.171.100
Connecting to google.com|72.14.205.100|:80... failed: Connection refused.
Connecting to google.com|74.125.45.100|:80... failed: Connection refused.
Connecting to google.com|209.85.171.100|:80... failed: Connection refused.

And this response as root:
> michael@michael-desktop:~$ sudo wget [http://google.com](http://google.com)
--2009-01-09 19:04:48--  [http://google.com/](http://google.com/)
Resolving google.com... 74.125.45.100, 209.85.171.100, 72.14.205.100
Connecting to google.com|74.125.45.100|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.google.com/](http://www.google.com/) [following]
--2009-01-09 19:04:48--  [http://www.google.com/](http://www.google.com/)
Resolving [www.google.com](www.google.com)... 209.85.175.99, 209.85.175.104, 209.85.175.147
Connecting to [www.google.com|209.85.175.99|:80](www.google.com|209.85.175.99|:80)... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://www.google.com.au/](http://www.google.com.au/) [following]
--2009-01-09 19:04:49--  [http://www.google.com.au/](http://www.google.com.au/)
Resolving [www.google.com.au](www.google.com.au)... 209.85.171.147, 209.85.171.99, 209.85.171.103, ...
Connecting to [www.google.com.au|209.85.171.147|:80](www.google.com.au|209.85.171.147|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [  <=>                                  ] 5,688       27.1K/s   in 0.2s    

2009-01-09 19:04:49 (27.1 KB/s) - `index.html' saved [5688]


---

### Post by mssever on 2009-01-09
> **Michael_TSM said:**
> Thanks again for the reply, but alas no progress. It seems both epiphany and Wget also require root access to work properly.

Wget gives me the following response as user:


And this response as root:
Well, I initially found it very difficult to believe that the problem was actually as you described, but I now see that it is. If even wget requires root access, then...

For the life of me, I can't imagine what might cause such a problem. Unless it has something to do with port 80. See if you can connect to a secure (https:) site without root. Also, see if you can access [my repository]("http://repository.scottseverance.us:8066/falcon/dists/main/") without root, since it's on port 8066, not port 80. If so, then your networking tools have some problem with port 80 (the default port for normal web connections).

---

### Post by heindsight on 2009-01-09
Sorry - double post due to connection problems.

---

### Post by heindsight on 2009-01-09
This looks like a misconfigured firewall to me. It looks as though you're blocking outgoing traffic to port 80 for all users except root.

I can replicate your symptoms by doing:
```

sudo iptables -A OUTPUT -m owner --uid-owner 0 -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 80 -j DROP

```

To verify if this is the case, could you post the output of
```
sudo iptables -L
```

---

### Post by Michael_TSM on 2009-01-11
> **mssever said:**
> For the life of me, I can't imagine what might cause such a problem. Unless it has something to do with port 80. See if you can connect to a secure (https:) site without root. Also, see if you can access [my repository]("http://repository.scottseverance.us:8066/falcon/dists/main/") without root, since it's on port 8066, not port 80. If so, then your networking tools have some problem with port 80 (the default port for normal web connections).

**mssever:**
Hmm, yes I can connect to a https site without root, I managed to connect to [https://www.cia.gov/](https://www.cia.gov/)
I couldn't access the link you gave either in root or as a user so nothing gained there, however firefox and wget didn't give me the usual 'failed to connect' or 'connection refused' responses that they've been giving me.
```
michael@michael-desktop:~$ wget http://repository.scottseverance.us:8066/falcon/dists/main/
--2009-01-11 21:32:21--  http://repository.scottseverance.us:8066/falcon/dists/main/
Resolving repository.scottseverance.us... 75.104.193.18
Connecting to repository.scottseverance.us|75.104.193.18|:8066...
```
It did the same thing in root and as a user.

**heindsight:**
Here is the output you requested, however I myself have no idea what it means.
```
michael@michael-desktop:~$ sudo iptables -L
[sudo] password for michael: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by heindsight on 2009-01-11
> **Michael_TSM said:**
> 
**heindsight:**
Here is the output you requested, however I myself have no idea what it means.
```
michael@michael-desktop:~$ sudo iptables -L
[sudo] password for michael: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

That means you don't have any firewall rules loaded. So it seems your problem is not being caused by a firewall misconfiguration.

It just occurred to me to wonder whether only your user account is blocked from making connections to port 80 or if only root can connect to port 80. Perhaps you could try creating a new user account, then log in as that user and try to wget something again. If it works for that user then the problem is probably specific to your user account. (Of course this won't really help to solve the problem, but it may bring us closer to understanding what's going on)

---

### Post by Michael_TSM on 2009-01-14
Unfortunately it seems to be affecting all users...

I made a test user, but no luck, didn't connect:
```
test@michael-desktop:~$ wget www.ubuntu.com
--2009-01-14 18:20:25--  http://www.ubuntu.com/
Resolving www.ubuntu.com... 91.189.94.9
Connecting to www.ubuntu.com|91.189.94.9|:80... failed: Connection refused.
```

Only with root access did it connect:
```
test@michael-desktop:~$ sudo wget www.ubuntu.com
[sudo] password for test: 
--2009-01-14 18:20:47--  http://www.ubuntu.com/
Resolving www.ubuntu.com... 91.189.94.9
Connecting to www.ubuntu.com|91.189.94.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15499 (15K) [text/html]
Saving to: `index.html.1'

100%[======================================>] 15,499      18.5K/s   in 0.8s    

2009-01-14 18:20:49 (18.5 KB/s) - `index.html.1' saved [15499/15499]

```

---

### Post by Michael_TSM on 2009-01-29
Nobody has any ideas?

---

### Post by heindsight on 2009-01-29
> **Michael_TSM said:**
> Nobody has any ideas?

I'm afraid I'm more or less out of ideas.
I'm not sure if this will really help, but could you try running tcpdump:
```
sudo tcpdump -i eth1 -p -v
```
(replace eth1 with the network interface you use to connect to the internet) and then do a wget (as a normal user) and post the tcpdump output here. it might just give us a better indication of where things are going wrong...

---

### Post by Michael_TSM on 2009-01-30
Thanks again for trying to help, I think this is what you were asking for:
> 
tcpdump: listening on lo, link-type EN10MB (Ethernet), capture size 96 bytes
19:08:46.668705 IP (tos 0x0, ttl 64, id 5632, offset 0, flags [DF], proto TCP (6), length 60) michael-desktop.local.56403 > localhost.http-alt: S, cksum 0x0c38 (correct), 1332528576:1332528576(0) win 5840 <mss 1460,sackOK,timestamp 7590848 0,nop,wscale 5>
19:08:46.668762 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40) ipvs.moddb.com.www > michael-desktop.local.56403: R, cksum 0xacca (correct), 0:0(0) ack 1332528577 win 0

---

### Post by heindsight on 2009-01-30
You seem to have posted output for tcpdump listening on the loopback interface. Your loopback interface is only a connection to your own machine so that shouldn't be your main internet connection. Rather try using:
```
sudo tcpdump -i any -p -vn
```

I do find it rather strange that there does seem to some traffic on your loopback interface. From the tcpdump output you posted, it seems you tried to establish a connection to port 8080 on your own local machine and then got a Connection refused reply from a moddb.com server. The only way this makes any sense to me is if you have a web proxy set up on your own computer and you've configured all web traffic to pass through this proxy. If this is the case, then perhaps your problem is due to some proxy misconfiguration.

maybe you can try doing:
```
wget --no-proxy www.ubuntu.com
``` as a normal user and see if that works.

---

### Post by Michael_TSM on 2009-01-30
Unfortunately no proxy doesn't change anything:
> michael@michael-desktop:~$ wget --no-proxy [www.ubuntu.com](www.ubuntu.com)
--2009-01-31 10:21:34--  [http://www.ubuntu.com/](http://www.ubuntu.com/)
Resolving [www.ubuntu.com](www.ubuntu.com)... 91.189.94.8
Connecting to [www.ubuntu.com|91.189.94.8|:80](www.ubuntu.com|91.189.94.8|:80)... failed: Connection refused.
 
This may sound like a silly question, but how do I run wget while tcpdump is already running? Last time I opened a new terminal to run wget clearly the wrong thing to do...

---

### Post by mssever on 2009-01-30
> **Michael_TSM said:**
> This may sound like a silly question, but how do I run wget while tcpdump is already running? Last time I opened a new terminal to run wget clearly the wrong thing to do...
Running wget and tcpdump in separate terminals is indeed the proper way to do it.

One further proxy-related test is to examine the http_proxy environment variable. From your previous response, it appears that you don't have a proxy configured. To be sure, run ```
echo $http_proxy
```If it's unset (just a blank line), then there's no proxy, at least as far as wget is concerned.

---

### Post by Michael_TSM on 2009-02-02
Amazing how you people persist, thankyou, although I'm beginning to lean towards just reinstalling Ubuntu.

Here are the outputs requested, firstly to **echo $http_proxy**, Which came up blank like you said.
```
michael@michael-desktop:~$ echo $http_proxy


```

Secondly to **sudo tcpdump -i any -p -vn**, This one just kept on going so I just chopped it off, I figured you were only asking for the first bit.
```
michael@michael-desktop:~$ sudo tcpdump -i any -p -vn
[sudo] password for michael: 
tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
23:34:28.880906 arp who-has 192.168.0.9 tell 192.168.0.1
23:34:29.236404 IP (tos 0x0, ttl 64, id 18311, offset 0, flags [DF], proto UDP (17), length 60) 192.168.0.12.44939 > 192.168.0.1.53: 10262+ A? www.ubuntu.com. (32)
23:34:29.561819 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 76) 192.168.0.1.53 > 192.168.0.12.44939: 10262 1/0/0 www.ubuntu.com. A 91.189.94.8 (48)
23:34:29.562377 IP (tos 0x0, ttl 64, id 45221, offset 0, flags [DF], proto TCP (6), length 60) 192.168.0.12.45453 > 127.0.0.1.8080: S, cksum 0x83af (correct), 1556871036:1556871036(0) win 5840 <mss 1460,sackOK,timestamp 9324505 0,nop,wscale 5>
23:34:29.562429 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40) 91.189.94.8.80 > 192.168.0.12.45453: R, cksum 0x2f30 (correct), 0:0(0) ack 1556871037 win 0
23:34:29.825013 IP (tos 0x0, ttl 128, id 11796, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:29.825061 IP (tos 0x0, ttl 128, id 11797, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:30.574782 IP (tos 0x0, ttl 128, id 11798, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:30.574784 IP (tos 0x0, ttl 128, id 11799, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:31.324801 IP (tos 0x0, ttl 128, id 11800, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:31.324803 IP (tos 0x0, ttl 128, id 11801, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:31.338228 arp who-has 192.168.0.9 tell 192.168.0.1
23:34:32.075043 IP (tos 0x0, ttl 128, id 11802, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:32.331009 arp who-has 192.168.0.9 tell 192.168.0.1
23:34:32.824859 IP (tos 0x0, ttl 128, id 11803, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:33.331033 arp who-has 192.168.0.9 tell 192.168.0.1
23:34:33.574860 IP (tos 0x0, ttl 128, id 11804, offset 0, flags [none], proto UDP (17), length 78) 192.168.0.2.137 > 192.168.0.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
23:34:34.560977 ar
```

---

### Post by heindsight on 2009-02-02
> **Michael_TSM said:**
> Amazing how you people persist, thankyou, although I'm beginning to lean towards just reinstalling Ubuntu.

Don't give up and reinstall just yet. Somehow we'll get to the bottom of this, and reinstalling seems a bit extreme...

> 
Here are the outputs requested, firstly to **echo $http_proxy**, Which came up blank like you said.
```
michael@michael-desktop:~$ echo $http_proxy


```


OK, so wget is not trying to use a proxy. I can't understand why it's sending the request to 127.0.0.1:8080 though. I'm not sure it will help, but could you perhaps post the output of:
```
route -n
```
and
```
cat /etc/hosts
```

> 
```

tcpdump: listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
23:34:29.236404 IP (tos 0x0, ttl 64, id 18311, offset 0, flags [DF], proto UDP (17), length 60) 192.168.0.12.44939 > 192.168.0.1.53: 10262+ A? www.ubuntu.com. (32)
23:34:29.561819 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 76) 192.168.0.1.53 > 192.168.0.12.44939: 10262 1/0/0 www.ubuntu.com. A 91.189.94.8 (48)
23:34:29.562377 IP (tos 0x0, ttl 64, id 45221, offset 0, flags [DF], proto TCP (6), length 60) 192.168.0.12.45453 > 127.0.0.1.8080: S, cksum 0x83af (correct), 1556871036:1556871036(0) win 5840 <mss 1460,sackOK,timestamp 9324505 0,nop,wscale 5>
23:34:29.562429 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto TCP (6), length 40) 91.189.94.8.80 > 192.168.0.12.45453: R, cksum 0x2f30 (correct), 0:0(0) ack 1556871037 win 0

```

OK, what's happening here is that you're sending a DNS request to look up the IP address of [www.ubuntu.com](www.ubuntu.com) and getting the response 91.189.94.8.
Then you're sending an http request to port 8080 on 127.0.0.1 and getting a connection refused reply from port 80 on 91.189.94.8.

Based on the fact that the request goes to 127.0.0.1 and the previous tcpdump output you posted, it seems these last two items (the http request and the connection refused response) are sent and received on the loopback interface. With no firewall rules loaded and no proxy configured, I can't imagine why that would be happening.

Could you perhaps post the output of the same tcpdump command, but this time doing wget as root? Just for comparison...

---

### Post by Michael_TSM on 2009-02-02
Okay, sorry for ignoring your last post but I think I know what the problem is.
Just before I upgraded I uninstalled dansguardian (The CE edition) thinking I could replace it with a firefox add on that did the same thing with less trouble.
After remembering this I did a google search and found the following:
[http://ubuntuforums.org/archive/index.php/t-468910.html](http://ubuntuforums.org/archive/index.php/t-468910.html)
So I followed their suggestions and I found a few more things to remove, like tinyproxy, but my internet is still not working without root. Anyideas as to how I might hunt down and remove the last vestiges of this program?

---

### Post by mssever on 2009-02-03
> **Michael_TSM said:**
> Okay, sorry for ignoring your last post but I think I know what the problem is.
Just before I upgraded I uninstalled dansguardian (The CE edition) thinking I could replace it with a firefox add on that did the same thing with less trouble.
After remembering this I did a google search and found the following:
[http://ubuntuforums.org/archive/index.php/t-468910.html](http://ubuntuforums.org/archive/index.php/t-468910.html)
So I followed their suggestions and I found a few more things to remove, like tinyproxy, but my internet is still not working without root. Anyideas as to how I might hunt down and remove the last vestiges of this program?
I suggest looking through the CE installer to see what kind of foolishness it did during the install. My experience with CE was with their script to convert a standard Ubuntu install to CE, which my brother ran. He promptly called me with problems, and I ended up reviewing the script and discovering that it was incompetently-written and had several major bugs that could potentially cause data loss. When I complained to the maintainer, he admitted that he didn't know much about programming (so he shouldn't have attempted such a script in the first place), but he refused to fix the bugs I pointed out and I wasn't interested in fixing them myself.

So, there's a good chance whatever you ran from CE is to blame. Dansguardian itself shouldn't cause you those problems.

---

### Post by jimv on 2009-02-03
nm

---

### Post by DonaldJ on 2009-02-03
This problem sounds a little like an extremely rare router-glitch.. like when a neighbor is stealing your wireless connection, and has made Internet enemies..?  But it sounds like a lot more...  Is there Linux software that can run to determine if someone is stealing your wireless connection, and if your connection's usage is exclusively all yours..?

Plus, I found that early Firefox caused its own problems in updating itself...  Too often updates conflicted with old config files, which weren't being deleted...  It caused some sort of a "logjam conflict" like macromedia does in W98...

Plus this problem might be conflict between two softwares.. like two browsers.. or like how two firewalls mess-up.. or two somethings in the same box.. or between Firefox and an AVS, or Firefox and a firewall.. like   the classic one in W98 between Firefox and Symantec, and/or Firefox and ZoneAlarm...  It deserves more research..  but it is a Nasty...  I'm bets the solution, or hint toward the solution might be in scanning the old Firefox glitch issues in W98...  There's a lot of good troubleshooting stuff in those archives which can be used for other things...

Off the top, I figure if you could super-accelerate the hd just for a moment.. then those glitches might shine brighter, leaving them more exposed and gross for easier diagnosis.. but that would likely destroy the OS..  but then you would know where the bad is...

---

### Post by mssever on 2009-02-03
> **DonaldJ said:**
> Plus, I found that early Firefox caused its own problems in updating itself...  Too often updates conflicted with old config files, which weren't being deleted...  It caused some sort of a "logjam conflict" like macromedia does in W98...

Plus this problem might be conflict between two softwares.. like two browsers.. or like how two firewalls mess-up.. or two somethings in the same box.. or between Firefox and an AVS, or Firefox and a firewall.. like   the classic one in W98 between Firefox and Symantec, and/or Firefox and ZoneAlarm...  It deserves more research..  but it is a Nasty...  I'm bets the solution, or hint toward the solution might be in scanning the old Firefox glitch issues in W98...  There's a lot of good troubleshooting stuff in those archives which can be used for other things...Firefox has already been conclusively ruled out.  Plus, Windows 98 has little in common with modern Linux.

> Off the top, I figure if you could super-accelerate the hd just for a moment.. then those glitches might shine brighter, leaving them more exposed and gross for easier diagnosis.. but that would likely destroy the OS..  but then you would know where the bad is...
I seriously doubt that accelerating the hard drive would have any effect on a networking issue.

---

### Post by heindsight on 2009-02-03
> **mssever said:**
> I suggest looking through the CE installer to see what kind of foolishness it did during the install. My experience with CE was with their script to convert a standard Ubuntu install to CE, which my brother ran. He promptly called me with problems, and I ended up reviewing the script and discovering that it was incompetently-written and had several major bugs that could potentially cause data loss. When I complained to the maintainer, he admitted that he didn't know much about programming (so he shouldn't have attempted such a script in the first place), but he refused to fix the bugs I pointed out and I wasn't interested in fixing them myself.

So, there's a good chance whatever you ran from CE is to blame. Dansguardian itself shouldn't cause you those problems.

I agree, sounds like something from CE is to blame. I'm not sure how, but it would seem some process (perhaps some sort of packet sniffer) is intercepting all traffic destined for port 80 on any host and rerouting it through port 8080 on 127.0.0.1.

It seems to me that knowing what process is listening on port 8080 would help a lot in figuring out what's going on.

Try running: ```
sudo netstat -tlenp
``` and look for a line with either 127.0.0.1:8080 or 0.0.0.0:8080 in the local address column. The last column of that line will give you the name of the process listening on port 8080.

---

### Post by jimv on 2009-02-03
Michael my man, try this:

sudo apt-get remove --purge firehol

Here's the config file for firehol that Dansguardian CE installs:

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

**transparent_squid 8080 "root root"**

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

# Accept all client traffic on any interface
	#client all accept
```

---

### Post by Michael_TSM on 2009-02-04
Okay, purging all dansguardian CE programs and related programs appears to have fixed it, it took a while to take effect for some reason, but take effect it has.
Thanks everyone for your time and help, it was greatly appreciated.

---


---
title: "FTP problem"
date: 2006-06-25
forum: Desktop Environments
---

### Post by jonboy99 on 2006-06-25
Hi all, am having a problem getting a lot of ftp clients to work on my comp.

Have used fireftp (the firefox extension) to try and log on to my pipex webspace, which annoyingly has recently demanded active ftp to connect.  However I have set all the clients to this mode.
When I attempt connection with fireftp on ubuntu I get this error log:

> false  525
FireFTP 0.94.2 'Sister Kate', created by Mime &#268;uvalo
220 Microsoft FTP Service
       USER aucj14
331 Password required for aucj14.
       PASS (password not shown)
230 User aucj14 logged in.
       PWD
257 "/" is current directory.
       TYPE A
200 Type set to A.
       PORT 127,0,1,1,153,33
500 Invalid PORT Command.
       LIST
150 Opening ASCII mode data connection for /bin/ls.
425 Can't open data connection.

However, if I boot the same computer into windows XP and use fireftp, it connects fine   :confused: 

Kbear will also not connect, but I can't find the error log, neither will konqueror, despite me configuring it for active ftp mode.
The only one that will work is gFTP, which i'm not too keen on.  The log file for this is:

> Successfully changed local directory to /home/jonboy99/Desktop
Looking up dslftp.dsl.pipex.com
Trying dslftp.dsl.pipex.com:21
Connected to dslftp.dsl.pipex.com:21
220 Microsoft FTP Service
USER aucj14

331 Password required for aucj14.
PASS xxxx
230 User aucj14 logged in.
SYST

215 Windows_NT
TYPE I

200 Type set to I.
CWD /

250 CWD command successful.
Loading directory listing / from server (LC_TIME=en_GB.UTF-8)
PORT 192,168,1,24,128,108

200 PORT command successful.
LIST -aL

150 Opening BINARY mode data connection for /bin/ls.
226 Transfer complete.

I see that this port command is pointing to a local IP (192.168.1.24), so what's going on as it works?

Am using a router to connect, and I have not set a firewall up on ubuntu (it doesn't have one by default does it?  Or does it?).  The router definitely doesn't have a firewall enabled, otherwise I guess lack of any port forwarding might explain the problem.

Cheers
Jon

[EDIT]

Hmm, just booted a local computer on the same router into debian sarge and fireFTP worked, using the local IP: 

> 220 Microsoft FTP Service
       USER aucj14
331 Password required for aucj14.
       PASS (password not shown)
230 User aucj14 logged in.
       PWD
257 "/" is current directory.
       TYPE A
200 Type set to A.
       PORT 192,168,1,18,128,7
200 PORT command successful.
       LIST
150 Opening ASCII mode data connection for /bin/ls.
226 Transfer complete.
       NOOP
200 NOOP command successful.

So why isn't fireftp using that IP on ubuntu?  Aaaargh..

---

### Post by ayoli on 2006-06-25
well, do you have on your ubuntu /etc/hosts (open it with: gksudo gedit) a line with your local ip and your hostname like:
```
192.168.1.24    your_hostname
```
if not, add it.
you can also do that thru menu System>Administration>Network, then pick Hosts tab and add your ip with your hostname
I think could be that, cause of r first error log that show a line:
```
PORT 127,0,1,1,153,33
```
127.0.0.1 is loopback adress and cant be used as local ip

---

### Post by jonboy99 on 2006-06-25
Hi, think you're along the right lines there, my hosts file looked like this:


> 127.0.0.1 localhost xp24ubuntu
127.0.1.1 xp24ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

So I changed it to:

> # 127.0.0.1 localhost xp24ubuntu
# 127.0.1.1 xp24ubuntu

#next two lines added by jon
192.168.1.1 localhost xp24ubuntu
192.168.1.1 xp24ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


But now the ftp program gives me this error:

> 220 Microsoft FTP Service
USER aucj14
331 Password required for aucj14.
PASS (password not shown)
230 User aucj14 logged in.
PWD
257 "/" is current directory.
TYPE A
200 Type set to A.
PORT 192,168,1,1,192,196
500 Invalid PORT Command.
LIST
150 Opening ASCII mode data connection for /bin/ls.
425 Can't open data connection.

Not sure why the loopback address should be in there?

---

### Post by jonboy99 on 2006-06-25
I am a complete mongoose, I should have made it 192.168.1.2 - 192.168.1.1 is my router address.
I fixed the IP for the computer so it would work, but what;s the solution for other computers that use DHCP (as this one was)

What could have put the loopback address there?  Is it the ubuntu default or would adblock for firefox have done it?


Thanks for the help anyway, working great now!

---

### Post by ayoli on 2006-06-25
i dont use dhcp but maybe your dhcp client can update self your hosts file otherwise try to add a permanent lease to your router, means that your router will give always the same ip to the same computer (that's done with network car mac adress, your router manual should explain it if it's capable)

---


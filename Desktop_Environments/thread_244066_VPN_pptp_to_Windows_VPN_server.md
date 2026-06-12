---
title: "VPN pptp to Windows VPN server"
date: 2006-08-25
forum: Desktop Environments
---

### Post by chrisgibbs on 2006-08-25
Having installed pptp and pptp-config without any problem i thought that this might have been a painless process for setting up a connection to my work through a VPN.

My M$ Windows based desktop has no problems connecting to the VPN server so i have ruled out port forwarding problems and anything server based.

The error messages that gets produced seem to be a LCP timeout and i dont recieve anything back at all........


I have google'd and searched these forums for an answer to my problem but was unable to find anyone with a similar problem - perhaps the closest match i found when broadening my search was a MAC OSX laptop experiencing similar problems.......

Here is the output from the pptp-config with debugging on. Hopefully someone is able to help or provide an alternative since having VPN access is critical to my business.....

```

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.2 2004/06/19 08:57:15
# pppd --version
pppd version 2.4.4b1
# uname -a
Linux ls50a 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
# grep mppe /proc/modules
# modinfo ppp_mppe
filename:       /lib/modules/2.6.15-26-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-26-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
Array
(
    [name] => (hidden by pptpconfig)
    [server] => (hidden by pptpconfig)
    [domain] => (hidden by pptpconfig)
    [username] => (hidden by pptpconfig)
    [password] => (hidden by pptpconfig)
    [pppd-options] => noipdefault 50
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 1
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.14.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.14.254  0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug        # (from /etc/ppp/peers/SYL)
updetach        # (from command line)
logfd 1        # (from command line)
linkname SYL        # (from /etc/ppp/peers/SYL)
dump        # (from /etc/ppp/peers/SYL)
noauth        # (from /etc/ppp/options.pptp)
refuse-chap        # (from /etc/ppp/options.pptp)
refuse-eap        # (from /etc/ppp/options.pptp)
name (hidden by pptpconfig)        # (from /etc/ppp/peers/SYL)
remotename SYL        # (from /etc/ppp/peers/SYL)
50        # (from /etc/ppp/peers/SYL)
        # (from /etc/ppp/options.pptp)
pty pptp 202.181.24.229 --nolaunchpppd         # (from /etc/ppp/peers/SYL)
crtscts        # (from /etc/ppp/options)
        # (from /etc/ppp/options)
asyncmap 0        # (from /etc/ppp/options)
lcp-echo-failure 4        # (from /etc/ppp/options)
lcp-echo-interval 30        # (from /etc/ppp/options)
hide-password        # (from /etc/ppp/options)
ipparam SYL        # (from /etc/ppp/peers/SYL)
noipdefault        # (from /etc/ppp/peers/SYL)
proxyarp        # (from /etc/ppp/options)
usepeerdns        # (from /etc/ppp/peers/SYL)
nobsdcomp        # (from /etc/ppp/options.pptp)
nodeflate        # (from /etc/ppp/options.pptp)
require-mppe        # (from /etc/ppp/peers/SYL)
require-mppe-128        # (from /etc/ppp/options.pptp)
noipx        # (from /etc/ppp/options)
using channel 21
Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/0
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x9ff4c17f> <pcomp> <accomp>]
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
Waiting for 1 child processes...
  script pptp (hidden by pptpconfig) --nolaunchpppd , pid 7418
Script pptp (hidden by pptpconfig) --nolaunchpppd  finished (pid 7418), status = 0x0
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.14.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.14.254  0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.14.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.14.254  0.0.0.0         UG    0      0        0 eth0


```

Thanks all

---

### Post by j04j04 on 2006-10-18
Did you ever find a solution to your problem? I'm having the same issue going from Ubuntu 6.06 LTS to msW:XP sp2. My msW:XP sp2 desktop connects perfectly, but I keep getting almost the exact same thing as you:

```

pptpconfig: debug information dump begins
WARNING: security sensitive information follows
pptpconfig 1.12 2006/08/21 06:19:12
pptp version 1.7.0
pppd version 2.4.4b1
Linux Icebox 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux
# modinfo ppp_mppe || modinfo ppp_mppe_mppc
filename:       /lib/modules/2.6.15-27-386/kernel/drivers/net/ppp_mppe.ko
author:         Frank Cusack <fcusack@fcusack.com>
description:    Point-to-Point Protocol Microsoft Point-to-Point Encryption support
license:        Dual BSD/GPL
alias:          ppp-compress-18
version:        1.0.2
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:        ppp_generic
srcversion:     6B88E623CA7C4D7FE2F11FA
# grep mppe /proc/modules
Array
(
    [name] => (hidden by pptpconfig)
    [server] => (hidden by pptpconfig)
    [domain] => 
    [username] => (hidden by pptpconfig)
    [password] => (hidden by pptpconfig)
    [pppd-options] => 
    [pptp-options] => 
    [resolv] => 
    [dns-options] => 
    [routing] => routing_client_to_lan
    [usepeerdns] => 
    [require-mppe] => 1
    [nomppe-40] => 
    [nomppe-128] => 
    [refuse-eap] => 
    [mppe-stateful] => 
    [autostart] => 
    [iconify] => 
    [persist] => 
    [debug] => 1
    [client-to-lan] => 
)
# route -n (before pppd)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
pptpconfig: debug information dump ends, starting pppd
pppd options in effect:
debug	
updetach
logfd 1	
linkname (hidden by pptpconfig)
dump
noauth
refuse-chap
refuse-mschap
refuse-eap
name (hidden by pptpconfig)
remotename (hidden by pptpconfig)

pty pptp (hidden by pptpconfig) --nolaunchpppd 
crtscts	

asyncmap 0
lcp-echo-failure 4
lcp-echo-interval 30
hide-password
ipparam (hidden by pptpconfig)
proxyarp
nobsdcomp
nodeflate
require-mppe
require-mppe-128
noipx
using channel 22
Using interface ppp0
pptpconfig: monitoring interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x473c8a6d> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfNak id=0x1 <auth chap MS-v2>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x473c8a6d> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x2 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfNak id=0x2 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x3 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfNak id=0x3 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x4 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfNak id=0x4 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x5 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfNak id=0x5 <auth chap MS-v2>]
rcvd [LCP ConfReq id=0x6 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0x6 <auth chap MS>]
rcvd [LCP ConfReq id=0x7 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0x7 <auth chap MS>]
rcvd [LCP ConfReq id=0x8 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0x8 <auth chap MS>]
rcvd [LCP ConfReq id=0x9 <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0x9 <auth chap MS>]
rcvd [LCP ConfReq id=0xa <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0xa <auth chap MS>]
rcvd [LCP ConfReq id=0xb <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0xb <auth chap MS>]
rcvd [LCP ConfReq id=0xc <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0xc <auth chap MS>]
rcvd [LCP ConfReq id=0xd <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0xd <auth chap MS>]
rcvd [LCP ConfReq id=0xe <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0xe <auth chap MS>]
rcvd [LCP ConfReq id=0xf <auth chap MS> <magic 0x7f4d3e4e>]
sent [LCP ConfRej id=0xf <auth chap MS>]
rcvd [LCP TermReq id=0x10]
sent [LCP TermAck id=0x10]
Script pptp (hidden by pptpconfig) --nolaunchpppd  finished (pid 22514), status = 0x0
Modem hangup
Connection terminated.
# route -n (after pppd exit)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
# route -n (after completion)
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0


```

---

### Post by emulsion on 2006-10-20
Same error message here...I see lots of threads with this question but none with the answer.  this seems like the common/key error message:

```

Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/1
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1
```

---

### Post by nivannick on 2006-11-24
I was having the same problem too, albeit on Debian Sid rather than Ubuntu.

I fixed this by opening port 1723 (PPTP) on my router (I am NAT'd behind it). For my router, this was done in its "Port Triggering" page, if that helps anybody. ("The Router will watch the outgoing data for specific port. If the PC behind the router sends the data witch is matching the 'Port Triggering table' through the router, the router will record it. When the requested incoming data returns, the router will send it to the PC by way of Port Triggering table rule.")

---

### Post by cmonspike on 2007-02-16
**[SIZE="2"]This is definitely the solution as reported by nivannick. A trace using tcpdump showed that the ipaddress being presented to the remote vpn server for negotiation is the "INTERNAL" ip address of the calling PC, which of course will not work. By using port triggering on your router for port 1723 the vpn server responds to the public ip address of your router which then knows to forward the response back to your pc for the vpn call and the connection is then established[/SIZE].**

---

### Post by maxamillion on 2007-02-16
[http://ubuntuforums.org/showthread.php?t=91249](http://ubuntuforums.org/showthread.php?t=91249)

[http://ubuntuforums.org/showthread.php?t=28396](http://ubuntuforums.org/showthread.php?t=28396)

---

### Post by milanfujda on 2007-07-20
Hello,
I was really happy to find this request since I need VPN working to use wi-fi connection at my university. But I really do not have any idea how to trigger the requested port 1723. I have already found, what triggering is, what forwarding is etc, and understand in principle what is it about, but do not have any idea, how to do it.
The only request I found was like this:

sudo iptables -I INPUT -p tcp --dport <1723> -j ACCEPT
sudo iptables -I INPUT -p udp --dport <1723> -j ACCEPT     

And the answer from my computer looked like this:

bash: syntax error near unexpected token `1723'

So I still completely do not know, what to do to connect through VPN.
Can anybody help?

---

### Post by Stradivarius on 2007-09-06
I am new to Ubuntu (Feisty), but am very experienced with PPTP in Windows.  I have a Windows Small Business Server 2003 that I can VPN to all day with Windows, so port forwarding is definitely not the issue (TCP 1723 & GRE forwarded in IPCOP).  I have set up my VPN settings in Network Manager and they work perfectly inside the firewall.  I cannot, however, connect from outside the firewall.  Again, my Windows installation on the same machine, using the same hardware, works outside the firewall every time.  Any ideas?

---


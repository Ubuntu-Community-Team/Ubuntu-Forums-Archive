---
title: "pptp works sometime but sometimes don't"
date: 2005-12-10
forum: Desktop Environments
---

### Post by jasplund on 2005-12-10
I'm having problems with pptpconfig. I need VPN to access my e-mail from my work. It sometimes work sometimes it don't sometimes I can only access the intranet but not internet and sometimes I can't access any of them.

and it can suddenly stop working


here's what pptpconfig gives me:
"Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/0
MPPE 128-bit stateless compression enabled
Cannot determine ethernet address for proxy ARP
local  IP address 128.39.175.11
remote IP address 128.39.175.5
pptpconfig: pppd process exit status 0 (started)
ip route add 128.39.175.2 via 192.168.0.1 dev eth0  src 192.168.0.2
pptpconfig: routes added to remote networks
ip route replace default dev 'ppp0'
pptpconfig: default route changed to use tunnel
pptpconfig: connected
ping -c 5 128.39.175.5
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
PING 128.39.175.5 (128.39.175.5) 56(84) bytes of data.

--- 128.39.175.5 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4001ms

pptpconfig: command failed, exit code 1"

---

### Post by jasplund on 2005-12-10
"sudo pppd call umb dump debug logfd 2 nodetach" gives me:



pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
linkname umb            # (from /etc/ppp/peers/umb)
dump            # (from command line)
noauth          # (from /etc/ppp/peers/umb)
refuse-eap              # (from /etc/ppp/peers/umb)
name johaas             # (from /etc/ppp/peers/umb)
remotename umb          # (from /etc/ppp/peers/umb)
                # (from /etc/ppp/options)
pty pptp ansatt.vpn.umb.no --nolaunchpppd               # (from /etc/ppp/peers/u mb)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam umb             # (from /etc/ppp/peers/umb)
proxyarp                # (from /etc/ppp/options)
require-mppe            # (from /etc/ppp/peers/umb)
mppe-stateful           # (from /etc/ppp/peers/umb)
noipx           # (from /etc/ppp/options)
using channel 8
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x95fb6cea> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x0 <mru 1400> <auth eap> <magic 0x17c97baf> <pcomp> <accom p> <callback CBCP> <mrru 1614> <endpoint [local:0f.42.d1.62.87.9f.4a.4a.82.e5.a3 .b1.ec.3b.cb.04.00.00.00.00]> < 17 04 0b 0a>]
sent [LCP ConfRej id=0x0 <callback CBCP> <mrru 1614> < 17 04 0b 0a>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x95fb6cea> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1400> <auth eap> <magic 0x17c97baf> <pcomp> <accom p> <endpoint [local:0f.42.d1.62.87.9f.4a.4a.82.e5.a3.b1.ec.3b.cb.04.00.00.00.00] >]
sent [LCP ConfNak id=0x1 <auth chap MD5>]
rcvd [LCP ConfReq id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x17c97baf> <pcomp>  <accomp> <endpoint [local:0f.42.d1.62.87.9f.4a.4a.82.e5.a3.b1.ec.3b.cb.04.00.00 .00.00]>]
sent [LCP ConfAck id=0x2 <mru 1400> <auth chap MS-v2> <magic 0x17c97baf> <pcomp>  <accomp> <endpoint [local:0f.42.d1.62.87.9f.4a.4a.82.e5.a3.b1.ec.3b.cb.04.00.00 .00.00]>]
sent [LCP EchoReq id=0x0 magic=0x95fb6cea]
rcvd [CHAP Challenge id=0x0 <fe22e4d8b1a4f3713e5d8a6fb1af67a5>, name = "VPN-ANS" ]
sent [CHAP Response id=0x0 <5b1350dbe448801e415d3a40871ef1d00000000000000000131c 32896b485c1bc6494c153622ea8140b65a036682a47700>, name = "johaas"]
rcvd [LCP EchoRep id=0x0 magic=0x17c97baf]
rcvd [CHAP Success id=0x0 "S=9A9851F400825663B3B165F68114B2234233A4CF"]
sent [CCP ConfReq id=0x1 <mppe +H -M +S +L -D -C>]
rcvd [CCP ConfReq id=0x4 <mppe +H +M +S +L -D +C>]
sent [CCP ConfNak id=0x4 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x5 <addr 128.39.175.5>]
sent [IPCP TermAck id=0x5]
rcvd [CCP ConfNak id=0x1 <mppe +H -M +S -L -D -C>]
sent [CCP ConfReq id=0x2 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfReq id=0x6 <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x6 <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x2 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x2 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <addr 128.39.175.15>]
sent [IPCP ConfReq id=0x3 <addr 128.39.175.15>]
rcvd [IPCP ConfAck id=0x3 <addr 128.39.175.15>]
rcvd [IPCP ConfReq id=0x7 <addr 128.39.175.5>]
sent [IPCP ConfAck id=0x7 <addr 128.39.175.5>]
Cannot determine ethernet address for proxy ARP
local  IP address 128.39.175.15
remote IP address 128.39.175.5
Script /etc/ppp/ip-up started (pid 8655)
Script /etc/ppp/ip-up finished (pid 8655), status = 0x0

---

### Post by jasplund on 2005-12-12
anyone?

---

### Post by ironphil on 2006-02-22
I have the same problem. It used to work, now nothing... And I can't find any solution, I have searched intensively for the last three days but unfortunatly, it seem we are the only ones to have this problem!

---


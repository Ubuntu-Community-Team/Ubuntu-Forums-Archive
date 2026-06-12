---
title: "[SOLVED] Someone tried to use my box as a DDOS attack vector"
date: 2007-09-16
forum: Forum Feedback &amp; Help
---

### Post by nowshining on 2007-09-16
```

Sep 16 07:54:54 localhost kernel: [10720.148519] Possible DRDOS TCP attempt: IN=ppp0 OUT= MAC= SRC=91.189.94.186 DST=4.245.99.93 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=8432 DF PROTO=TCP SPT=80 DPT=36843 WINDOW=1741 RES=0x00 ACK URGP=0 

```

edit: :) i am using arno-iptables-firewall

---

### Post by nowshining on 2007-09-16
```

% This is the RIPE Whois query server #2.
% The objects are in RPSL format.
%
% Rights restricted by copyright.
% See http://www.ripe.net/db/copyright.html

% Note: This output has been filtered.
%       To receive output for a database update, use the "-B" flag

% Information related to '91.189.88.0 - 91.189.95.255'

inetnum:        91.189.88.0 - 91.189.95.255
netname:        CANONICAL-CORE
descr:          Canonical Ltd
country:        GB
org:            ORG-CAN1-RIPE
admin-c:        KT1076-RIPE
admin-c:        JT2256-RIPE
tech-c:         KT1076-RIPE
tech-c:         JT2256-RIPE
status:         ASSIGNED PI
mnt-by:         RIPE-NCC-HM-PI-MNT
mnt-lower:      RIPE-NCC-HM-PI-MNT
mnt-by:         CANONICAL-MNT
mnt-routes:     CANONICAL-MNT
mnt-domains:    CANONICAL-MNT
source:         RIPE # Filtered

organisation:   ORG-CAN1-RIPE
org-name:       Canonical Ltd
org-type:       OTHER
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
addre-mail:         info@canonical.com
mnt-ref:        CANONICAL-MNT
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered

person:         James Troup
address:        Canonical Ltd.
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
phone:          +441624643643
nic-hdl:        JT2256-RIPE
mnt-by:         JT2256-MNT
source:         RIPE # Filtered

person:         Karl Tilbury
address:        Canonical Ltd.
address:        1 Circular Road
address:        Douglas
address:        Isle of Man
address:        IM1 1AF
mnt-by:         KT1076-MNT
phone:          +441624643643
nic-hdl:        KT1076-RIPE
source:         RIPE # Filtered

% Information related to '91.189.88.0/21AS41231'

route:          91.189.88.0/21
descr:          Canonical Route Object
origin:         AS41231
mnt-by:         CANONICAL-MNT
source:         RIPE # Filtered



```

---

### Post by nowshining on 2007-09-16
no i just thought it was funny esp after whoising it and seeing it's the ubuntu team..lolz.. :P

---

### Post by nowshining on 2007-09-16
strange tho My whole log consists of and has been doing it lately of..

```


Sep 16 07:21:09 localhost kernel: [ 8700.432290] PPP: VJ uncompressed error
Sep 16 07:25:15 localhost kernel: [ 8945.924395] PPP: VJ uncompressed error
Sep 16 07:25:16 localhost kernel: [ 8946.977004] PPP: VJ uncompressed error
Sep 16 07:25:20 localhost kernel: [ 8950.759614] PPP: VJ uncompressed error
Sep 16 07:25:29 localhost kernel: [ 8960.112476] nf_conntrack: table full, dropping packet.
Sep 16 07:25:30 localhost kernel: [ 8960.511444] PPP: VJ uncompressed error
Sep 16 07:25:30 localhost kernel: [ 8960.519435] nf_conntrack: table full, dropping packet.
Sep 16 07:25:31 localhost kernel: [ 8961.690914] nf_conntrack: table full, dropping packet.
Sep 16 07:25:31 localhost kernel: [ 8961.756441] nf_conntrack: table full, dropping packet.
Sep 16 07:25:31 localhost kernel: [ 8961.800472] nf_conntrack: table full, dropping packet.
Sep 16 07:25:32 localhost kernel: [ 8962.151455] nf_conntrack: table full, dropping packet.
Sep 16 07:25:34 localhost kernel: [ 8964.481593] nf_conntrack: table full, dropping packet.
Sep 16 07:25:34 localhost kernel: [ 8964.681102] nf_conntrack: table full, dropping packet.
Sep 16 07:25:34 localhost kernel: [ 8964.748932] nf_conntrack: table full, dropping packet.
Sep 16 07:25:34 localhost kernel: [ 8964.792819] nf_conntrack: table full, dropping packet.
Sep 16 07:25:35 localhost kernel: [ 8965.143955] nf_conntrack: table full, dropping packet.
Sep 16 07:25:40 localhost kernel: [ 8970.666262] printk: 1 messages suppressed.
Sep 16 07:25:40 localhost kernel: [ 8970.666268] nf_conntrack: table full, dropping packet.
Sep 16 07:25:47 localhost kernel: [ 8977.996082] PPP: VJ uncompressed error
Sep 16 07:25:49 localhost kernel: [ 8979.578901] printk: 3 messages suppressed.
Sep 16 07:25:49 localhost kernel: [ 8979.578907] nf_conntrack: table full, dropping packet.
Sep 16 07:25:52 localhost kernel: [ 8982.568750] nf_conntrack: table full, dropping packet.
Sep 16 07:25:56 localhost kernel: [ 8986.945904] printk: 4 messages suppressed.
Sep 16 07:25:56 localhost kernel: [ 8986.945909] nf_conntrack: table full, dropping packet.
Sep 16 07:26:07 localhost kernel: [ 8997.679463] printk: 2 messages suppressed.
Sep 16 07:26:07 localhost kernel: [ 8997.679469] nf_conntrack: table full, dropping packet.
Sep 16 07:26:09 localhost kernel: [ 8999.829969] nf_conntrack: table full, dropping packet.
Sep 16 07:26:10 localhost kernel: [ 9000.671863] nf_conntrack: table full, dropping packet.
Sep 16 07:26:16 localhost kernel: [ 9006.577222] nf_conntrack: table full, dropping packet.
Sep 16 07:26:24 localhost kernel: [ 9014.275197] PPP: VJ uncompressed error
Sep 16 07:27:37 localhost kernel: [ 9086.898065] PPP: VJ uncompressed error
Sep 16 07:30:38 localhost kernel: [ 9267.602108] PPP: VJ uncompressed error
Sep 16 07:53:52 localhost kernel: [10658.876405] PPP: VJ uncompressed error
Sep 16 07:53:53 localhost kernel: [10659.291384] PPP: VJ uncompressed error
Sep 16 07:54:02 localhost kernel: [10667.973847] PPP: VJ uncompressed error
Sep 16 07:54:20 localhost kernel: [10685.674662] PPP: VJ uncompressed error
Sep 16 07:54:54 localhost kernel: [10720.148519] Possible DRDOS TCP attempt: IN=ppp0 OUT= MAC= SRC=91.189.94.186 DST=4.245.99.93 LEN=64 TOS=0x00 PREC=0x00 TTL=55 ID=8432 DF PROTO=TCP SPT=80 DPT=36843 WINDOW=1741 RES=0x00 ACK URGP=0 


```

but why canonical ??

---

### Post by happy-and-lost on 2007-09-16
Maybe it was part of the DDOS attack on Automatix...

It's a conspiracy, I tell you!

---

### Post by nowshining on 2007-09-16
oh as for the vj uncompressed error and ip packets dropped i think I know what's causing that - ipblock - it does this on me as I have it setup to startup and do it's stuff in the background - :) and have port 80 and others unlocked i just noticed that also i have been noticing slowdowns of the forums on my side lately or it could be due to the gutsy wvdial - I did set arno-iptables to allow only 48 connections tho not the default 16000 + which I don't need on dialup..


however as for the drdos attack i don't know - it happened a few more time and I was cut off the forums - google worked fine when i went to it..odd really..

---

### Post by chrisccoulson on 2007-09-16
My log seems to be full of these too. Same IP address as well

---

### Post by nowshining on 2007-09-16
wow it seems like something is wrong on the canonical side then this would/will prove it's just not me that it is happening too, also they keep coming after like 10 minutes or so on my side.

---

### Post by n3tfury on 2007-09-16
do you bake cookies on that tinfoil?

---

### Post by nowshining on 2007-09-16
n3tfury ??

---

### Post by PriceChild on 2007-09-16
The ip mentioned here is the new UbuntuForums.org ip as of a day or two ago... I'm moving this to Forum Feedback and Help and will notify an admin.

---

### Post by jdong on 2007-09-16
Very interesting.... The forums did relocate to a new host recently to expand our capacity. Looks like there might be some quirks with the setup.

Everyone, please remain calm, I'll see if either me or Ryan can get in contact with a server admin to figure out what is causing these alerts.

As far as a DRDOS, I can assure you nobody at Canonical or the forums is trying to cause a DRDOS attack on you... It's most likely a false positive resulting from some sort of screwed up packet.

---

### Post by nowshining on 2007-09-16
strange it quit after posting that

Sep 16 08:38:10 localhost kernel: [13309.983105] nf_conntrack: table full, dropping packet. 


was the last log and where i am it's now about 9:30 so about over half and hour ago..odd tho..

---

### Post by nowshining on 2007-09-16
and lolz I figured that :) if anyone wants them I  can hand over all my kern.log files also so far I've been able to surf the forums okay because when that did happen i would lose connection to the forums..

---

### Post by nowshining on 2007-09-16
oh and as for the last drdos attack or possibly one was

```
Sep 16 08:35:20 localhost kernel: [13140.615071] Possible DRDOS TCP attempt: IN=ppp0 OUT= MAC= SRC=91.189.94.186 DST=4.245.99.93 LEN=52 TOS=0x00 PREC=0x00 TTL=55 ID=22169 DF PROTO=TCP SPT=80 DPT=58962 WINDOW=1802 RES=0x00 ACK URGP=0 
```

---

### Post by jdong on 2007-09-16
I talked to James Troup, the server admin, and he says it's an overzealous firewall rule too. I took a look at this firewall script, and here's the responsible rule:

```


    $IPTABLES -A EXT_INPUT_CHAIN -p tcp ! --dport 2049 -m multiport --sports 20,21,22,23,80,110,143,443,993,995 \
      -m limit --limit 6/h --limit-burst 1 -j LOG --log-level $LOGLEVEL --log-prefix "Possible DRDOS TCP attempt: "

```


It's simply looking for more than 6 packets per hour that are not coming from  ports 20,21,22..... to port 2049


This rule is pretty easy for legit traffic to trip. It's not a sign of an attack. There is nothing to worry about.

---

### Post by nowshining on 2007-09-16
so it's a problem with arno-iptables-firewall

so i need to get ahold of the author then and have him look at it or should I just disable it??

---

### Post by nowshining on 2007-09-16
as for the other erros I changed conntrack in the config from 48 to over 1000 :) seems like the rest of the errors went away..

---

### Post by jdong on 2007-09-16
> **nowshining said:**
> so it's a problem with arno-iptables-firewall

so i need to get ahold of the author then and have him look at it or should I just disable it??

Well I wouldn't say it's a "problem"; every signature-based rule needs to balance the probability of catching an attack with the probability of generating an annoying number of false alerts.... This seems like one of those rules that'll generate false positives.

It's probably better to just keep it on and ignore these alerts unless you get an absurd number of them from some unknown site.

---

### Post by Frak on 2007-09-16
I was wondering about that, OS X gave me the same warning.

---

### Post by nowshining on 2007-09-16
already then & i guess Frak that answers both of our questions :P

---


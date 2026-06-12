---
title: "Conky problem"
date: 2012-07-07
forum: Desktop Environments
---

### Post by netgiga on 2012-07-07
How can i add download speed and names of 3 processes that are using most of network bandwidth in conky?

---

### Post by jmfal on 2012-07-07
Welcome to Ubuntu

Here is the network section of my conky

```
     ${color 800000}NETWORK ${hr 2}$color
Local Ip: #${addr eth0}
Down: $color${downspeed eth0}k/s ${alignr}Up: ${upspeed eth0}k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth1
25,140 000000 00ff00}
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}     
```

You may have to move things around , our conkys might be different sizes.
I commented out my IP address , you can remove the # and it should register

---

### Post by netgiga on 2012-07-07
Thanks.I already made something similar but i don't know how to monitor processes which are using most of network bandwidth

---

### Post by jmfal on 2012-07-07
There is a humongous "post your conky" thread in the community cafe section of the forum, you should post your question there.

You don't get any beans for posting there, but I'm sure somebody will help.

Good Luck

---


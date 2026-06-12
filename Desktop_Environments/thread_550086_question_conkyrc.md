---
title: "question conkyrc"
date: 2007-09-13
forum: Desktop Environments
---

### Post by cwhisperer on 2007-09-13
Hi, here a part of my conkyrc file

${color #5b6dad}Networking eth0:
${color #5b6dad} Down:${color #7f8ed3} ${downspeed eth0} k/s${color #5b6dad}${offset 80}Up:${color #7f8ed3} ${upspeed eth0} k/s
${color #000000} ${downspeedgraph eth0 32,150 000000 7f8ed3} ${color #000000}${upspeedgraph eth0 32,150 000000 7f8ed3}
${color #5b6dad} Address: ${color #7f8ed3}${addr eth0}${alignr}${color #5b6dad}TCP Connections: ${color #7f8ed3}${tcp_portmon 1 65535 count}

${color #5b6dad}Networking eth1:
${color #5b6dad} Down:${color #7f8ed3} ${downspeed eth1} k/s${color #5b6dad}${offset 80}Up:${color #7f8ed3} ${upspeed eth1} k/s
${color #000000} ${downspeedgraph eth1 32,150 000000 7f8ed3} ${color #000000}${upspeedgraph eth1 32,150 000000 7f8ed3}
${color #5b6dad} Address: ${color #7f8ed3}${addr eth1}${alignr}${color #5b6dad}TCP Connections: ${color #7f8ed3}${tcp_portmon 1 65535 count}

How to display only the one which is currently used?
Regards

---

### Post by cwhisperer on 2007-09-14
another question ;)

is it possible to display all the wireless networks available?

regards

---


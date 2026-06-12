---
title: "Automate a script (sysctl.conf) during startup"
date: 2009-01-04
forum: General Help
---

### Post by adriant42 on 2009-01-04
Hello,

I know this has been discussed lots of time everywhere, but seems I can't get this one work.

Let me start with a quick background. I recently fixed intermittent problems with my internet during downloads (big files). I added this script to /etc/sysctl.conf to modify the TCP window size settings

```

net.core.rmem_default = 262144
net.core.rmem_max = 262144
net.core.wmem_default = 262144
net.core.wmem_max = 262144
net.ipv4.tcp_wmem = 4096 87380 262144
net.ipv4.tcp_rmem = 4096 87380 262144
net.ipv4.tcp_mem = 524288 524288 262144
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

```

To make this work, I have to restart by typing

```

sudo sysctl -p

```

This works like a charm and this where my problem starts. It seems that I have to manually type the restart command, otherwise my intermittent problema arise.

So, I was thinking why not put the command in /etc/init.d/ and ran update-rc.d command --> did not work (not sure why) and I still need to manually type the restart command

Did another thing, put the script in anacrontab --> did not work, anacrontab won't let me to set to run a job on every restart. It only works the first time. When I restart again, it will remember that the job has been executed earlier. 

I also tried putting the script in the root's crontab, but this is still not the most efficient solution. The most frequent time that I can set is every hour. This doesn't guarantee the script to be run immediately after restart. Also, why do I want to run this script every hour if running once is sufficient.

Any suggestions on how to make this work? Also, out of curiosity, why doesn't /etc/sysctl.conf automatically start during startup? Is it because there are other tcp settings that might conflict?

As always, thanks in advance,

---

### Post by adriant42 on 2009-01-04
I added the sleep command in my script and put it under /etc/init.d/

```

sleep 1m
sudo sysctl -p
exit 0

```

Then, I typed

```

sudo update-rc.d tcp start 99 2 3 4 5 .

```

This seems to work!!! The sleep command will put a delay and the sysctl -p somehow works only after I connect to my home wireless network. One minute is a good setting for me to make sure I connect first.

I'll post another if for some reasons this stops working.

Cheers

---


---
title: "How do I set this settings to sysctl.conf permanently?"
date: 2009-03-25
forum: General Help
---

### Post by synergycheery on 2009-03-25
/etc/sysctl.conf

echo 49152 > /proc/sys/fs/file-max
echo 262144 > /proc/sys/net/core/rmem_default
echo 262144 > /proc/sys/net/core/rmem_max
echo 262144 > /proc/sys/net/core/wmem_default
echo 262144 > /proc/sys/net/core/wmem_max
echo 4096 87380 8388608 > /proc/sys/net/ipv4/tcp_rmem
echo 4096 65536 8388608 > /proc/sys/net/ipv4/tcp_wmem
echo 4096 4096 4096 > /proc/sys/net/ipv4/tcp_mem
echo 1 > /proc/sys/net/ipv4/tcp_low_latency
echo 4000 > /proc/sys/net/core/netdev_max_backlog
echo 1024 65000 > /proc/sys/net/ipv4/ip_local_port_range
echo 16384 > /proc/sys/net/ipv4/tcp_max_syn_backlog

---

### Post by oldos2er on 2009-03-25
```
gksu gedit /etc/sysctl.conf
```
or
```
sudo nano /etc/sysctl.conf
```

 Or install the package nautilus-gksu, restart X, then in Nautilus right-click on the file, choose 'Open as administrator'.

---


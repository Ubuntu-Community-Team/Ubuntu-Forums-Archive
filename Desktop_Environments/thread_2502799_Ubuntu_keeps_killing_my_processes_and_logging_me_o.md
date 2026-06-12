---
title: "Ubuntu keeps killing my processes and logging me out"
date: 2024-11-29
forum: Desktop Environments
---

### Post by ckao1030 on 2024-11-29
Ubuntu 24.04.1 LTS Desktop. I'm running a process that uses a large amount of swap disk. The process runs for around an hour and runs fine using 128 out of 128GB RAM and 256 GB out of 2 TB swap disk NVME. Then near the end when swap usage increases to around 300 GB the session ends and I'm logged out. I don't think it's a hardware issue as I changed out the RAM and NVME. AUto Screen lock and suspend are disabled. Swappiness at 60.


How can I stop getting the session terminated? Thanks!




ERRORS from log:


novato@novato-Super-Server:~$ sudo grep --text -ri 'killed process' /var/log/
/var/log/syslog:2024-11-28T23:54:31.369757-08:00 novato-Super-Server kernel: Out of memory: Killed process 6174 (python) total-vm:77951424kB, anon-rss:28399472kB, file-rss:116736kB, shmem-rss:2304kB, UID:1000 pgtables:70004kB oom_score_adj:200
/var/log/syslog:2024-11-28T23:57:43.092454-08:00 novato-Super-Server kernel: Out of memory: Killed process 8376 (python) total-vm:75541232kB, anon-rss:27676500kB, file-rss:119808kB, shmem-rss:9984kB, UID:1000 pgtables:70220kB oom_score_adj:200
/var/log/syslog:2024-11-29T00:01:16.232384-08:00 novato-Super-Server kernel: Out of memory: Killed process 10445 (python) total-vm:75645144kB, anon-rss:28301288kB, file-rss:114432kB, shmem-rss:2304kB, UID:1000 pgtables:69980kB oom_score_adj:200
/var/log/syslog:2024-11-29T00:29:10.753860-08:00 novato-Super-Server kernel: Out of memory: Killed process 24363 (swapoff) total-vm:18292kB, anon-rss:0kB, file-rss:768kB, shmem-rss:0kB, UID:0 pgtables:60kB oom_score_adj:200
/var/log/syslog:2024-11-29T00:29:10.759830-08:00 novato-Super-Server kernel: Out of memory: Killed process 12190 (python) total-vm:213823008kB, anon-rss:22247060kB, file-rss:122112kB, shmem-rss:14592kB, UID:1000 pgtables:263252kB oom_score_adj:200
/var/log/journal/9c539c2437834f84bb1175357351d30c/user-1000.journal:9P


Aready tried to turn off OOM killer.


Tried this already:




Kernel-level modifications:


bash


Copy


# Modify sysctl settings
sudo sysctl -w vm.overcommit_memory=2
sudo sysctl -w vm.overcommit_ratio=100


# Make permanent by editing /etc/sysctl.conf
sudo nano /etc/sysctl.conf
# Add these lines:
vm.overcommit_memory = 2
vm.overcommit_ratio = 100






Adjust OOM killer behavior for specific processes:


bash


Copy


# Lower the OOM score for critical processes
# This makes them less likely to be killed
sudo echo -999 > /proc/$(pidof your_process)/oom_score_adj






Add kernel parameter at boot:


bash


Copy


# Edit GRUB configuration
sudo nano /etc/default/grub


# Add to GRUB_CMDLINE_LINUX_DEFAULT:
oom_kill_disable=1

---

### Post by ian-weisser on 2024-11-29
The only real way to "turn off" the OOM killer is to add memory or swap.
The OOM killer isn't there for fun. It's the last line of defense before you exhaust your memory --including swap-- and crash the entire system.

Your encounters with OOM-killer suggest you did not add enough swap yet.

---


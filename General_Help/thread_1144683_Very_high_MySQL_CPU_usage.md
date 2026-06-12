---
title: "Very high MySQL CPU usage"
date: 2009-05-01
forum: General Help
---

### Post by kaput on 2009-05-01
I've posted a bug about this ( [https://bugs.launchpad.net/bugs/370058](https://bugs.launchpad.net/bugs/370058) ), but figured I'd check in here to see if anyone has any answers. It's on a system installed via Mythbuntu, but seems to be a general MySQL issue in Jaunty.

-----

Set up a combo FE/BE on a fresh install of Mythbuntu 9.04 on an Acer
X1200 (2300+ Sempron X2 / 3 GB RAM / GeForce 8200 / HDMI).

Everything works fine, minus very high CPU usage for the 'mysqld_safe'
process. I've ran the 'optimize_mythdb.pl' script, as well as running
MySQL repairs. Even when MythTV backend and Apache are stopped, the
process pegs one of my cores at 100%.

Output from syslog at start of process, with no further data following
for five minutes following start:

*****
Apr 30 15:14:14 mythtv mysqld_safe[32560]: started
Apr 30 15:14:14 mythtv mysqld[32563]: 090430 15:14:14  InnoDB: Started; log sequence number 0 112623
Apr 30 15:14:14 mythtv mysqld[32563]: 090430 15:14:14 [Note] /usr/sbin/mysqld: ready for connections.
Apr 30 15:14:14 mythtv mysqld[32563]: Version: '5.0.75-0ubuntu10'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Apr 30 15:14:15 mythtv /etc/mysql/debian-start[32601]: Upgrading MySQL tables if necessary.
Apr 30 15:14:15 mythtv /etc/mysql/debian-start[32607]: Looking for 'mysql' as: /usr/bin/mysql
Apr 30 15:14:15 mythtv /etc/mysql/debian-start[32607]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Apr 30 15:14:15 mythtv /etc/mysql/debian-start[32607]: This installation of MySQL is already upgraded to 5.0.75, use --force if you still need to run mysql_upgrade
Apr 30 15:14:15 mythtv /etc/mysql/debian-start[32612]: Checking for insecure root accounts.
Apr 30 15:14:15 mythtv /etc/mysql/debian-start[32616]: Triggering myisam-recover for all MyISAM tables
*****

Process info:

*****
 PID    USER    PR  NI  VIRT  RES  SHR S %CPU  %MEM    TIME+  COMMAND          
 2730    root      20   0   1872   496   468  R  100      0.0         1240:18  mysqld_safe  
*****

Again, this is with MythTV backend/frontend and Apache (for MythWeb) all
stopped.

I'm more than happy to do any troubleshooting/testing as necessary.

---


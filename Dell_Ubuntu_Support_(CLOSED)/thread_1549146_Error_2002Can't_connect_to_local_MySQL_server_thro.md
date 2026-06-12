---
title: "Error: 2002Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld"
date: 2010-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by l0uismustdie on 2010-08-09
Hello, I am running a Dell desktop with Ubuntu 10.04 with mysql  Ver 14.14 Distrib 5.1.41, for debian-linux-gnu (i486).  As of yesterday mysql was running with no problems and the only thing that I have changed since that time (I believe) is that I ran:

```

sudo aptitude update
sudo aptitude safe-upgrade

```Now, whenever I attempt to do anything with mysql, including connecting to the server off of which I work, I encounter the error:
```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```I have done some research on other forums and throughout this forum but haven't found the solution yet.  I have tried:
```

sudo find / -name mysqld.sock -print

```with no luck.  I have also looked for /var/run/mysqld which doesn't exist on my machine.

Thank you in advance for any assistance anyone out there can offer.
Josh

---

### Post by DaithiF on 2010-08-09
Hi,
try:
```
sudo service mysql start
```

what happens?  can you connect after running this?

thanks

---

### Post by l0uismustdie on 2010-08-09
Yep.  That did it.  But...wha?!?! The mysql service was turned off? Could this have happened from the updates?  Will this continue to happen?

Thanks again!

---

### Post by DaithiF on 2010-08-09
can you post the contents of /etc/init/mysql.conf please

---

### Post by l0uismustdie on 2010-08-09
here you go:
```

# MySQL Service

description     "MySQL Server"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (net-device-up
          and local-filesystems
      and runlevel [2345])
stop on runlevel [016]

respawn

env HOME=/etc/mysql
umask 007

pre-start script
    #Sanity checks
    [ -r $HOME/my.cnf ]
    [ -d /var/run/mysqld ] || install -m 755 -o mysql -g root -d /var/run/mysqld
    # Load AppArmor profile
    if aa-status --enabled 2>/dev/null; then
        apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld || true
    fi
    LC_ALL=C BLOCKSIZE= df --portability /var/lib/mysql/. | tail -n 1 | awk '{ exit ($4<4096) }'
end script

exec /usr/sbin/mysqld

post-start script
    for i in `seq 1 30` ; do
        /usr/bin/mysqladmin --defaults-file="${HOME}"/debian.cnf ping && {
            exec "${HOME}"/debian-start
            # should not reach this line
            exit 2
        }
        sleep 1
    done
    exit 1
end script

```

---

### Post by DaithiF on 2010-08-10
ok, that looks fine.  so next thing to check ... can you post the output from:
grep bind-address /etc/mysql/my.cnf
and
cat /etc/network/interfaces

thanks

---

### Post by l0uismustdie on 2010-08-10
Sure thing:
```

boincuser@lorax:~$ grep bind-address /etc/mysql/my.cnf 
bind-address        = 127.0.0.1
boincuser@lorax:~$ cat /etc/network/interfaces
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#    address 192.168.2.3
#    netmask 255.255.255.0
#    gateway 98.218.244.1

```

THanks again

---

### Post by DaithiF on 2010-08-10
it seems strange to me that your interfaces file doesn't contain an entry for loopback (your mysql is listening for connections on the loopback ip address), so I would add these 2 lines to the top of the /etc/network/interfaces file:
auto lo
iface lo inet loopback
I'm not convinced thats really the problem though, since mysql starts ok for you manually post-boot.  However, give it a go, reboot, see if you can connect with mysql, and if not, then grep for any error messages in the logs:
```
sudo grep mysql /var/log/*

```

---

### Post by l0uismustdie on 2010-08-11
Everything seems to be in order and working correctly...thanks again.

---

### Post by c2duo on 2011-08-12
same problem help please !!

---

### Post by ankish on 2013-02-13
> **DaithiF said:**
> it seems strange to me that your interfaces file doesn't contain an entry for loopback (your mysql is listening for connections on the loopback ip address), so I would add these 2 lines to the top of the /etc/network/interfaces file:
auto lo
iface lo inet loopback
I'm not convinced thats really the problem though, since mysql starts ok for you manually post-boot.  However, give it a go, reboot, see if you can connect with mysql, and if not, then grep for any error messages in the logs:
```
sudo grep mysql /var/log/*

```

I'm new user for ubuntu. i dont knw anything about that, but i executed some programs right now. I'm also facing the same problem like you and i have one more major issue that is 2 mysql's running in my pc. old socket file in /etc/bin/mysql directory and new one is in /opt/lampp/bin/mysql directory. now how can i connect from ruby program to this new socket file path. 
can any one help me out......:confused:

Thank you in advance.
ankish

---


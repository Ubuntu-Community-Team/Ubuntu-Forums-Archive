---
title: "Xsupplicant - parse error"
date: 2006-08-13
forum: Desktop Environments
---

### Post by tjansson on 2006-08-13
I just arrived at a new university and they use 802.1X and PEAP for authenticating me when connecting my computer at my dorm. I have installed xsupplicant and configured /etc/xsupplicant/xsupplicant.conf so it reads:

```

### GLOBAL SECTION
network_list = all
default_netname = default<F11>
startup_command = <BEGIN_COMMAND>ifconfig eth1 allmulti 0.0.0.0 up<END_COMMAND>
first_auth_command = <BEGIN_COMMAND>dhclient eth1<END_COMMAND>
reauth_command = <BEGIN_COMMAND>dhclient -r; dhclient<END_COMMAND>
logfile = /var/log/xsupplicant.log
deny_interfaces = lo,cipsec0, sit0
### NETWORK SECTION
default
{
        type = wired
        allow_types = all
        identity = <BEGIN_ID>something<END_ID>

        eap-peap {
                root_cert = NONE
                chunk_size = 1398
                random_file = /dev/urandom
                session_resume = yes
                allow_types = all

                eap-mschapv2 {
                username = <BEGIN_UNAME>something<END_UNAME>
                password = <BEGIN_PASS>something<END_PASS>
                }
        }
}

```

But when I try to start xsupplicant I get parsing errors:
```

xdirac xsupplicant # xsupplicant -i eth1 -d 7 -f
Using default config path!
<>Error in (null), at line 4:
syntax error:

startup_command = <BEGIN_COMMAND>ifconfig eth1 allmulti 0.0.0.0 up<END_COMMAND>
               ^
General Parse error!
There was a problem with the config file.  We cannot continue.

```

The next thing I try is to out-comment the startup_command, but then it just moves along and complains about the reauth_command? 

Why does xsupplicant say that there is a parseing error. The config file seems fine to me and is similar to the default ubuntu config file?

---

### Post by tjansson on 2006-08-15
I seems that the tags to begin and end commands and other stuff is not in use anymore, which makes the current exable file useless? I got it working now by remove the syntax all together:
```

### GLOBAL SECTION
network_list = all
default_netname = default
logfile = /var/log/xsupplicant.log
### NETWORK SECTION
default
{
        type = wired
        allow_types = all
        identity = "something"

        eap-peap {
                root_cert = NONE
                chunk_size = 1398
                random_file = /dev/urandom
                session_resume = yes
                allow_types = all

        eap-mschapv2 {
                        username = "something"
                        password = "something"
                }
        }
}

```

---

### Post by yanqian on 2006-09-11
Thanks,tjansson!

With the help of your post, I finally solved my problem.

---

### Post by yanqian on 2006-09-11
I have a new problem, why xsupplicant can't start at bootup?

I installed xsupplicant by apt-get,and it automatically created a link in /etc/rc2.d,

$ ls -l /etc/rc2.d/ | grep xsupplicant
lrwxrwxrwx 1 root root 21 2006-09-10 23:26 S20xsupplicant -> ../init.d/xsupplicant

I think it should start at bootup, but it doesn't work, in order to connect the internet, I have to type the two commands everytime I start ubuntu:

$ sudo xsupplicant -i eth0 &
$ sudo dhclient &

---


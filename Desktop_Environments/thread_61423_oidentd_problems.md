---
title: "oidentd problems"
date: 2005-08-31
forum: Desktop Environments
---

### Post by darkrad on 2005-08-31
i installed oidentd doing:

```
atp-get install oidentd
``` 

then i read the readme that forward the reader to the install doc, that i couldn't find. ](*,) 
Anybody know how to succesfully configure and run it?
thanks

---

### Post by darkrad on 2005-08-31
i tried to download the .tar.gz version.
i extracted, made ./install, make, make install.
then i read the configuration info on "man oidentd" and "man oidentd.conf", but i couldn't find any instruction on how to start it. i tried:

```

root@ubuntu:/home/luca/oidentd-2.0.7 # /etc/init.d/oidentd start
Starting ident daemon: oidentd.

```

but it still doesn't work (i tried to use a prog that needs ident reply and i get *, that is when it can't get any reply), since .oidentd.conf file is not created in each home user dir (or should i create it manually? (i already tried too))..
any suggestion?

---

### Post by darkrad on 2005-09-01
If i do:

```

Starting nmap 3.75 ( http://www.insecure.org/nmap/ ) at 2005-09-01 13:14 CEST
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1659 ports scanned but not shown below are in state: closed)
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
113/tcp open  auth
631/tcp open  ipp

Nmap run completed -- 1 IP address (1 host up) scanned in 0.227 seconds

```

so identd is running. my /etc/oidentd.conf file is:

```

# Configuration for oidentd
# see oidentd.conf(5)
#
default {
    default {
        deny spoof
        deny spoof_all
        deny spoof_privport
        allow random_numeric
        allow numeric
        allow hide
        }
}
user root {
    default {
        force reply "UNKNOWN"
        }
}
user mike {
    default {
        allow spoof
        allow spoof_all
        allow random
        allow hide
        allow numeric
        }
}

```

then i created .oidentd.conf into mike's homedir, and filled with:

```

global {
        reply "mikeident"
}

```

Then i tried to use a ftp client on the box using mike access, but ident still doesn't reply in the correct way, it shows "*" instead of "mikeident".
any idea why?  ](*,)

---

### Post by darkrad on 2005-09-13
ok, the problem was that i didn't nat the 113 port on the router ](*,) 
Now the new problem is:
i have 2 pc linked to router, one with linux 1) and one with win 2). since i can't nat 113 port on both computers, i wanted to run oidentd on 1) machine and reply to 2) ident requests with the masqaurading option.
/etc/default/oidentd shows like this:

```

# options to use when starting oidentd as daemon:
# -m    lookup masquaraded connections in /etc/oidentd_masq.users
# -f    forward requests for masquaraded connections to real host
# -q    don't log connections to oidentd
# see oidentd(8) for detailed list
OIDENT_OPTIONS="-mf"

# user / group
OIDENT_USER=nobody
OIDENT_GROUP=nogroup

# Allow the default router to act as an oidentd proxy? (yes/no)
# this is needed behind a masquarading router that runs oidentd -f
# if your identd proxy is not the default router, you have to
# manually specify it via -P
OIDENT_BEHIND_PROXY=yes

```

and /etc/oident_masq.conf has this line:

```

192.168.2.2                   someident             UNIX

```

since 2) has that internal ip.
Then i tried on win machine but i get no answer... 
any clue?

---


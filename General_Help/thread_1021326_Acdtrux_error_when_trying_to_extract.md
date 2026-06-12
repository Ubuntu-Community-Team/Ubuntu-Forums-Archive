---
title: "Acdtrux error when trying to extract"
date: 2008-12-25
forum: General Help
---

### Post by willis575 on 2008-12-25
I am trying to get the wireless working on an acer aspire one by following these instructions

```

wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
mkdir madwifi-hal-current
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz -c madwifi-hal-current
cd madwifi-hal-current
make
make install
modprobe ath_pci
```


however, when I get to this

```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz -c madwifi-hal-current
cd madwifi-hal-current
```

it gives me this error

```
"tar: You may not specify more than one '-Acdtrux' option"
```

What does this mean and how can I overcome this? Thanks!

---

### Post by taurus on 2008-12-25
> 
tar **-xzf** madwifi-hal-0.10.5.6-current.tar.gz **-c** madwifi-hal-current

It means that you cannot put the -options at two different places.  Why not just extract it and then change the name of the new directory to whatever you want, madwifi-hal-current.

```
tar xvzf madwifi-hal-0.10.5.6-current.tar.gz
mv madwifi-hal-0.10.5.6-r3879-20081204 madwifi-hal-current
```

p.s.  You need to include sudo in front of the "make install" or else you will get a error message about permission UNLESS you log in as root!

```
**sudo** make install
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by willis575 on 2008-12-25
Thanks Taurus! Merry Christmas! =)

---

### Post by willis575 on 2008-12-25
Hmmm.... It gives me this after I issue the make command.

```
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by taurus on 2008-12-25
Did you change to the new directory?

```
cd madwifi-hal-current
```

By the way, you don't even have to rename the directory.  You can just change to it and start the "make" command in there.

```
cd madwifi-hal-0.10.5.6-r3879-20081204
make
```

---

### Post by willis575 on 2008-12-25
Yep.


```
justina@justina-laptop:~/madwifi-hal-current$ make
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by taurus on 2008-12-25
Can you post the output of this command?

```
ls -la ~/madwifi-hal-current
```

---

### Post by willis575 on 2008-12-25
justina@justina-laptop:~/madwifi-hal-current$ ls -la ~/madwifi-hal-current
total 4344
drwxr-xr-x  3 justina justina    4096 2008-12-25 10:18 .
drwxr-xr-x 32 justina justina    4096 2008-12-25 10:18 ..
-rw-r--r--  1 justina justina 4421132 2008-12-03 20:44 madwifi-hal-0.10.5.6-current.tar.gz
drwxr-xr-x 13 justina justina    4096 2008-12-03 20:44 madwifi-hal-0.10.5.6-r3879-20081204

---

### Post by taurus on 2008-12-25
> **willis575 said:**
> justina@justina-laptop:~/madwifi-hal-current$ ls -la ~/madwifi-hal-current
total 4344
drwxr-xr-x  3 justina justina    4096 2008-12-25 10:18 .
drwxr-xr-x 32 justina justina    4096 2008-12-25 10:18 ..
-rw-r--r--  1 justina justina 4421132 2008-12-03 20:44 madwifi-hal-0.10.5.6-current.tar.gz
drwxr-xr-x 13 justina justina    4096 2008-12-03 20:44 **[COLOR="Blue"]madwifi-hal-0.10.5.6-r3879-20081204[/COLOR]**

Here it is.

```
cd madwifi-hal-0.10.5.6-r3879-20081204
make
```

---

### Post by willis575 on 2008-12-25
Thanks buddy! It installed perfectly. Still no wifi though lol.

---

### Post by LettuceB on 2008-12-26
Hi, Willis575

I've had great help from this interchange between you and taurus, thanks a lot.

I think you may have forgotten the next step of the instructions, where you need to append the line 'ath_pci' to /etc/modules.

I did that and rebooted, and it worked like a charm!

---


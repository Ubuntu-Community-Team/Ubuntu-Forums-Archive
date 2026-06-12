---
title: "Couldn't find package linux-headers-uname -r"
date: 2009-02-16
forum: General Help
---

### Post by Metallicaman41 on 2009-02-16
I am trying to install VMWare server onto my Ubuntu server (ubuntu server 8.10 with desktop installed)

The instruction to install say to run this command prior to installing VMware

```
sudo apt-get install linux-headers-'uname -r' build-essential xinetd
```

I get these results when running it

```
user@computer:~$ sudo apt-get install linux-headers-'uname -r' build-essential xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r

```

I tried installing vmware without running it but got stuck on the following question, so im assuming i need to run that command.

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.
```

Any ideas?

---

### Post by oldos2er on 2009-02-16
Your command has the wrong syntax. Try ```
sudo apt-get install linux-headers-`uname -r` build-essential xinetd
```

---

### Post by Phlee on 2009-02-16
Useually if you:

```
apt-get update || apt-get dist-upgrade
```

then:

```
uname -r
```

You'll get something like:

"2.6.27-7-generic"

append that to your apt-get

```
apt-get install linux-headers-2.6.27-7-generic build-essential xinetd
```

the uname -r call does work with apt just don't remember syntax

---

### Post by glotz on 2009-02-16
Yeah, what oldos2er said, i.e. wrong kind of dotties there
' <-- that's the wrong one
` <-- that's the right one

also instead of `command` you can also use $(command)

---

### Post by Metallicaman41 on 2009-02-16
> **Phlee said:**
> Useually if you:

```
apt-get update || apt-get dist-upgrade
```

then:

```
uname -r
```

You'll get something like:

"2.6.27-7-generic"

append that to your apt-get

```
apt-get install linux-headers-2.6.27-7-generic build-essential xinetd
```

the uname -r call does work with apt just don't remember syntax


That worked.  Thanks

---


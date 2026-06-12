---
title: "SSH DISPLAY variable incorrect ? - jaunty 9.0.4"
date: 2009-05-07
forum: General Help
---

### Post by yasheshb on 2009-05-07
hello.

  i've installed ubuntu 9.0.4 and am having problems with the DISPLAY variable being set for remote users
here's my environment

bfc22 - FC6 fedora core 6
bfc33 - ubuntu amd 64 bit server
jupiter - FC6

when i login from jupiter to bfc22 and bfc33 here are the results of the environment variable DISPLAY

```
ssh vps@bfc22
[vps@bfc22 ~]$ env | grep DISPLAY
DISPLAY=localhost:17.0
[vps@bfc22 ~]$ 

and

ssh vps@bfc33
vps@bfc33:~$ env | grep DISPLAY
DISPLAY=0.0
vps@bfc33:~$

```

when i invoke emacs on bfc22 it comes up in a separate window on my local machine jupiter but when i invoke emacs on bfc33 it does not come up in a new window , instead it comes up in the terminal 

any help why this worked smoothly on a vanilla fedora core installation but is giving a nightmare on vanilla ubuntu installations.

thx.

yashesh

---

### Post by Brandon Williams on 2009-05-07
What are you doing to tell ssh to forward X from the bfc33 server? You don't have a -X on your command line, so I assume that you have have the necessary entry in your .ssh/config file. Is this correct?

Also, I can't remember whether the Ubuntu sshd_config allows X11 forwarding or not. I think it does, but you should double-check that 'X11Forwarding yes' is in your sshd_config file. While you're there, also check what the 'X11DisplayOffset' value is. This is 10 by default. It hasn't been changed to something else in your config, has it?

---

### Post by Joeb454 on 2009-05-07
By default, I think Ubuntu blocks X11 forwarding via ssh, it needs to be enabled by editing /etc/sshd_config as Brandon Williams mentioned :)

---

### Post by yasheshb on 2009-05-07
brandon, joeb:

 thx for the input. the /etc/ssh/ssh*_config files were modified earlier. here are their content


BFC33
```
yvb@bfc33:/etc/ssh$ ls -l /etc/ssh/sshd_config
-rw-r--r-- 1 root root 1874 2009-05-05 15:58 /etc/ssh/sshd_config
yvb@bfc33:/etc/ssh$ grep X11 /etc/ssh/sshd_config
X11Forwarding yes
X11DisplayOffset 10
yvb@bfc33:/etc/ssh$ 

```


BFC22
```

[root@bfc22 ~]# ls -l /etc/ssh/sshd_config
-rw------- 1 root root 3301 Oct  2  2006 /etc/ssh/sshd_config
[root@bfc22 ~]# grep X11 /etc/ssh/sshd_config
#X11Forwarding no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
[root@bfc22 ~]# 
```

on bfc22 (fedora core 6) theX11DisplayOffset 10 is commented out as a default setting whereas on bfc33 it's set to 10

Also, the defaul file permissions for sshd_config on fc6 are 600 and on ubuntu 9 are 644.

i changed the x11 display offset on jaunty to match fc6 but still the same results. 

thx.

yashesh

---

### Post by Brandon Williams on 2009-05-08
And when you run the ssh client, how are you telling it that you want X forwarding? It's not in your command line. Is there a setting in your ~/.ssh/config file?

---

### Post by yasheshb on 2009-05-11
> **Brandon Williams said:**
> And when you run the ssh client, how are you telling it that you want X forwarding? It's not in your command line. Is there a setting in your ~/.ssh/config file?

brandon:

 here's the configuration


```
Host *
    GSSAPIAuthentication yes
        ForwardX11 yes
# If this option is set to yes then remote X11 clients will have full access
# to the original X11 display. As virtually no X11 client supports the untrusted
# mode correctly we set this to yes.
    ForwardX11Trusted yes

```

the same configuration works fine for fc6. well thanks for your help. appreciate it. i'm switching to FC11 on May 26th since this is real flaky so appreciated your troubleshooting tips.

yashesh

---


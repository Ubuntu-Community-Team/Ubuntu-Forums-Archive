---
title: "Xubuntu 7.04 Error message: &quot;Could not look up internet address for [NAME]...&quot;"
date: 2007-04-27
forum: Desktop Environments
---

### Post by yammosk on 2007-04-27
Hi, I have a problem with my Xubuntu. In order to fully integrate my xubuntu desktop into an existing Windows Active Directory environment, I edited my hosts file so that it now looks like this: 


> 
# The following lines are desirable for IPv6 capable hosts
127.0.0.1 localhost [NAME] [NAME].DOMAIN.COM



The content of my hostname file is 

[NAME]


[NAME] and DOMAIN.COM are placeholders for the real things. As I work in an enterprise I'd rather not post that information. 

The problem is that ever ytime I log in now,  I am greeted with the rather annoying message: > Could not look up internet address for [NAME] This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding [NAME] to the file /etc/hosts on your system.

What can I do to solve this? The correct name is in the hosts file imho. Any other hints? Where could I look for a solution? 
There was a time when the hosts file did indeed not contain the name of the client. Could it be possible that the error message is still from that time? How can I test this? 

I don't mean to be greedy, ANY help or any general wondering would be really appreciated. 

Thanks

Yammosk

---

### Post by Eloyo on 2007-11-06
xfce4 wants to find your host on /etc/hosts. sudo it and add your localhost to your machine address 127.0.0.1.

---

### Post by graabein on 2008-01-01
I got the same message in Xubuntu 7.10. Here is my **/etc/hosts** file:
```
127.0.0.1 localhost
127.0.1.1 <computer>.<domain>

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

The message says: 
> Could not look up internet address for <computer>.

Does this mean it can't take *<computer>.<domain>* (workgroup) settings in **/etc/hosts** or do I have to exchange *localhost* with *<computer>* in the first line?

---

### Post by RiTarDid on 2008-02-05
(solved here) [http://ubuntuforums.org/showthread.php?t=686355](http://ubuntuforums.org/showthread.php?t=686355)

---

### Post by dgray_from_dc on 2008-02-27
> **RiTarDid said:**
> (solved here) [http://ubuntuforums.org/showthread.php?t=686355](http://ubuntuforums.org/showthread.php?t=686355)

I have the ```
Could not look up internet address for . . .
```
problem too.

That thread didn't quite solve my problem though.  My /etc/hosts file had my hostname in it with a domain attached to it.  I added another line without the domain name and it cleared up.

```

127.0.0.1  host.domain host.DOMAIN
127.0.0.1  host                     <-----------------added

```

I'll post there as well, hope this helps someone!!

---


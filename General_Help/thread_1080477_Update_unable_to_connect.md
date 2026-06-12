---
title: "Update unable to connect"
date: 2009-02-25
forum: General Help
---

### Post by channelfh on 2009-02-25
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libxml2-dev 2.6.31.dfsg-2ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libxml2-dev 2.6.31.dfsg-2ubuntu1.3
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.31.dfsg-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-dev_2.6.31.dfsg-2ubuntu1.3_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)




Continually receive this message when I try to update anything. I haven't altered anything on my end that I'm aware of. Problem started maybe 1.5-2 weeks ago. I've tried using different connections...that's the only thing I could think of. I've attempted to find others with similar problem but my search proved fruitless. Apologies if I overlooked a simple solution and thanks to any and all help.

---

### Post by kestrel1 on 2009-02-25
Go to System -> Administration -> Software Sources & check under Third Party Software tab that the CD-Rom is not ticked.

---

### Post by channelfh on 2009-02-25
> **kestrel1 said:**
> Go to System -> Administration -> Software Sources & check under Third Party Software tab that the CD-Rom is not ticked.

Yeah, that's un-ticked...Problem still persists.

---

### Post by avtolle on 2009-02-25
Take a look at your /etc/hosts file. There might be something amiss there. Post it here for review if you have any questions so we might look at it.

EDIT: To get a look, do```
cat /etc/hosts
```from the terminal, and then to paste it here, select the text, Shift+Ctrl+c to copy, and then paste it here. Good luck.

---

### Post by channelfh on 2009-02-25
> **avtolle said:**
> Take a look at your /etc/hosts file. There might be something amiss there. Post it here for review if you have any questions so we might look at it.

127.0.0.1	localhost
127.0.1.1	user-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by channelfh on 2009-02-25
bump? Any input on what this means?
I suppose i've stumped everyone or bored them?

---

### Post by channelfh on 2009-02-25
Shamelessly self bumping once more

---

### Post by wowbagger53 on 2009-02-25
Well I'm new to Ubuntu and the update mechanism, but let's see if we can get you a little further...

I note that it's trying to connect on port 4001 to localhost. I thought that it should use port 80. Is it possible that you are using a proxy, or perhaps have a misconfigured firewall?

---

### Post by kestrel1 on 2009-02-25
I have been away from my machine, am I not allowed a break :lolflag:
Have you run```
sudo apt-get update
```
& run the update manager again.

---

### Post by Demiurgo_linux on 2009-02-25
Mmmmm... it shouldn't connect to localhost but to remote server....

Can you post ```
cat /etc/resolv.conf
``` 
It's a strange problem... your internet connection is ok? can you visualize [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) ?

---

### Post by avtolle on 2009-02-25
The /etc/hosts file looks fine to me. Check whether under Synaptic under Settings>Preferences in the Network tab the radio button for direct connection to the internet is selected, or if it shows that a proxy is in use; if you are not behind a proxy, select the direct connection button (if it is not already selected).

---

### Post by channelfh on 2009-02-25
> **kestrel1 said:**
> I have been away from my machine, am I not allowed a break :lolflag:
Have you run```
sudo apt-get update
```
& run the update manager again.

Attempted this already, and to no avail...Gave same error as other update attempts.

---

### Post by channelfh on 2009-02-25
> **Demiurgo_linux said:**
> Mmmmm... it shouldn't connect to localhost but to remote server....

Can you post ```
cat /etc/resolv.conf
``` 
It's a strange problem... your internet connection is ok? can you visualize [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) ?

Connecting to url via browser is not a problem...
Here's output from request
```
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4898
#
### END INFO

search hsd1.al.comcast.net.


nameserver 68.87.68.162
nameserver 68.87.74.162
nameserver 68.87.64.196

```

---

### Post by channelfh on 2009-02-25
Ima bump one last time ftw!
Hopefully last time anyway...

---

### Post by kestrel1 on 2009-02-25
Not sure if this will help in your case but try this```
sudo dpkg --configure -a
```

---

### Post by Demiurgo_linux on 2009-02-26
> Not sure if this will help in your case but try this
Code:

```
sudo dpkg --configure -a
```
 This is not the problem... The error reveal a problem during the connection to the url: it redirects the connection to localhost... and this is BAD.
> **channelfh said:**
> 
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

It's normal that you can't connect to localhost, but we have to understand WHY you are redirected to localhost... i have no ideas... Anyone can solve the problem?

---

### Post by kestrel1 on 2009-02-26
> **Demiurgo_linux said:**
> This is not the problem... The error reveal a problem during the connection to the url: it redirects the connection to localhost... and this is BAD.
I think this is just a clutching at straws thing.

channelfh, can you post the output from your sources.list file: ```
gedit /etc/apt/sources.list
```
I wonder if there is something in there for some reason.

---

### Post by channelfh on 2009-02-26
> **kestrel1 said:**
> I think this is just a clutching at straws thing.

channelfh, can you post the output from your sources.list file: ```
gedit /etc/apt/sources.list
```
I wonder if there is something in there for some reason.

Here's the requested output once more. 

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by channelfh on 2009-02-27
Anyone find anything unusual in there that may be causing the problem?

---

### Post by kestrel1 on 2009-03-02
No, your source.list looks fine as far as I can see.
Not making much sense why it is trying to connect via localhost. Might be something in iptables. I am a bit at a loss to think why though.

---

### Post by channelfh on 2009-03-03
So, anyone know where I might be able to search out an answer for this or am I going to have to try and find a linux guru some where in the area work on it locally?

---

### Post by kestrel1 on 2009-03-03
Could you check to make sure that there is no proxy set-up on you machine. To do this go to System -> Preferences -> Network Proxy
Make sure that this is set to Direct Internet Connection. Also whilst there check that under the Ignored Hosts tab that it is set as follows:
> localhost
127.0.0.1/8
*.local
If that doesn't work (you may want to reboot first) then check in Synaptic Package Manager that you do not have anon-proxy installed. If you do, completly remove it. Reboot & see what happens then.

---

### Post by channelfh on 2009-03-05
Thanks...I guess it was the anon-proxy...I don't remember installing it but I apparently did. Doesn't matter much now, everything seems to be working fine. Thanks again to everyone that helped.

---

### Post by kestrel1 on 2009-03-06
I suspect it was anon-proxy, it may have got installed when you were trying to get something else on the system. At least you are now sorted.

---


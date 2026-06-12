---
title: "Error during opening user directory (on desktop)."
date: 2012-04-01
forum: Desktop Environments
---

### Post by kleenex on 2012-04-01
Hi, I have a strange problem on my Xubuntu 12.04 LTS beta 2. After system start when I want to get to my home directory by clicking on folder on the desktop after ten seconds I receive this error:

```
Did not receive a reply. Possible causes include: the remote application did not send
a reply, the message bus security policy blocked the reply, the reply timeout expired,
or the network connection was broken.
```After closing the window with this message my home folder opens normally (with one click).
p.s. After very first time with this issue I had this error:

```
Failed to open directory &quot;kleenex&quot;.
Error while retrieving information about a file &quot;/home/kleenex/.gvfs': 
Transport endpoint is not connected.
```**.gvfs** hidden folder in user directory is empty.

---

### Post by 2F4U on 2012-04-01
There is a bug report that seems to be related to your problem:

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117)

---

### Post by kleenex on 2012-04-17
Hi, sorry for the long time of silence. Thanks for the link. There is an interesting thing in post #4 by Mr. Miglietta. He wrote that *Thunar 1.2.2 fixes this bug. *It is strange, because I have Thunar 1.2.3-3ubuntu2.

```
**[COLOR=SeaGreen]$ dpkg -l |grep thunar[/COLOR]**
ii  libthunarx-2-0                         1.2.3-3ubuntu2                         
ii  thunar                                 1.2.3-3ubuntu2                      
ii  thunar-archive-plugin                  0.3.0-4                                
ii  thunar-data                            1.2.3-3ubuntu2                         
ii  thunar-media-tags-plugin               0.2.0-1                                 
ii  thunar-volman                          0.6.1-0ubuntu1
```This problem still occurs.

---

### Post by kleenex on 2012-04-19
Ok, solved. The solution was to change the values &#8203;&#8203;of **AutoMount** entry in /usr/share/gvfs/mounts/network.mount file to **False**.
```
[Mount]
Type=network
Exec=/usr/lib/gvfs/gvfsd-network
[COLOR=Red][B]--- AutoMount=true
[COLOR=SeaGreen]+++ AutoMount=false[/COLOR][/B][/COLOR]
```On this website _[Comment #26 for Bug]("https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117/comments/26")_ user Kiran Majer also suggested creation of a file in the **$HOME/.config/autostart/** directory. Generally he suggest to add something like (whole file is available to download on already mentioned site).

```
gvfs-mount network: > /dev/null && gvfs-ls network: > /dev/null
```but in my case it was not needed. Thanks **2F4U R**. You helped me alot!

---


---
title: "BitTorrent"
date: 2006-08-18
forum: Desktop Environments
---

### Post by marianom on 2006-08-18
Hi,
everytime I shutdown my PC, I see a BitTorrent process halting as part of the  shutting down process.
Is there anyone that can enlight me about what this BitTorrent process do in my machine? I don't recall installing it or using it.

Thanks a lot.

---

### Post by meng on 2006-08-18
It's installed by default, and is started up automatically at boot. If you never intend to use it, you can remove the service from loading automatically.

---

### Post by murataht on 2006-08-18
does anybody know what that service do exactly? is it safe to disable it? or is it intended to use with bittorent application?

---

### Post by marianom on 2006-08-18
I've no problem if it's there to supply some required functionality for Ubuntu but I've got my -maybe paranoid- concerns about its role.

The thing is that it's mentioned in the halting process (I almost sure to see the word Btrack or something like that with it - as soon as I restart my machine I will confirm the exact word) and not everything's running in my machine does so I figure it has a special meaning.

---

### Post by Izzy25 on 2006-08-18
yup same problem here idk if it affects my computer or not and also it doesnt show up anywhere in the menus it says installed in the synaptic package manager but it wont show up is there a way your supposed to install it? and it says when it shuts down " Stopping BitTorrent tracker bttrack bittorent" what is that for?

---

### Post by murataht on 2006-08-18
anybody else interested in this?

---

### Post by marianom on 2006-08-18
Thanks Izzy25, that's the exact message.

Hope somebody can tell us what's it for.

---

### Post by asplode on 2006-08-18
Its a bittorrent tracker service.  Basically it uses your computer as a tracker.  If you don't know what this means, or would like more information, I refer you to [this enlightening wikipedia article.]("http://en.wikipedia.org/wiki/BitTorrent_tracker")  

If you don't make torrent files, you definately don't need this.  If you do make torrent files, but already have a tracker you can use (Oink comes to mind) than you still don't need this.

However, if you make your own torrents, and don't have a tracker, (lets say a private torrent for you and your friends own personal use) then you could use this service.

I believe InitNG or something similar can disable it, but I'm not really sure it takes much resources, so I've left mine enabled.

---

### Post by taageluskeren.dk on 2006-08-24
You can do this to disable the service:
"sudo chmod a-x /etc/init.d/bittorrent"
Or completely remove the file

---

### Post by jobezone on 2006-08-24
> **taageluskeren.dk said:**
> You can do this to disable the service:
"sudo chmod a-x /etc/init.d/bittorrent"
Or completely remove the file

By default it isn't running, even though we all see it being stoped when we shutdown. I'm forgetting a bit the exact details of it, but it's something like this:

 The script to shut bittorrent tracker is part of the "shutdown runlevel" ( can't remember which is it, some of the **/etc/rc*.d** directories, with * being a number).

**/etc/rc2.d** is the default runlevel when you boot the system.

If you wanted to have the bittorrent tracker start when you boot ubuntu, you could make a symlink from **/etc/init.d/bittorrent** to **/etc/rc2.d/S**bittorrent** , with ** being a number which tells the order of execution of this service among the other ones in that directory.

Or you could go to the **/etc/default** directory, where many system-wide defaults for programs are configured, and edit **/etc/default/bittorrent** , and change this part:
> # If you want the bittorrent tracker to run, switch this to 1.
START_BTTRACK=0

---


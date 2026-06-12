---
title: "[SOLVED] apt-get install Does Not Work?!"
date: 2008-12-15
forum: General Help
---

### Post by matey3 on 2008-12-15
hello all;
once again I have run out of resources so I am here asking the experts...

1- I have this server which is running Feisty 7.04 and Xen. 
For some reason when I do an apt-get install update it gives me the E error;

E: Couldn't find package update

So I messed with /etc/apt/sources.list file and it seemed to me that those links had a /dists/ missing (I checked the http link in there in my browser and found the Packages.gz ).
The server is Not running any GUI 
so I put the /dists/ at the end of each line but still did not work.

I do have internet/network connectivity.
Any ideas as to what is the problem>?

2- And also I manually downloaded the Packages.gz, can I install it manually? How?

I appreciate it.

Thanks in advance!

---

### Post by howefield on 2008-12-15
The desktop version of Feisty Fawn reached end of life at the end of last October. I think it is the same for the server version.

(LTS server versions like 8.04 get 5 years support)

---

### Post by orlox on 2008-12-15
You're running apt-get in a wrong way. you use the command:
```

apt-get install update

```

The way to use apt-get to install a package is:

```

apt-get install <packagename>

```

So you're actually telling apt to search for a package named update and try to install it. So, you don't have an error, you're just doing it wrong. If you want to perform an update, you should do:

```

apt-get update

```

Also, just as the other user posted, feisty has reached the end of its life:

[http://ubuntuforums.org/showthread.php?t=947232]("http://ubuntuforums.org/showthread.php?t=947232")

I would seriously recommend you to upgrade two distributions up to hardy, wich has long term support. This is more appropiate for a server.

Hope this helps!

---

### Post by matey3 on 2008-12-15
Thank You All so much for quick reply.

I didnt realize that feisty 7.04 has been removed!(or as howefield said > " has reached end of its life" )

I found the link and the lines (for sources.list file) that I was looking for in here;
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

Thanks a lot, The problem is solved!
2 thumbs up!
):P

---


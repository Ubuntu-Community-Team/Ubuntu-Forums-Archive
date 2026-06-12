---
title: "Unable to apt-get update or update in Add/Remove"
date: 2009-05-02
forum: General Help
---

### Post by Kaidao on 2009-05-02
Hey,

I just installed Ubuntu (Jaunty) today, and took about 4 hours trying to get my Belkin Wireless Adapter to work. It now finally works and I'm able to surf the web. But I've come across a problem. For some reason, I can't seem to use the command "apt-get update". The error that I come across is

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources
Unable to connect to 168.192.0.100 8080:
```Also, when I try to update my Add/Remove, I get an error that says

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  Unable to connect to 168.192.0.100 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.
```Is there anyone that can help me?

Thanks.

---

### Post by Bungo Pony on 2009-05-02
Either that particular server's down (it happens) or you need to change where you're getting your updates in the sources.lst file.

---

### Post by Kaidao on 2009-05-02
Sorry, but where's my sources.lst file and what should I change it to?

---

### Post by Kaidao on 2009-05-03
Bump. Anyone got any suggestions?

---

### Post by Kaidao on 2009-05-03
Ok, well I changed my sources.list but I'm still getting the same error:

```
Err http://archive.canonical.com jaunty-backports/partner Sources              
  Unable to connect to 168.192.0.100 8080:
```

when I do a sudo apt-get update.

Can someone please help me on this?

---

### Post by plucky on 2009-05-03
Post your sources.list file.Open a terminal and ```
cat /etc/apt/sources.list
``` and copy and paste it to the forum.

Use a [noparse]```
[/noparse] at the start of the text and a [noparse]
```[/noparse] at the end of the text as it makes it easier for us to read.

Good Luck

---


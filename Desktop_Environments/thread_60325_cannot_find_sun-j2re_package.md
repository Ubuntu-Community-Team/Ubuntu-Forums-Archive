---
title: "cannot find sun-j2re package"
date: 2005-08-27
forum: Desktop Environments
---

### Post by ubuntunewbie on 2005-08-27
want to install sun java runtime environment. used to find this package earlier in kynaptic. but it's not there anymore..
anybody knows what repository to pull it from in /etc/apt/sources.list?

Please help !

---

### Post by incinerator on 2005-08-27
I guess you already have added ubuntu-extras to your sources.list, then. See the Ubuntu Backports section of this forum to find out why some packages are not available atm. As a quick summary, there is a problem with the master download server of the ubuntu-backports/extras project making certain packages not appear in the Packages.gz file and therefore these are invisible to apt-get.

There are two workarounds to this:

1.) Go to the Ubuntu Backports website to find a mirror and download and install the package manually. sun-j2* packages are in the hoary-extras/restricted/ directory.
2.) Go to the [wiki](https://wiki.ubuntu.com/JavaPackageBuildNewVersions?highlight=%28java%29)  and build your own java packages.

---

### Post by numberexhaust on 2005-08-27
If you are a Java developer, I've found the best thing to do is to download jdk5.0 and netbeans from [http://java.sun.com](http://java.sun.com)

I don't know how to find the package through apt-get, though.  Try searching synaptic for something like "mozilla plugins", or something to that extent.

---

### Post by c0rderr0y on 2005-08-27
i wonder how long it will take to fix.... i was going to install kubuntu on a few computers this week but that does not look like it will happen now  ](*,)

---

### Post by incinerator on 2005-08-27
I fail to agree with at attitude. Java not really essential, is it? You can (very) easily build your own java packages anyway, I don't know why people are afraid of doing that.

Wow, Sun's marketing must be really good, to make people NOT install linux just because they don't have a point'n'click Java setup. Why don't you install Slowlaris, then? It is free software, you know. Alternatively you could just ask yourself what you really need java for. I hope you will be surprised to find out it is not much.

---

### Post by c0rderr0y on 2005-08-27
you don't have to act like a dick by posting comments like

"Wow, Sun's marketing must be really good, to make people NOT install linux just because they don't have a point'n'click Java setup. Why don't you install Slowlaris, then?"

The main reason why ubuntu/kubuntu became so popular it that it just works (tm) i also use slackware but like the idea of not having to spend a whole crapt load of time getting everything to work nicely when i can have half of it done for me.

---

### Post by incinerator on 2005-08-27
lol, who did start replying off-topic in the first place?

---

### Post by ubuntunewbie on 2005-08-28
The java packages have become available again now

---


---
title: "How can I find the source URL of a spcific package?"
date: 2009-04-13
forum: General Help
---

### Post by v0yAgEr on 2009-04-13
Hi,
I would like to know if there is a possibility to find out the full URL of a package.

When I type 'apt-cache show *blabla*', I get the path to the .deb file, but without any info about the source that hosts this package. Instead, I'm looking for a way to find out the full URL of the deb file.

I need only the URL - I know that there is an option to download the package without installing, but it's not what I'm looking for...

Many thanks!

---

### Post by cariboo on 2009-04-14
You can find which repository an application is in by selecting the package in Synaptic and then clicking the properties button. See the screencshot. Next check /etc/apt/sources.list for the exact url for the universe repository as show in the example.

In my case it is:

```
http://archive.ubuntu.com/ubuntu/ jaunty universe
```

Jim

---

### Post by v0yAgEr on 2009-04-14
Thanks for your reply, but is there any way of getting this info via command line? Thanks again :)

Edit: Nevermind, I got it :) If you type apt-cache policy *package_name*, it gives you the repo that the package belongs to. Combining this with apt-cache show *package_name*, gives you the full path to the deb file. If you have a better idea I would love to hear it... Thanks anyway !

---


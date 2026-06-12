---
title: "Conky, External IP Updating"
date: 2009-04-14
forum: General Help
---

### Post by codeseer on 2009-04-14
From what I've seen so far, most conky users have something like this:

```

Net IP: ${execpi 3600 wget -O - -q myip.dk |grep '"Box"' | egrep -o '[0-9.]+'}

```

This works good for those with stable connections and those who may not be using the information often. However, I am wondering what the best way to keep the information updated as often as possible would be.

One could decrease the execution frequency, but this also increases bandwidth usage (both locally and to the website).

One could poll it locally if they had some way of determining the external IP from the command line that didn't consume Internet bandwidth (perhaps a router CLI, but this wouldn't be widely usable) or if they had some way of knowing when the Internet connection disconnected/reconnected, they could poll the new information using the above command.

Assuming the user would be on a local network, behind a router, does anybody have any ideas on how to address this problem?

---


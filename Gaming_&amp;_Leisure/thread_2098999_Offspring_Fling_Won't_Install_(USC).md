---
title: "Offspring Fling Won't Install (USC)"
date: 2012-12-28
forum: Gaming &amp; Leisure
---

### Post by rudeboyskunk on 2012-12-28
I just got Offspring Fling through its addition to the Humble Indie Bundle 7, and I try to install it through the Ubuntu Software Center, but after taking awhile, it doesn't do anything, and finally gives me this error:

W:Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/offspring-fling/ubuntu/dists/quantal/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/offspring-fling/ubuntu/dists/quantal/main/binary-amd64/Packages)  The requested URL returned error: 404
, W:Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/offspring-fling/ubuntu/dists/quantal/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/offspring-fling/ubuntu/dists/quantal/main/binary-i386/Packages)  The requested URL returned error: 404
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldrocker99 on 2012-12-28
The same thing happened to me last night...

---

### Post by BroWren on 2012-12-28
The same thing's happening to me, too. Running 12.10 on 64-bit here... from poking around in the repo, it looks like they only uploaded a build for 12.04. :(

---

### Post by GreggC on 2012-12-29
> **BroWren said:**
> The same thing's happening to me, too. Running 12.10 on 64-bit here... from poking around in the repo, it looks like they only uploaded a build for 12.04. :(
Same thing happened to me &  I'm running 12.04

---

### Post by sffvba[e0rt on 2012-12-29
My initial thoughts were that it was perhaps not added to the Repo's yet as it was just added to the Bundle however from this ([https://apps.ubuntu.com/cat/applications/quantal/offspring-fling/](https://apps.ubuntu.com/cat/applications/quantal/offspring-fling/)) it would seem it should be available for both 12.04 and 12.10...


404

---

### Post by Gadgetguy96 on 2012-12-29
While the repository is being worked on, just log into your Humble Bundle page and download the .deb file to install it.
I have installed Offspring Fling this way.

---

### Post by closertozero on 2012-12-29
Here's what worked for me:

After the failed usc-install apttempt, i noticed the ppa was still in my repo-list, and that it said "/dists/quantal" (weird since i run precise). I changed the dist reference to precise and started USC again, still no dice - same error. A bright light suddenly blinded me, so I threw up a terminal window to stop it from taking my eye-sight. In the terminal I simply typed

```
sudo apt-get install --reinstall offspring-fling
```

and presto, it worked.

---

### Post by rudeboyskunk on 2012-12-30
> **closertozero said:**
> Here's what worked for me:

After the failed usc-install apttempt, i noticed the ppa was still in my repo-list, and that it said "/dists/quantal" (weird since i run precise). I changed the dist reference to precise and started USC again, still no dice - same error. A bright light suddenly blinded me, so I threw up a terminal window to stop it from taking my eye-sight. In the terminal I simply typed

```
sudo apt-get install --reinstall offspring-fling
```

and presto, it worked.

Began to follow your advice, changed it from quantal to precise (since I'm running 12.04) and it worked.  Thank you sir, don't know why I didn't notice that before.

---


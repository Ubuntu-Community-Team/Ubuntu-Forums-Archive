---
title: "Bastion Fails to Install from USC"
date: 2012-06-17
forum: Gaming &amp; Leisure
---

### Post by cprofitt on 2012-06-17
Am getting the following errors:

> W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/bastion/ubuntu/dists/precise/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/bastion/ubuntu/dists/precise/main/binary-amd64/Packages)  The requested URL returned error: 401
 W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/bastion/ubuntu/dists/precise/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/bastion/ubuntu/dists/precise/main/binary-i386/Packages)  The requested URL returned error: 401
Seen two bugs on it... and a question, but nothing is resolving this for me. Anyone else with some suggestions?

Bug Link -- [https://bugs.launchpad.net/software-center-agent/+bug/1010252](https://bugs.launchpad.net/software-center-agent/+bug/1010252)
Similar Bug Link: -- [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1008289](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1008289)

Thanks

---

### Post by Carborundum on 2012-06-17
I have the same problem with Amnesia. It's not a problem on our end; the credentials provided in [https://software-center.ubuntu.com/subscriptions/](https://software-center.ubuntu.com/subscriptions/) are invalid. They are on the form
```
deb https://[your USSO username]:[your password to this specific PPA]@[PPA URL] [Ubuntu version] main
```You can test them manually by entering the URL to the ppa, and try to sign in with the username and password from the deb line.

I contacted Canonical directly about this a week ago, but haven't received a reply yet.

---

### Post by bud986 on 2012-06-17
Hopefully they are working on the problem if not I guess you have to download the binaries from humbleindie bundle.

---

### Post by Carborundum on 2012-06-18
> **bud986 said:**
> Hopefully they are working on the problem if not I guess you have to download the binaries from humbleindie bundle.
Yeah, I'm not too worried. As you say, we have access to the games through another download method, and we didn't actually pay Canonical anything for them. In light of that, I don't think we can expect our problem to have very high priority for Canonical, and I'm fine with that.

Unfortunately, some people have apparently been been hit by this bug after making a purchase directly through Software Center. Had that happened to me, I would have been a bit more upset at not receiving a reply yet.

---


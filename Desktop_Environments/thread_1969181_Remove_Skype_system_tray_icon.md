---
title: "Remove Skype system tray icon"
date: 2012-04-29
forum: Desktop Environments
---

### Post by kriggus on 2012-04-29
Hi, 

I've searched for a solution for quit some time now but without any success. To the problem, I can't get rid of the (in my opinion) very ugly Skype icon in the system tray. Ironicly it seams like most people have the opposite problem...

Anyway, I installed skype following this guide:
[http://www.liberiangeek.net/2012/04/install-skype-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-skype-in-ubuntu-12-04-precise-pangolin/)

Essentially the guide says, type:
```
sudo apt-add-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```then:
```
sudo apt-get update && sudo apt-get install skype
```Since then I've removed Skype, purged Skype, reinstalled Skype using the .deb available at skype's website, reseted unity and finally checked that Skype is not in my systemtray-whitelist, which btw i set to default ['JavaEmbeddedFrame', 'Wine', 'Update-notifier']. Nothing seams to help.

I run the 64bit version of Ubuntu 12.04 LTS and am now out of ideas.

Thanks for the help!

---

### Post by kriggus on 2012-04-30
Found the answer! To remove sni-qt and sni-qt:i386 (=

```
apt-get remove sni-qt:i386
apt-get remove sni-qt
```

I can now control the appearance of the skype icon thought the systemtray-whitelist as i wished. 

If other side-effect of removing sni-qt is expected, please let me know.

---

### Post by vaul on 2012-11-01
I would like to clarify one detail &#8212; does this mean that you will not be able to maximize the Skype when it is minimized to tray, even when no indicator is displayed; if so what use is this solution? 

Update: looks like it is fine, it minimizes as any normal appication now.

---


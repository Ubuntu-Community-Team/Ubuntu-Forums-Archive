---
title: "KDE Dolphin won't connect to owncloud webdav"
date: 2016-06-29
forum: Desktop Environments
---

### Post by courtney2 on 2016-06-29
I can do webdav://domain.com/path/to/webdav and it works just fine, but if I go to permanently set the connection in Dolphin I always get the error:
```
 Unable to connect to server.  Please check your settings and try again.


```

I know it's not my server because I can do it just fine with the GNOME desktop through online accounts and I can also connect with my MacBook. I also followed the instructions in the owncloud documentation and I have had no luck. When I type in the information it looks sort of like this:

Name: ownCloud
User: me
Server: domain.com
Port: 443
Folder: owncloud/path/to/webdav

Then I set the radios to create an icon for the remote folder and also to use encryption (my server is set up to connect only to port 443 and use an encrypted connection only

---

### Post by courtney2 on 2016-07-03
I figured it out. ownCloud introduced a capital letter that I didn't add and that's what was causing failed authentication. I found out that it was capitalized by looking at my federated cloud ID

---


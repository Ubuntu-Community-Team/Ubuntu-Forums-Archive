---
title: "Gutsy/KDE: Long username causes &quot;Add a Network Folder&quot; to choke"
date: 2007-12-19
forum: Desktop Environments
---

### Post by LAI on 2007-12-19
Hi,

I'm trying to create a network folder to connect via FTP to a server. The login I have works fine on the command-line, but the problem is that the username is too long for Konqueror's "Add a Network Folder" function. The username includes the string "@hostname.tld", which screws up some clients. Here's what happens:

1. Enter "remote:/" in Konqi's location bar.
2. Select "Add a Network Folder".
3. Choose "FTP", click "Next", fill in folder name, long username, servername and so on.
4. Click "Save and Connect". It asks me for my password, and saves the connection.
5. Try to open the network folder. This fails because the connection seems to have a truncated version of the username: instead of "myusername@servername.tld", it seems that it has [i]saved[\i] "myuse...ame.tld" rather than just using that for display purposes.

Has anyone else experienced this problem? Does anyone have a workaround?

Cheers,
-LAI

---


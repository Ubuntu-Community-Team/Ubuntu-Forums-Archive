---
title: "Strange Problem with &quot;Connect to Server&quot;"
date: 2006-07-19
forum: Desktop Environments
---

### Post by tknorris on 2006-07-19
I have a strange problem with "connect to server". Sometimes when I map an SMB share, no icon shows up on the desktop. Even if I try multiple times with different servers/shares, it will not show up. However, when I reboot, all the icons will be there for each time I defined the connection.

I've checked in the nautilis xml file, and each defined connection shows up, I can do the mounts at the console (via smbmount) and they work fine, and I can see each connection I defined listed in gconf-editor but for some reason the icon just won't show up on the desktop.

The most annoying part is this only seems to happen sometimes, but once it starts happening, I can't get the proper behaviour back until I reboot.

Anyone have any thoughts on what could be causing this?

---


---
title: "Can't View Music Folder on Windows 2003 Share (Samba?)"
date: 2008-05-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by undfined on 2008-05-07
All -

Just spent the last 2 days getting Hardy installed on a brand new Dell Inspiron 1420n.  I'm lovin' Gimp, Firefox, and am flying xls files around without any problems.

I'm up and running, with a few issues.

One is that I can't view a Windows 2003 Server share.

I get an error:

"The folder contents could not be displayed.

Sorry, couldn't display all the contents of "music on 192.168.10.100": Invalid argument"

This is when I try to attach and bookmark a location after using the "Connect to Server" option in the Places menu.

What I have is a Win2K3 server with a secondary hard drive.  I have several folders on that drive shared.  I can connect to all of them except my music folder.  

Some other folders have issues too.  My backup folder has my pictures in it.  When trying to copy them to my 1420n some folders error out.

It seems as though any folder with more than a certain number of files in it is looked at by Ubuntu it errors out.  I have yet to pinpoint the number.

I saw this: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/206585](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/206585)

But the tweak there didn't work for me.

Any other thoughts?

Thanks ahead.

---

### Post by edmicman on 2008-09-05
Did you ever get this worked out?  I'm having the exact same problem on a music folder with ~3000 subfolders within that.  This is crazy annoying that I can't get to my music over the network from Hardy  :-/

---


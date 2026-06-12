---
title: "xterm + vnc: Color name &quot;black&quot; is not defined"
date: 2006-07-28
forum: Desktop Environments
---

### Post by porterde on 2006-07-28
Hello,

I recently upgraded a machine from Breezy to Dapper, and I am having a problem using xterm within a vnc session.  The vnc server is running on the Dapper machine.

Basically, when I use xterm, I get these messages and some of the colors don't work:

Warning: Color name "black" is not defined
xterm: Cannot allocate color green
xterm: Cannot allocate color red

This did not happen on Breezy.  Any help would be greatly appreciated.

Best,
Don

---

### Post by porterde on 2006-08-01
I have resolved this problem and am posting the solution here for reference.

Basically, when one starts vncserver, it reads the client's X config for things like screen size, etc.  Among these features are the _location_ of the rgb.txt file.  This is a strange assumption, that rgb.txt will be in the same place on both the client and server, but whatever...

My problem occurred on a set of machines with a different X server, so this file was in a different location.  I identified where it was looking in .vnc/[session].log file and created a symlink to /etc/X11/rgb.txt.

This fixes new sessions.  Old ones must be restarted.

Hope this helps...

Don

---


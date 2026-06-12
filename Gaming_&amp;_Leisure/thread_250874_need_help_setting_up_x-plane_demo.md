---
title: "need help setting up x-plane demo"
date: 2006-09-04
forum: Gaming &amp; Leisure
---

### Post by fubadubrub on 2006-09-04
Hello, I have x-plane demo installed to /usr/local/games/X-Plane 8.50 Beta 10.  Now x-plane does not fully understand multiuser and attempts to write to /usr/local/games/X-Plane 8.50 Beta 10 directory which it can't obviously.  I wish they would make it so that it put it's write files in home.

Any way I would like to create a group called x-plane and add user self to that group.  Then change the permissions on the files that I know that x-plane writes to.  I like to give the group x-plane read and write permissions on the write files.

Right now the entire x-plane folder is user owned which is bad Linux form.  I figure that by creating a group called x-plane and adding myself I can get more fine grained control and leave the other x-plane files and directory's read only by user.

I made a group called x-plane using users and groups in the System menu and added myself.  Then using Nautilus I changed the group on the write files to x-plane and set it to read and write.  I tried to do this using Nautilus as sudo.  This did not work.  The demo runs fine it just cant save preference changes.

Can anybody help me with this.

---


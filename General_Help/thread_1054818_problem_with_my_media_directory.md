---
title: "problem with my media directory"
date: 2009-01-30
forum: General Help
---

### Post by nealien on 2009-01-30
i am using ushare to stream media to my xbox360.  it works fine (i think) but i'm now having a problem with my media.  all of my media is on a third internal hard drive.  this drive consists of 3 folders.  videos, music, and pictures.  the hard drive is using the ntfs file system so all the machines in my house can access it.  the problem is that ushare requires me to write the location of my media in the conf file.  i have no idea what to write there.  so far i have tried...

/media/noobaliciousstorage_

and

g:  (since it's my g: drive)

someone please help!

---

### Post by mb_webguy on 2009-01-30
I don't have any experience with ushare -- I use MediaTomb myself -- but if you're running the app in Linux and it asks you for the path, you need to give it the Linux path, not the Windows path.  G:/ is a Windows path, and has nothing to do with Linux.

If you have the drive mounted as /media/noobaliciousstorage, then that's what you need to put in the conf file.  However, since this is a directory, the app may expect a / at the end of the path, so you should try "/media/noobaliciousstorage/".

And if you continue to have problems with ushare, I'd suggest trying another server.  There are several available, and some are easier to use than others.  I found MediaTomb extremely easy to set up and use.  You may have to make some few minor edits to the config file when you first set it up -- I had to change two lines, I think, to make it compatible with my PS3 -- but it has a web-based GUI to add and remove media directories.

---

### Post by nealien on 2009-01-30
thank you very much for ure response.  i had thought of that already, and it still doesn't work.  the xbox sees my computer just fine.  it just doesn't see any media.  i run the command ushare -x to start the server, and it gives me errors about there being no such file or directory.  i even thought that it could be a permissions thing, so i used the command sudo ushare -x and still nothing.  i've used townkymedia and ushare so far neither work.  i'm gonna try this program you're suggesting.  

thanks again :D

---


---
title: "Changing group and owner recursively"
date: 2012-06-28
forum: Desktop Environments
---

### Post by bencouve on 2012-06-28
This will be easy for someone I know, but I am concerned with doing harm to the file system.

I want to recursively change the owner and group of files and directories and . (dot) and .. (dot dot) within a file system to the same owner and group. Could someone suggest the best way of doing this. 

Say for example Ihave

/abc/de/fg/hi

and I want to change the owner and group of all files and directories that they contain.

Hope that is clear enough. Thanks in advance.

---

### Post by miggys on 2012-06-29
You could do this with chown (change owner)

chown -hR user:group /abc/

will change /abc/ and everything under it.  The R flag means recursive and the h flag says that if there are links, only change the link and not the target of the link.  I am not sure what you are trying to do about . and ..  -- be careful trying to reference those.  You can easily make something happen you had not intended.

---

### Post by bencouve on 2012-06-29
Thanks, that worked great.

---


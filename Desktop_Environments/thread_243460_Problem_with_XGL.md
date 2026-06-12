---
title: "Problem with XGL"
date: 2006-08-25
forum: Desktop Environments
---

### Post by mlw4428@gmail.com on 2006-08-25
Basically I followed the post that spoke of fixing the Ctrl-Backspace bug in XGL. The command I followed was:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```

However now the 3D cube effect when I'd hit Ctrl-Alt and an arrow key has disappeared. I also cannot manipulator "the cube" with my mouse. How can I fix it so that Ctrl-backspace doesn't work, but everything else does (short of ripping the backspace key off my keyboard). 

If that cannot be done how can I restore it to the default functionality? Thanks!

---

### Post by mlw4428@gmail.com on 2006-08-25
Apparently you only have to log out and log back in to fix it...but is there another way of bypassing that ctrl-backspace bug?

---

### Post by h00s on 2006-08-25
The ctrl+backspace bug is only in compiz installed from repos.
Update to latest xgl/compiz.

edit /etc/apt/sources.list and add this lines to it:
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```

After that done,
```
sudo apt-get update
sudo apt-get upgrade
```

And after that done, you should have installed latest compiz plugins, cgwd etc.

Also, it's possibly to change only ctrl+bkscp using xmodmap but I'm not sure how to do it, but I read it somewhere in forum. You could search forum and find it.

---


---
title: "Gftp and Vim inside external terminal"
date: 2006-08-31
forum: Desktop Environments
---

### Post by kikinovak on 2006-08-31
Hi,

Until recently, I've been using the following combination to edit files remotely on a web server: in XFCE, GFTP, xfterm4 (wrapper script for aterm), and Vim. In GFTP > FTP > Options, I configured the following line at "Edit files with":

xfterm4 -exec vim --nofork

... which allowed me to right-click on a remote file, choose "Edit", and then Aterm would pop up with the file already opened in Vim. 

Now I wonder how I could do this in my Ubuntu GNOME environment. I've already come as far as:

gnome-terminal -e vim

... but that's it. Doesn't work. Anyone has an idea?

---

### Post by kikinovak on 2006-08-31
I'll answer that myself, since I just found the solution by trial and error:

```
gnome-terminal -x vim
```

It's as simple as that. But it leaves me with another question:

How can I open gnome-terminal fullscreen (well, not fullscreen, only maximized) by default. Since I use the Terminal rather often, I always have to open it and then click to maximize. 

Any suggestions?

---


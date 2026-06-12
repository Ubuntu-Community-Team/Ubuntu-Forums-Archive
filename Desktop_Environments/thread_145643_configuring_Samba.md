---
title: "configuring Samba"
date: 2006-03-16
forum: Desktop Environments
---

### Post by onclouds on 2006-03-16
can anyone please explain me how to drag and drop network folders onto my Xubuntu system?
I'm getting the following error...

Error getting file list: Can't get data from remote machine (application/octet-stream not provided)

I have a partition in a network PC with music and would like to listen to it on the Xubuntu PC without having to copy it. Is that possible? if so How? and if not how can I copy the folders I want?

thanks in advance

---

### Post by nalmeth on 2006-03-16
do you have xfsamba4? 
try:
ALT-F2
enter 'xfsamba4'
if installed it should also appear in 'xfce4-appfinder' under network
see what you can do with that

---

### Post by MJRehrig on 2006-04-03
I'm pretty sure Xubuntu does not come with XFsamba4 because it is in the XFFM  package and Xubuntu uses Thunar as its file manager.

I am having a similar problem to OnClouds, but I know I do not have XFSamba or XFFM installed.  When I try to install XFFM with synaptic, it says it has unresolved dependencies...etc.  I am not using my linux computer right now, but if you want the exact error message, with all of the dependencies listed, just post back and I will reply with that.

I actually don't need XFFM. I was just trying to get it to use XFSamba, so if you know of any programs for XFCE that are graphical samba managers, that would be great.

thanks for any help!

---

### Post by justmehere on 2006-05-30
I just installed xffm and it worked fine for me. (clean unstall and all the updates then added the unverse repositories in synaptic then installed xffm).

---


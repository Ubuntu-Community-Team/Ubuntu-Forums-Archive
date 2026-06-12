---
title: "vnc server stopped working"
date: 2009-07-31
forum: Desktop Environments
---

### Post by willemto on 2009-07-31
Maybe someone can help?

After installing the latest linux kernel update my vnc sever setup stopped working. I now only get the gray xterm screen when logging in remotely.

It seems the gnome-session does not start. Where do I start looking for the problem? I have tried different ./.vnc/xstart configurations, but no luck.  Another thing that broke was the loss on my terminal, but this I fixed with an entry to the /etc/fstab file.

It seems that every time there is a kernal update, something breaks...:(

---

### Post by willemto on 2009-07-31
I have now determined that it is only gnome-session that are at fault. Running gnome-session & from a terminal, local or remote fails.

---

### Post by willemto on 2009-07-31
Problem went away by itself. I guess LINUX is just undeterministic when in the hands of an idiot like myself. :(

Can anybody recommend a good book that describes how gnome works; how to set it up; what files are cache resulting in delayed action when you change them? I would hate to remain an idiot.

---

### Post by willemto on 2009-07-31
"By itself" is incorrect.

When I run the following from command line:

vncserver -geometry 1280x970 -depth 24 
all is well, and I get a GNOME login remotely.

When I run this script:

#!/bin/sh
gnome-terminal --command "sh  -c  'vncserver -geometry 1280x970 -depth 24   2>&1 && sleep 20000000'"

All is well seeing GNOME again, until I terminate the script terminal: I get the gray screen from where I am logging in.

If I remove the sleep from the script, then I just get the gray screen.

I guess it has to do with parent terminal terminating, terminating also the child processes. I guess a & somewhere will do the trick? But I still want the error report.

---


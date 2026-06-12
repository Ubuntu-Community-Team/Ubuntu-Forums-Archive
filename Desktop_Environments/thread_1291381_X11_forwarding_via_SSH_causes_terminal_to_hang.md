---
title: "X11 forwarding via SSH causes terminal to hang"
date: 2009-10-14
forum: Desktop Environments
---

### Post by tnine on 2009-10-14
Hi all,
 Sorry if this is the wrong forum, I couldnn't find anything that seemed more appropriate.  I'm having a bit of a problem with SSH forwarding.  I'm connecting to a CentOS server, and then running the Xnest command with the following script.
```


#!/bin/sh

if [ "$#" -ne 1 ]
then
  echo "You must specify a display number.  Try any number > 0"
  exit -1
fi

/usr/bin/Xnest ":$1" -ac -geometry 1024x768 -once -query localhost &> /dev/null &
```

So, I start the script on my server with the command "XnestStart 1".  This works well when I'm connecting from OS X clients, as well Fedora desktops.  However, whenever I connect with Ubuntu, my X session starts, then after 1 to 2 minutes my remote X11 screen turns black and  my SSH session hangs.  Any idea's what's going wrong? I've verfied it's not the server by connecting with other clients, and I'm not getting the same problem.  I'm connecting with ssh with these options.

ssh -X -C [EMAIL="todd@foo.bar.com"]todd@foo.bar.com[/EMAIL]

Thanks,
Todd

---


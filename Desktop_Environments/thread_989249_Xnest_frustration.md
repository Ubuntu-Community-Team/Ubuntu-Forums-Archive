---
title: "Xnest frustration"
date: 2008-11-21
forum: Desktop Environments
---

### Post by taiji_jian on 2008-11-21
Am I the ONLY ONE who cares that XNEST has been HORRIBLY HORRIBLY BROKEN for something like THREE major Ubuntu releases? I have three headless servers on my network that I have been accustomed to administering remotely via XDMCP. They are of widely varying ages and capabilities, and I USED TO connect to them from a similar variety of machines. 

I've posted about this. I've googled obsessively about this. I've even filed a couple of bugs. NOTHING.

NYRRRGH. Is everyone else just using the command line and ssh to maintain their headless boxes, or what?

---

### Post by jpkotta on 2008-11-22
You could use vnc instead.  Use this to connect to a remote X server.
```

#!/bin/bash

usage="$0 [user@]remote_host [<DISPLAY>]"

login="$1"
if [ -z "$login" ] ; then
    echo $usage
    exit 1
fi

disp="$2"
if [ -z "$disp" ] ; then
    disp=:0
fi

ssh "$login" "x11vnc -localhost -display '$disp' -scale 4/5 -bg" 
vncviewer -via "$login" localhost"$disp"
```

You could also use X11 forwarding if it's just a few graphical apps you want.
```
ssh -X user@remote xlogo
```

---

### Post by krunge on 2008-11-23
> **taiji_jian said:**
> Am I the ONLY ONE who cares that XNEST has been HORRIBLY HORRIBLY BROKEN for something like THREE major Ubuntu releases? I have three headless servers on my network that I have been accustomed to administering remotely via XDMCP. They are of widely varying ages and capabilities, and I USED TO connect to them from a similar variety of machines. 

I've posted about this. I've googled obsessively about this. I've even filed a couple of bugs. NOTHING.


Yes, I think I see the problem you are having (you didn't give any details, BTW). When I run Xnest like this:
```

Xnest :2 -geometry 1024x768 -query hostname

```
It gives me an xdmcp session on 'hostname'.  It worked fine on my workstation, but when I tried it on a Ubuntu 8.10 box it came up OK, but was somehow missing expose events or something and so the apps/windows inside the Xnest were not repainting themselves.  Is this what you are seeing?

I had to do a full refresh inside the Xnest session to force the windows to repaint.  I also tested it with twm as the window manager so it is not a desktop bug.

I'm not sure what you can try next, except going back to an older Xnest binary.

---

### Post by Jack Waugh on 2011-08-03
I can't even get Xnest to work locally.  Not only does it fail to refresh, but it doesn't pass arrow keys through when I type them.  It passes printable characters, however.

---

### Post by krunge on 2011-08-05
> **Jack Waugh said:**
> I can't even get Xnest to work locally.  Not only does it fail to refresh, but it doesn't pass arrow keys through when I type them.  It passes printable characters, however.
Isn't Xephyr an Xnest replacement? Perhaps it is maintained and still works...

---


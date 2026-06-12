---
title: "Remote control that works?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by jrohde on 2006-09-24
Hi,

I have tried various versions of VNC, but none worked well enough - there is a lot of problems updating the screen.

Is it possible to remote control Ubuntu from a Windows pc over LAN in a way that works (nearly) just as well as commercial applications like NetOp?

Jakob

---

### Post by atrophic on 2006-09-24
I use the free version of the NX Server, and the NX client on windows.  It works very well.

See this link for a guide: [http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake](http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake)

---

### Post by jrohde on 2006-09-24
Hi,

Thanks.

The link to NX Server doesn't work! It seems like there is no free version af the server any more?

Jakob

---

### Post by jrohde on 2006-09-24
Hi again,

These packages doesn't install on my amd64 Ubuntu :-(

So I guess this isn't for me...

Jakob

---

### Post by tlue on 2006-09-24
> **jrohde said:**
> Hi,

Is it possible to remote control Ubuntu from a Windows pc over LAN in a way that works (nearly) just as well as commercial applications like NetOp?

Jakob

Perhaps Xming is good for your needs (...like NetOp):
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)

---

### Post by tagra123 on 2006-09-24
> **tlue said:**
> Perhaps Xming is good for your needs (...like NetOp):
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)


If you are not concerned with needing the GUI then ssh is very good.  You will need to install putty (ssh client) on windows to access the ubuntu terminal. I have had no problems with this method.

---


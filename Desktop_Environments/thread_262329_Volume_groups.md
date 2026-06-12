---
title: "Volume groups"
date: 2006-09-21
forum: Desktop Environments
---

### Post by blingenfelter on 2006-09-21
On shutdown, my Dapper Drake on Thinkpad continually stops at 

"Will now halt LVM volume groups...    e.t running.manager, use"

and does not finish shut down. Why? So ever time, I have to hold down the power-on button until everything stops. Annoying.

---

### Post by Rob_Frohne on 2006-09-21
I have the same thing happening on my Dell D600 laptop.  I kind of think it has something to do with power management, suspend, or hibernate.  In my situation, it only does it periodically, and after I have suspended, or hibernated.  Also, when this happens, my network doesn't work and it seems there are some other funny things too.

This is with the latest Dapper updates.

Rob

---

### Post by Rob_Frohne on 2006-09-21
Oops!  I forgot to subscribe, and this is the only way I know how to do it.

Rob

---

### Post by Rob_Frohne on 2006-09-22
I did a 

sudo /etc/init.d/lvm stop 

and then I noted a problem with ALSA shutting down when trying to shutdown the computer.  So I recalled that I have been running self compiled ALSA driver here, and I hadn't recompiled it with the latest kernel update from Ubuntu.  I did that and the LVM stuff seems to have cleared up.  

I also had a smartmedia card in the PCMCIA slot of the computer and I removed that.  I put it back in and the LVM messages haven't returned.  

The funny thing is, I though I wasn't using LVM, as I did the regular gui install of ubuntu and I thought LVM had to do with raid or something.

Rob

---


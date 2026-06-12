---
title: "tsclient error"
date: 2005-09-01
forum: Desktop Environments
---

### Post by Scanner on 2005-09-01
I have installed tsclient 0.140 and rdesktop 1.3.1 on Kubuntu Hoary.  tsclient seems to work fine execpt that when I close the windows session (Win2003 Server in Console Mode) I get a Terminal Server Client Error dialog box on my Linux machine that says

 An Error has occured.
NOT IMPLEMENTED: System pointer message  0x7f00

and tsclient does not save changes made to the server profile.  I have tried not going to console mode, and changing display and redirect settings same thing.

Any help on this would be appreciated.

---

### Post by mlomker on 2005-09-02
Hmm.  I use Tsclient all of the time and haven't had that problem (I'm a *cough* NT Admin).  All of our servers are still at Win2k, though.  Have you tried downloading and compiling the latest version of rdesktop?  They are up to 1.4.1 now...you can find it through sourceforge.net.

---

### Post by ned.b on 2005-12-22
This error only seems to occur on 2003 Server, I have also tested the Terminal Services Client on 2000 Server and XP Pro and both run without this error.

---

### Post by biguns on 2006-01-07
I am having the same problem as you. I also in connecting to W2k3 server. Did you ever resolve this?

Correction: I may have figured it out. In the protocol selection, instead of using the default RDP, use RDPv5. It worked for me.

---

### Post by Scanner on 2006-01-09
No I was still having problems I will try this and see if it helps.

---

### Post by fdsg72-lux on 2006-10-24
Using RDPv5 works like a charm on Win2K3 hosts - thanks a lot for that tip - somehow never bothered to try it out but now it looks like such the obvious thing to try ](*,) 

Ubuntu forums rock!

---


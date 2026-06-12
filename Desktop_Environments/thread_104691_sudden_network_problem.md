---
title: "sudden network problem"
date: 2005-12-16
forum: Desktop Environments
---

### Post by linuxgrrl on 2005-12-16
hi,
I used to have a working samba and webmin here.
suddenly (within the past few days) my windows box is unable to connect.  When I try to get into webmin to try to fix it, I get "firefox can't establish a connection to the server at localhost:10000.
Tried restarting samba, no luck
INternet is working fine.
Had my samba settings just so, am not sure what could have broken it.
Not sure even where to start with this one!
help!
Mary

---

### Post by afhp on 2005-12-16
Sounds like it is webmin, not samba, that is not running. Can you check ?

---

### Post by linuxgrrl on 2005-12-17
[QUOTE=afhp]Sounds like it is webmin, not samba, that is not running. Can you check ?[/QUOTE]

You are correct.  I started webmin manually, and restarted samba from there.  The XP box still won't connect ("view workgroup computers" hangs for a while, then gives "mnshome [my workgroup] is not available. You might not have permission to access this resource").

I'm reluctant to mess with my samba settings since they were working so well before ... any thoughts on what I should check or change first?  

I upgraded firefox on both machines yesterday but it's hard to believe that could be it.  But who knows ...

---

### Post by linuxgrrl on 2005-12-17
[QUOTE=linuxgrrl]You are correct.  I started webmin manually, and restarted samba from there.  The XP box still won't connect ("view workgroup computers" hangs for a while, then gives "mnshome [my workgroup] is not available. You might not have permission to access this resource").

I'm reluctant to mess with my samba settings since they were working so well before ... any thoughts on what I should check or change first?  

I upgraded firefox on both machines yesterday but it's hard to believe that could be it.  But who knows ...[/QUOTE]

Thanks for your help.
Okay, the problem seems to be solved now (other than the mystery of why webmin didn't start at boot time.)

The workgroup names didn't match, so I changed the samba name to match the one that Winxp was looking for.

Now why was the &*%$ network even working at all before???  I guess I'll never know.

---

### Post by HermanAB on 2005-12-17
Here is a Samba debugging guide:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---


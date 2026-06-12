---
title: "ubuntu 64 bit freezes when click on logout icon"
date: 2007-11-26
forum: Desktop Environments
---

### Post by marcadams on 2007-11-26
Hi;

I've had 64 bit Gutsy installed since it's release (over a month now).
However since around a week ago, every time I press the log-out icon on the gone panel, the desktop freezes - it will not accept any user interaction. :confused:

My only option appears to be <Cntrl>, <ALT> <BACKSPACE>

I have not recently installed any new applications, or knowingly changed my system configuration - so I believe one of the recent updates was the culprit.


My system:
MB  = EPoX EP-9NPA+ Ultra  (nForce4 Ultra)
CPU = AMD Athlon 64 3
Gcard = Gainward GeForce 6200 (Nvidia)

Any suggestions would be greatly appreciated !

---

### Post by marcadams on 2007-11-26
FYI - I have just disabled the nvidia restricted driver and restarted,
The problem still remains...

---

### Post by marcadams on 2007-11-26
I've actually resolved the issue. 

It appears if you disable "power manager" option via the "sessions" dialogue, the desktop will freeze when the logout button is pressed.

Re-enabling this option corrects this problem,

---


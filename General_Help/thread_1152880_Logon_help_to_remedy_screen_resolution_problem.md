---
title: "Logon help to remedy screen resolution problem"
date: 2009-05-08
forum: General Help
---

### Post by David Brant on 2009-05-08
Hello

I foolishly altered my screen resolution, which i assumed would return to the former resolution before i confirmed things were not OK. It didn't ... and now i see nothing after logon!

I have other non-super user accounts, but that doesn't help me. I also notice there are alternative logon options, but i need someone to talk me through the process before i make things worse before better!

Your help would be greatly appreciated

Dave

---

### Post by David Brant on 2009-05-08
Phew, sorted it! 

Resetting an out-of-range resolution

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Logon/Options

Select Session/Failsafe Terminal

```
rm ~/.config/monitors.xml
exit
```

Hopefully you will find, as i did, everything is restored as was.  :)

---


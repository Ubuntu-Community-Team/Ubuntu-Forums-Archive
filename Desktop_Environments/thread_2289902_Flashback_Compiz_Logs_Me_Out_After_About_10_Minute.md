---
title: "Flashback Compiz Logs Me Out After About 10 Minutes 14.04"
date: 2015-08-07
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-08-07
Hello,

Intermiitantly, after about 10 min, the xscreensaver timeout, Flashback Compiz sessions will log me out; and I have to log back in. This is really mysterious. Any help appreciated.

Thanks, Hannibal

---

### Post by workshopsystems on 2015-08-13
```

xset -d :0 s 0

```

try that and see if it still happens

I doubt very much its compiz causing the problem its more like lightdm isnt fully installed or missing packages and when you use some applications and increase cpu or graphics load , it defaults to tty 
it sounds like a graphic issue 

compiz wont log you out, it will either work or not work or work but function wrong i.e windows appear with no titlebar etc etc  , but lightdm will log you out if theres a failure in xorg 

try reinstalling lightdm

```

sudo apt-get --reinstall lightdm

```

---

### Post by coljohnhannibalsmith on 2015-08-13
Your description sounds exactly like what I've been experiencing; but neither of the proposed fixes worked.

Thanks, Hannibal

---


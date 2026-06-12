---
title: "Xubuntu session manager"
date: 2006-05-22
forum: Desktop Environments
---

### Post by asundaresan on 2006-05-22
Hi,

I use xubuntu with breezy. Whenever I reboot my laptop and log into xubuntu, it loads some (apparently) old session with a half dozen terminals. Each of them asks for my ssh key password. There also pops up several messages that say
```
Could not grab keyboard. A malicious client may be eavesdropping on your session
```

Are these related?

Where can I delete the saved session? I have unchecked the limited options in the Xfce settings manager.

Thanks,
Aravind.

---

### Post by encho on 2006-05-22
The message does not look good (hope you're not hacked). I use dapper's xfce (just love 4.3), but maybe this applies to you as well.

There are two folders of interest:
~/.config/autostart where default sessions are (those that you can change through xfce settings menu)
~/.cache/sessions where autosaved sessions are.

Hope this helps.

---

### Post by asundaresan on 2006-05-25
Hi encho,

Thanks for the info. I'll see if the problem vanishes when I prevent multiple terminals from opening up and asking me for the ssh private key. The settings seem to be slightly different for xfce 4.2 in breezy. I'm looking forward to trying dapper when it is released.

I hope I'm not hacked, because I am usually behind a proxy and I haven't installed any fancy stuff.

---

### Post by asundaresan on 2006-06-05
The problem was solved when I removed the offending file: ~/.cache/sessions.

Thanks,
Aravind.

---


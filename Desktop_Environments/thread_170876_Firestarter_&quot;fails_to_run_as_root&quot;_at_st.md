---
title: "Firestarter &quot;fails to run as root&quot; at startup"
date: 2006-05-05
forum: Desktop Environments
---

### Post by linuxNewb on 2006-05-05
NOTE: I know that this issue has been raised in other threads, but no real answers have been given, for some reason they all stray off topic, and obviously this must be a somewhat common problem...

After apt-getting firestarter, every time I boot into ubuntu, I get a small window that asks for my password. The it always says, "failed to run firestarter as root". Firestarter does actually seem to be running in spite of this error message; however, this is really annoying. 

Does anyone know how to stop firestarter from asking for a password to run as root at startup? 

As a side note... I used firestarter on this machine before having to reinstall ubuntu, and it never did this before. Thanks in advance.

---

### Post by Ramses de Norre on 2006-05-05
Did you set it in your start up programs? If so you'll need to set it to nopasswd in sudoers.
Can you do sudo firestarter? And the output of ps -aef|grep firestarter may reveal some info.

---

### Post by linuxNewb on 2006-05-05
[QUOTE=Ramses de Norre]Did you set it in your start up programs? If so you'll need to set it to nopasswd in sudoers.
Can you do sudo firestarter? And the output of ps -aef|grep firestarter may reveal some info.[/QUOTE]

Thanks for your reply. I took it out of the startup list, and it doesn't do it anymore.

---


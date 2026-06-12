---
title: "app or process using sudo"
date: 2008-03-20
forum: Desktop Environments
---

### Post by prezbedard on 2008-03-20
I was installing software using synaptic. I then launched aptitude using sudo when I couldn't find a certain package. I got the error that it couldn't lock files and realized synaptic was still open. I closed it. I ran sudo aptitude again and the same thing happened. It didn't even ask for the password. This makes me think there is some process locking up the suo root access. I have browsed the processes but can't really determine what it is? Anything I can to avoid rebooting?

Thanks,

---

### Post by prezbedard on 2008-03-20
ok I  found a process running "apt-get -qq update" I didn't launch this. Could this be related to the auto update notifier or is it possible the process locking up my sudo access?

---

### Post by prezbedard on 2008-03-20
ok I have it asking for the sudo password but stiall can't lock file. I believe do to the ps "apt-get -qq update" is it ok to kill this?

---


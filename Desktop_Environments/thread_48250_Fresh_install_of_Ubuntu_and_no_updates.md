---
title: "Fresh install of Ubuntu and no updates?"
date: 2005-07-11
forum: Desktop Environments
---

### Post by denzilla on 2005-07-11
I just installed Ubuntu on a PC and there are no updates whatsoever! Something change?

---

### Post by tread on 2005-07-11
Did you enable all the repositories? If the only repo turned on is the cd, you won't find any updates :)

---

### Post by denzilla on 2005-07-11
[QUOTE=tread]Did you enable all the repositories? If the only repo turned on is the cd, you won't find any updates :)[/QUOTE]


I didn't change anything. The last time I installed Ubuntu, it found updates within 5min of installing. I thought you didn't need to change anything to just get security updates?

---

### Post by varunus on 2005-07-11
It should have set up all the repositories for you, unless there was some problem detecting your net connection.  Either that, or you did a network install, which will install the newest packages from the internet during the installation.  What are the contents of your /etc/apt/sources.list?

---

### Post by denzilla on 2005-07-11
I got it fixed now :) 

When I use synaptic, it says that manual intervention is required to update mozilla-firefox and mozilla-gnome-support. What is the proper way to deal with this situation?

---

### Post by varunus on 2005-07-12
Go ahead and manually update them.  It'll get you the new firefox 1.0.4.   :) 

Glad you got it working.

---

### Post by denzilla on 2005-07-12
[QUOTE=varunus]Go ahead and manually update them.  It'll get you the new firefox 1.0.4.   :) 

Glad you got it working.[/QUOTE]


Thanks :)

---


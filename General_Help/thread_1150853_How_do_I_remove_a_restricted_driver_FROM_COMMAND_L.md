---
title: "How do I remove a restricted driver FROM COMMAND LINE?"
date: 2009-05-06
forum: General Help
---

### Post by AnthraxMouthwash on 2009-05-06
Hi.

I just installed the ATI graphics driver from restricted drivers.  Now Ubuntu fails to boot.

How can I remove the driver from the command line?

Thanks.

---

### Post by dradius on 2009-05-06
If you know the ATI driver package names you can do:

sudo apt-get remove packagenames

---

### Post by AnthraxMouthwash on 2009-05-06
It's not a package.

I installed it from the "proprietary" Hardware Drivers GUI.  Sorry, maybe I should edit post title to say "proprietary" and not "restricted".

Duh.  My mistake.

---

### Post by AnthraxMouthwash on 2009-05-06
Okay.  I can't edit the thread title.

Sorry.

Anybody reading this, my question is about removing a propriatary hardware driver from the command line because the ATI graphics driver has totally messed up Ubuntu and it crashes at the end of booting.

---

### Post by oldos2er on 2009-05-06
> **AnthraxMouthwash said:**
> It's not a package.

I installed it from the proprietary drivers GUI.  Sorry, maybe I should edit post title to say "proprietary" and not "restricted".

Duh.  My mistake.

 It's still a package.  Use "apt-cache search [packagename]" to find it, "sudo apt-get remove [packagename] to uninstall it.

---

### Post by AnthraxMouthwash on 2009-05-06
Thanks.

apt-cache search helped a lot.  I found it pretty much straight away.  Removed.  All is good now.

Needless to say, I won't be trying to install the ATI gfx drivers again.  No accellerated gfx for me... not that I mind.

---


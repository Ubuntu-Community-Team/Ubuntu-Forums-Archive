---
title: "bootup scripts at user login"
date: 2012-03-02
forum: Desktop Environments
---

### Post by kishon on 2012-03-02
i want to have specific scripts run at bootup when a particular user logs in. (this is in a multi user ubuntu pc). And i want to have different scripts for different user. Any help on where such scripts should be kept?

---

### Post by enjoijesus94 on 2012-03-02
Yes Go To System > Prefrences > Startup Applications

There You Can Select What Applications Or Even Scripts To Be Executed On Startup.

:popcorn:

---

### Post by Bobhuber on 2012-03-02
> **kishon said:**
> i want to have specific scripts run at bootup when a particular user logs in. (this is in a multi user ubuntu pc). And i want to have different scripts for different user. Any help on where such scripts should be kept?
$HOME/.profile

---

### Post by el_baby on 2012-05-28
> **Bobhuber said:**
> $HOME/.profile

but ~/.profile is executed when you start a shell (e.g. when you launch a terminal).

If I start a plain unity session, ~/.profile is not run (at least using unity under precise).

---


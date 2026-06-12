---
title: "is there an alternative network config tool?"
date: 2005-07-20
forum: Desktop Environments
---

### Post by holr on 2005-07-20
hello!

working with kubuntu, and upgraded everything to kde 3.4.1 (by adding the extra lines from kubuntu.org into my etc/apt/sources.list file) but still getting that confounded problem in the control panel where it will not work with the network settings!

I can normally go through the console and do sudo kcontrol which helps, but it still hangs when I want to enable my wifi on bootup. I have to keep doing sudo kcontrol and enabling the wifi adapter everytime i load up!

I know that gnome had a nice working tool (system-config-network or something???) but if i was to install this, id also need a whole group of other gnome related dependencies, resulting in a big download.

Does anyone know of a small dedicated network configutation tool, like the one for gnome, but just for kde? I suppose I could modify /etc/network/interfaces manually, but I dont know enough about what options I need...

thanks!

---

### Post by Feanor on 2005-07-20
Do this

```
kdesu kcontrol
```

Network settings should work now  ;-)

---

### Post by holr on 2005-07-20
[QUOTE=Feanor]Do this

```
kdesu kcontrol
```

Network settings should work now  ;-)[/QUOTE]

whats the difference between doing "sudo kcontrol" and "kdesu kcontrol" btw?

Thanks for the help too!

---

### Post by Feanor on 2005-07-20
Exactly I don't know, I think depends on parameters and paths on which works the commands...

---

### Post by staticvoid on 2008-02-11
in gnome gksu and sudo are different for this reason:

gksu runs app with admin privledges
sudo runs the command in a terminal

:)

---


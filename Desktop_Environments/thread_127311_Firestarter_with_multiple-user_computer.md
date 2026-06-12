---
title: "Firestarter with multiple-user computer"
date: 2006-02-08
forum: Desktop Environments
---

### Post by nmatheis on 2006-02-08
Hello
I have four users on my computer. I added Firestarter and turned it on in my user.  From reading over some posts and the Ubuntu FAQ, I learned that Firestarter configuers iptables, which in turn starts up every time I login.  Sound right?  So what about the other users on the computer?  Does the firewall start up for them, too, since I started it in my (administrator) user?
Thanks!
Nikolaus

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=nmatheis]Hello
I have four users on my computer. I added Firestarter and turned it on in my user.  From reading over some posts and the Ubuntu FAQ, I learned that Firestarter configuers iptables, which in turn starts up every time I login.  Sound right?  So what about the other users on the computer?  Does the firewall start up for them, too, since I started it in my (administrator) user?
Thanks!
Nikolaus[/QUOTE]
When the computer boots, firestarter configures netfilter (iptables is a command line front end to netfilter).  So it will be configured for all your users.  Typically, it requires admin privileges to alter the settings.

---

### Post by nmatheis on 2006-02-09
thanks for the reply!  is this true for other firewall apps, like guarddog?

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=nmatheis]thanks for the reply!  is this true for other firewall apps, like guarddog?[/QUOTE]
Yes.

---

### Post by alfonz on 2006-02-09
Sorry this may be off topic but I've only used Firestarter, does anyone recomend another one or Firestarter is as good as the rest of em.

---

### Post by cwaldbieser on 2006-02-09
[QUOTE=alfonz]Sorry this may be off topic but I've only used Firestarter, does anyone recomend another one or Firestarter is as good as the rest of em.[/QUOTE]
I like how the GUI in firestarter is really simple to use.  For my home use, that is about all I need.  guarddog was more explicit about fine-grained control, but I also found it more tedious to set up and change.  You can write your own iptables script, but that really forces you to think carefully about what rules you REALLY want to enforce.

---


---
title: "User Management: K/X/Ubuntu"
date: 2007-06-04
forum: Desktop Environments
---

### Post by teejay17 on 2007-06-04
Can someone point me to a how-to that illustrates how to set up different users? I would like to set up a more secure system, so I'd like to get out of Administrator mode on a few different computers.
What do I need to know/do?

---

### Post by blackened on 2007-06-04
What exactly do you mean by "get out of Administrator mode"? Are you running as root all the time?

---

### Post by teejay17 on 2007-06-04
> **blackened said:**
> What exactly do you mean by "get out of Administrator mode"? Are you running as root all the time?
Well, I think so. I'm using the initial account that I set up when I installed. Although I am prompted to enter my password to do any updating and installations, I think it's safer to be in another account for regular use, no? (Another question: can I do "sudo" actions in another account other than the administrator one?)
Of course, I still need to know how to set up a regular user account too.

---

### Post by blackened on 2007-06-04
Since Ubuntu has root user access disabled by default, then if you didn't explicitly set it to be that way, then it isn't that way. In which case your PC will be no safer if you log in under another username unless you were to choose for that other username not to have sudo powers, and even that wouldn't make you much safer than you already are.

 A better place to start, as far as security, would be to lock down inadvertently open ports (all ports default to closed on initial Ubuntu install), secure access points and routers, and set up iptables. Some info on those sorts of things at [http://www.linuxsecurity.com/content/view/101892/155/]("http://www.linuxsecurity.com/content/view/101892/155/").

---

### Post by teejay17 on 2007-06-04
> **blackened said:**
> Since Ubuntu has root user access disabled by default, then if you didn't explicitly set it to be that way, then it isn't that way. In which case your PC will be no safer if you log in under another username unless you were to choose for that other username not to have sudo powers, and even that wouldn't make you much safer than you already are.

 A better place to start, as far as security, would be to lock down inadvertently open ports (all ports default to closed on initial Ubuntu install), secure access points and routers, and set up iptables. Some info on those sorts of things at [http://www.linuxsecurity.com/content/view/101892/155/](http://www.linuxsecurity.com/content/view/101892/155/).

Thanks for the link. So basically, if I just install Ubuntu as-is, and log in using the user name and password I initially created, then I should be fairly safe?

---

### Post by blackened on 2007-06-04
Concerning the OS, yes, you should be fairly safe with the default install, but you should always be concious of your general network security situation and problems that might arise from it.

---


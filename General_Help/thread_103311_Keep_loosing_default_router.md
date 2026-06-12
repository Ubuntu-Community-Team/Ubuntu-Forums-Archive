---
title: "Keep loosing default router"
date: 2005-12-13
forum: General Help
---

### Post by guice on 2005-12-13
Everytime I reboot, I loose my default router. There's no -P for "permanent" command on route. How can I get a permanent default router? Using the network control panel doesn't work, it's actually the reason why my default route will no longer stick.

---

### Post by amohanty on 2005-12-14
Are you using dhcp to get an ip address or do you have a static ip?

---

### Post by guice on 2005-12-14
[QUOTE=amohanty]Are you using dhcp to get an ip address or do you have a static ip?[/QUOTE]
Static IP assignment.

hmm .. do I need to add an /etc/defaultrouter file? I looked for it, but wasn't there. Wasn't sure if things were different in Kubuntu. There's a lot different, as far as config files, than the Solaris systems I work on at work.

---

### Post by PokerFacePenguin on 2005-12-14
[QUOTE=guice]Static IP assignment.

hmm .. do I need to add an /etc/defaultrouter file? I looked for it, but wasn't there. Wasn't sure if things were different in Kubuntu. There's a lot different, as far as config files, than the Solaris systems I work on at work.[/QUOTE]

I usually use a dhcp address off of my router, but when I want a static one, i have a simple bash script that adds my default route...perhaps this could be a solution for your issue.  There is probably a better solution, but this could work for you until you discover such.

---


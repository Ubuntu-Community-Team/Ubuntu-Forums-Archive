---
title: "Unable to activate eth1 from control center in KDE"
date: 2005-10-12
forum: Desktop Environments
---

### Post by doctorphoton on 2005-10-12
Hello,

I am using Kubuntu. The problem i am facing is:
When ever i start kubuntu and login into kde and after logging in , plug the LAN Cable into eth1(LAN CARD) i am unable to get ip address from dhcp and also, i am unable to enter to administration mode of network settings in control center and also am not able to  configure my eth1 from network settings in control center, can not enable and disable the eth1 or can not change any network settings. i click the administration mode , enter password and again it redirects to the main page of control center.

but when i keep the LAN Cable entered into my laptops LAN CARD and restart the computer, during restart it gets ip address for eth1 from dhcp and then i am able to access network settings administration mode from control center and can configure, enable and disable eth1. when computer is already restarted wiithout pluging the cable and i plug the cable i can not get ip address.

why is it so?

I want to start my computer,log in to kde and then i want to plug the lan cable and want to do changes in network settings from administrration mode.
how to do this?

Thanks
Doctor PHOTON

---

### Post by hlfrk414 on 2005-10-12
I had trouble getting into administrator mode as well when i first started using kubuntu, but work through it, as kubuntu is one of the easiest distros to use overall. 
Go to the Control Center Icon in the K menu, right click, and Edit item. Go to the box that says 'run as a different user', check it, and type in the user 'root'. Now start  it up and enter **your** password to run it as root Works around the control menu's bugginess. Might be a good idea to copy the control center item and make a new item where you start as root, since you probably don't always need to start it as root.

---

### Post by doctorphoton on 2005-10-13
Hey dear thank you very much
the problem is solved.

---


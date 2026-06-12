---
title: "How Does A Person Get Rid Of The Networkmanager Applet"
date: 2010-10-02
forum: Desktop Environments
---

### Post by NoSalt on 2010-10-02
Hello All

    I have just installed XUbuntu 10.04 onto my computer and I am in the process of customizing it. I have two questions regarding the menubar Networkmanager Applet. First, I already edited the /etc/network/interfaces file; so how do I get the Networkmanager Applet in the menubar to stop trying to control eth0 on me? I will set the interfaces file to one thing, but as long as Networkmanager Applet is active, it will always try to re-assign the IP address to some dynamic address. Second, and most important, how do I remove the Networkmanager Applet from the "Notifications" area? I don't need that applet and I don't want it hanging around in the Notifications area.

Thanks for taking the time to read. Have a good night.  :)

---

### Post by lloyd_b on 2010-10-02
> **NoSalt said:**
> Hello All

    I have just installed XUbuntu 10.04 onto my computer and I am in the process of customizing it. I have two questions regarding the menubar Networkmanager Applet. First, I already edited the /etc/network/interfaces file; so how do I get the Networkmanager Applet in the menubar to stop trying to control eth0 on me? I will set the interfaces file to one thing, but as long as Networkmanager Applet is active, it will always try to re-assign the IP address to some dynamic address. Second, and most important, how do I remove the Networkmanager Applet from the "Notifications" area? I don't need that applet and I don't want it hanging around in the Notifications area.

Thanks for taking the time to read. Have a good night.  :)

Personally, I just do "sudo apt-get remove network-manager" to completely uninstall it.  Like you, I prefer handling my network by modifying '/etc/network/interfaces', so I have no use for even having network manager installed.

Lloyd B.

---

### Post by NoSalt on 2010-10-02
lloyd_b ... thanks, that worked great. Any tips on how to get rid of the annoying little Networkmanager applet in my menu bar?

Thanks again, for taking the time to read and reply.   :)

---

### Post by NoSalt on 2010-10-03
Never mind ... when I applied the Windows fix (i.e., rebooted) the menu-bar icon was gone. Very cool.

---


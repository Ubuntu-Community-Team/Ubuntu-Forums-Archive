---
title: "VNC into Intrepid machine"
date: 2008-12-30
forum: General Help
---

### Post by vishnumrao on 2008-12-30
I have a machine running Intrepid Ibex. Since it sits in another lab, I remote login into it rom a Xp machine using RealVNC. 

Problem: Each time the machine is rebooted, I have to login to GNOME to be able to use the machine. Here is the method I use: [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

Question: Is there a way to remote desktop into a Ubuntu machine without having to have GNOME session live. The LCD screen, mouse and keyboard connected to this machine were removed. It now is connected to the LAN, so remote desktop is my only option. (I can temporarily connect all above mentioned peripherals.)

---

### Post by kaginken on 2008-12-30
You can enable the auto-login so it just boots up into the default environment - however this could be a big security concern so I wouldn't recommend it unless you are on a very secure network, or don't care...

To enable auto-login, you have to go into the System/Administration/Users & Groups panel (can't give you the exact path at the moment) and you will see an option there to allow automatic logins.

Hope this helps!

:guitar:

---

### Post by vishnumrao on 2008-12-30
kaginken,

I did think about this option. But I do not want to enable auto-login.

Another reason, I am looking for an alternative method to remote desktop is because, in the present method the screen is not locked after I remote login to the machine. So if someone connected a LCD monitor, mouse, keyboard to this machine, they could easily view and access this machine. I would like to lock the screen too. 

For the time being, I will enable auto login and use the machine. But would like to get the same functionality as a windows remote desktop, where in the screen is locked.

---


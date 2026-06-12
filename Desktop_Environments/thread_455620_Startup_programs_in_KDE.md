---
title: "Startup programs in KDE"
date: 2007-05-26
forum: Desktop Environments
---

### Post by fakie_flip on 2007-05-26
How can I get Kopete to stop coming up each time I reboot and login? I want to set all the start up programs back to default in KDE. Thanks

---

### Post by firephoto on 2007-05-26
Unless you have a manually saved session, just make sure you quit kopete instead of just closing the window which leaves it in the system tray. KDE remembers what applications are open when you logout and saves them to the session that is restored by default when you log back in.

---

### Post by Nythain on 2007-05-26
yeah, in a nutshell... make sure you close the programs you dont want automatically loaded before you shutdown or reboot... also you can in terminal type
kdesu kcontrol
then navigate
kde components-------> session manager------------> click the option to start with an empty session

---

### Post by fakie_flip on 2007-05-27
Thanks. I choose "Start with an empty session." in KDE Control Center.

---


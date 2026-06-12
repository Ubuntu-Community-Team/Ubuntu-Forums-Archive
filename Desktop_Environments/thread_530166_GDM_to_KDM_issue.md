---
title: "GDM to KDM issue"
date: 2007-08-20
forum: Desktop Environments
---

### Post by chinocracy on 2007-08-20
Not a serious problem, but I am wondering how to successfully use KDM on my initially GDM installation. I had Ubuntu Dapper first, then I added components to enable Kubuntu. KDE works fine, though the login screen is still GDM. I tried the instructions to change to KDM. The KDM login screen appears, seems fine. But when I log in with user name and password, the display just flickers as if loading, and then goes back to the KDM login screen. So strangely, KDM login can't login to Kubuntu! Anything I'm missing here?
Also, since my boot-up meter changed to Kubuntu, how do I change it back to the Ubuntu-style? Thanks.

---

### Post by prince_niceguy on 2007-08-22
Run the following command

sudo dpkg-reconfigure kdm

select kdm again and try to login.

---

### Post by zoobave on 2007-08-23
edit the following file and add the path of WDM instead of GDM
/etc/X11/default-display-manager

regards,
Zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com")

---


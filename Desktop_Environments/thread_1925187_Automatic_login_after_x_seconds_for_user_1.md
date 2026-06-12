---
title: "Automatic login after x seconds for user 1"
date: 2012-02-14
forum: Desktop Environments
---

### Post by 3svb on 2012-02-14
All,

I have a multi-user system (11.10).
Is it possible to trigger an automatic login after x amount of seconds ?

Case:
I want to be able to intervene the login process so that user 2 is able to login before the system loggs in user 1.

Thanks in advance !

---

### Post by 3svb on 2012-02-15
**[EDIT]**

Damn! This does not apply to 10.04 and up ...
Maybe this can do the trick ?

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

**[/EDIT]**



Maybe I found a solution. 
When I get home, I will give it a try and let you guys know.


.....
You  can also load it  by pressing  **Alt + F2** and typing **gksu /usr/sbin/gdmsetup** in Run Application box.

[IMG]http://cloud.addictivetips.com/wp-content/uploads/2009/06/login-window-alt-f2.jpg[/IMG]

This will open the **Login Window Preferences** window. Now, to enable auto login, go to **Security** tab and check **Enable Automatic Login** and enter user name for your system. You can also set delay in auto login by checking **Enable Timed Login** and selecting time in seconds. If you enable it, your system will wait for specified number of second before logging you.

[IMG]http://cloud.addictivetips.com/wp-content/uploads/2009/06/security-tab.jpg[/IMG]

Click Close and reboot your system. Now you won&#8217;t see the login windows anymore and won&#8217;t need to type the password during every startup.  Enabling automatic login is not recommended because it will lead to higher security risk. Enjoy!

Source:
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-ubuntu-user-login-window/]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-disable-ubuntu-user-login-window/")



Anyone tried this already ?

---

### Post by Krytarik on 2012-02-15
I presume that you are using the default display manager of Oneiric 11.10, LightDM. Find/add this key to the "[SeatDefaults]" section of your "/etc/lightdm/lightdm.conf" and set the timeout to your liking:
> autologin-user-timeout = Number of seconds to wait before loading default userSource: "/usr/share/doc/lightdm/lightdm.conf"

Regards.

---

### Post by 3svb on 2012-02-17
Thx Krytarik !

But I'm still not able to choose an alternative profile.
Bug is confirmed !

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/902852](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/902852)

---

### Post by Krytarik on 2012-02-17
> **3svb said:**
> Bug is confirmed !

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/902852](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/902852)
Make sure to both enlist yourself as 'affected by this bug' and subscribe to it, in order to both get notified about changes and raise the "bug heat". ;-)

---


---
title: "There was an error loading the theme Human [Resolved]"
date: 2007-02-06
forum: Desktop Environments
---

### Post by Knine on 2007-02-06
I installed Ubuntu on x86 PC, and it works well for quite a time.

But after some days, I reset the computer, and then when the initial screen is loaded, the following message is shown.

[IMG]http://jp1998.cafe24.com/1.jpg[/IMG]

And then I pressed OK button, the following message is shown.

[IMG]http://jp1998.cafe24.com/2.jpg[/IMG]

And then I pressed OK button again, the following dialog box is shown.

[IMG]http://jp1998.cafe24.com/3.jpg[/IMG]

But I can’t login, because the text field, named ‘Username’, is disabled.

 

However, in spite of this circumstance, remote login via XDMCP from another PC is possible.

But in case of remote login, the image of theme is not loaded with following screen.

 

[IMG]http://jp1998.cafe24.com/4.jpg[/IMG]

 

How can I solve this problem?

Can you help me?

---

### Post by Knine on 2007-02-06
How can I delete this post?
I'd written this reply for test...

---

### Post by aysiu on 2007-02-06
Can you try temporarily installing and using another GDM theme just to get you functional, and then we'll work on restoring the Human theme?

You can find other GDM themes here:
[http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=1661cb276c601b07e60b45b63d358230](http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=1661cb276c601b07e60b45b63d358230)

---

### Post by Knine on 2007-02-06
Thank you for your reply.
But I don't know how to install GDM theme...:( 
And almost all applications of Ubuntu quits unexpectedly with following dialog box for example.

[IMG]http://jp1998.cafe24.com/5.jpg[/IMG]

> **aysiu said:**
> Can you try temporarily installing and using another GDM theme just to get you functional, and then we'll work on restoring the Human theme?

You can find other GDM themes here:
[http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=1661cb276c601b07e60b45b63d358230](http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=1661cb276c601b07e60b45b63d358230)

---

### Post by aysiu on 2007-02-06
That's weird.

What happens if you try creating a test user. Does that test user run into the same problems?

Press Control-Alt-F1 and log in. Then type ```
sudo adduser testuser
sudo adduser testuser admin
sudo /etc/init.d/gdm restart
``` Then log in with the test user. If you're not getting all the same crazy errors, you can install a GDM theme by going to System > Administration > Login Window > Install Theme.

---

### Post by Knine on 2007-02-07
The problem has gone~~!!:guitar: 

I tried to system upgrade and install graphic card driver.
In that process, I rebooted PC, then screen has loaded normally.

Thank you anyway for your concern.):P 


> **aysiu said:**
> That's weird.

What happens if you try creating a test user. Does that test user run into the same problems?

Press Control-Alt-F1 and log in. Then type ```
sudo adduser testuser
sudo adduser testuser admin
sudo /etc/init.d/gdm restart
``` Then log in with the test user. If you're not getting all the same crazy errors, you can install a GDM theme by going to System > Administration > Login Window > Install Theme.

---


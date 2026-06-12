---
title: "Login Banner"
date: 2010-05-25
forum: Desktop Environments
---

### Post by btrichardson on 2010-05-25
Hello,

For legal reasons, I need to display a login banner on my Ubuntu 10.04 desktop machine that requires a person to acknowledge the contents of the banner by clicking a button before they are presented with a login screen. I had this working with 8.04, but the same configuration doesn't seem to work with 10.04. After searching for a solution on Google, the only thing I came across was a suggestion to simply edit the /etc/issue file, but that didn't make a difference.

Can someone please help me?!

--
Thanks!
Bryan

---

### Post by hictio on 2010-05-25
/etc/issue will work if you are login to the system via console, that is the CLI.
If you have a graphical login enabled, then you'd have to take a look at [gdm](http://en.wikipedia.org/wiki/GNOME_Display_Manager).
As I understand, gdm had quite a revamp recently on Ubuntu, but, perhaps this might give you a hint or two [Linux: Display a login banner for Gnome (GDM) Desktop](http://www.cyberciti.biz/tips/howto-unix-linux-change-gnome-login-banner.html).

What I'm not sure at all is how to actually make a pre-login window that actually has a button that the user has to click.

---

### Post by zencoder on 2010-05-31
Bryan, hictio is right /etc/issue and /etc/issue.net are where you want to enter any login banner information.  If you are running an SSH server, make certain to enable the **Banner /etc/issue.net** setting in **/etc/ssh/sshd_config** to display the warning before a user authenticates via ssh.

I have the same requirement as you and am looking into this also...I'll share whatever I happen to find for GDM.

---

### Post by e.meitner on 2010-06-02
See: 
[https://answers.launchpad.net/ubuntu/+source/gdm/+question/97156](https://answers.launchpad.net/ubuntu/+source/gdm/+question/97156)

---

### Post by btrichardson on 2010-06-08
Perfect! The answer on Launchpad worked great. Thanks!

---


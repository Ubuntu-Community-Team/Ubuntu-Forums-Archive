---
title: "root: no cd-rom or flash drive automount on desktop"
date: 2007-03-01
forum: Desktop Environments
---

### Post by gaspar on 2007-03-01
Help! After some time using Ubuntu, I got tired of sudoing everything, so I'm using my root account. The problem is, I don't have the icons for removable media on my desktop. I can mount them manually, but I don't want to do that.
So, any way to have them automounted and with icons on my gnome desktop?:( 
Thanks in advance!

---

### Post by scxtt on 2007-03-01
off the top of my head, check out /etc/group and take notice of any groups your "main user" (the one you 1st used before using root) is a part of - possibly adding "root" to those groups would solve your "problem" ...

FWIW, i'd stop using the root account as a GUI user ... if you don't want to type your sudo p/w continually, just keep a terminal open that you've done **sudo -s** in and it'll keep you in a root shell for the duration of your GUI login (even w/ your users env. variables) ...

---

### Post by gaspar on 2007-03-02
Thanks, I´ll try that as soon as I get home tonight. Just for curiosity, why did you stop using root in GUI?
And are you an ATHF fan too? cool! :)

---

### Post by hizaguchi on 2007-03-02
Using root for your normal user account just isn't a good idea.  Most software isn't intended to run with unlimited permissions because it would be easy for a bug to hide in a complicated GUI app that would normally be only a minor problem but that could cause much more damage if it is run as root.  Or so the thinking goes.  Sounds logical to me, so I don't do it.  You can get sudo to work without needing a password though.  I think you just have to add yourself to the "sudo" group with
```
sudo usermod -aG sudo yourusername
```
and it will stop asking for a password.  Either that or I messed with some other stuff and ended up with it that way.  Just make sure you put "-aG" in there and NOT just "-G".  Otherwise you'll do like I did and remove yourself from all groups except sudo, meaning you're not a part of the group "admin", meaning sudo doesn't work at all for you and it's time to reboot in single user mode. :)

---

### Post by solomone on 2007-03-02
> **gaspar said:**
> Help! After some time using Ubuntu, I got tired of sudoing everything, so I'm using my root account. The problem is, I don't have the icons for removable media on my desktop. I can mount them manually, but I don't want to do that.
So, any way to have them automounted and with icons on my gnome desktop?:( 
Thanks in advance!

I *highly* recommend that you don't use the root account for everything.  It's sooo easy to screw up your system as root user.  I mean, you might as well reformat your hard drive now and get it over with.  The small inconvenience of using sudo or sudo su, is nothing compared to hosing your system.

---


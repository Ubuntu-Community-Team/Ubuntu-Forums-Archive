---
title: "Sudo: stop asking password"
date: 2014-04-22
forum: Desktop Environments
---

### Post by magostinelli on 2014-04-22
Hi to all,

i upgrade my lubuntu to trusty, after the update and reboot, the system stopped to ask the sudo password for all operation: update, user admin, ubuntu software center, shutdown command.

I manually installed gksu and i run gksu-properties, everything seems ok.

Whatever administrative command I launch, the system never ask the password.

If I use command line and sudo it working, but not inside lubuntu (or unity) gui.

Probabily i must install another package, but which one?

Regards.

---

### Post by grahammechanical on 2014-04-22
There is nothing wrong. And you do not need to install another package. Many months ago the developers decided to reduce the number of times we were asked to authenticate tasks. This situation applied to 13.10 also and may be even to 13.04.

The developers reasoned that users were likely to authenticate out of habit if we were often asked for a password. And authenticating out of habit without checking what we are authenticating is a security risk.

So, for a long time, well before Trusty started development there would be times when we could install applications through the software centre and not be asked for a password and then there would be other times when we would be asked for a password. And the same with updating. You will find that if there is an upgrade to the Linux kernel you will need to put in your password.

I cannot remember ever needing to put in my password to shut down. And if the task I am doing is a user admin task, then most certainly I am required to put in my password. I have been running Trusty Tahr since its development first started. I have been updating daily and most of the time I have not needed to authenticate. This is my experience.

Regards.

---

### Post by magostinelli on 2014-04-23
Yes, it's wrong, because it's impossible to logout or to apply the update, I must use the command line.

For example, in lubuntu at logout: Access Denied: Operation not permitted

---


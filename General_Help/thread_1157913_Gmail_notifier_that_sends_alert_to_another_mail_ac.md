---
title: "Gmail notifier that sends alert to another mail account"
date: 2009-05-13
forum: General Help
---

### Post by ukdoc on 2009-05-13
Hi, I've searched the fora for something that might help me find a solution for this, but I'm a bit lost.

I have a gmail account that I don't receive that much mail into and don't check all that often. However, I can see that there are several gmail notification projects ongoing, but I'm not sure which one would work for me best.

What I would ideally want is for a notifier to run all the time (my ubuntu machine is constantly switched on) and if I receive an email in my gmail account to then send a basic email to my gmx email account with something like "New gmail message" as the subject. So in essence, rather than just having a notification on the ubuntu desktop, are there any notifiers that can also be configured to send an email alert in addition?

Thanks

[EDIT]: I don't want to just forward the emails to another account because they contain potentially confidential information that I don't want my secretary to have access to.

---

### Post by lovinglinux on 2009-05-13
Why don't you forward a copy of the e-mail from Gmail to the other account?

---

### Post by ukdoc on 2009-05-13
> **lovinglinux said:**
> Why don't you forward a copy of the e-mail from Gmail to the other account?

Please see my edit above!

---

### Post by lovinglinux on 2009-05-13
I don't think you will find a notification applet that would do that. But you could write a script.

You could for example use *offlineimap* to sync the gmail account with a folder in your machine, then use a script to check if there are contents on the local inbox folder, then send a message using *sendEmail*.

```
sudo apt-get install offlineimap sendemail
```

---


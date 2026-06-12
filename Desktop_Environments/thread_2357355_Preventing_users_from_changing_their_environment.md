---
title: "Preventing users from changing their environment"
date: 2017-04-01
forum: Desktop Environments
---

### Post by webmiester on 2017-04-01
Hi Everyone,

I have recently installed Ubuntu Mate 16.04 on a Raspberry pi 3.  I am thinking of using this device with Ubuntu for terminals in our hospital and our library.  this means that the device will be used by different people.  As terminals for use by different people, one problem is that they might manipulate the settings of their desktop environment (e.g. add panels, change background, etc.).  When they login as a non-root user, I am able to solve one problem wherein they cannot install any new applications (a problem I could not control with windows or android).  Using their account however, I noticed that I can still manipulate the settings of their graphical environment.  Is there a way that I can restrict them from manipulating these settings?

Thank you everyone.  BTW, although i know that this is Ubuntu running on a ARM processor, the commands and features look almost the same as their x86 brothers, so I suppose whatever suggestions you can give will most probably work on this machine too.

webmiester

---

### Post by SeijiSensei on 2017-04-01
You can try removing write privileges from the "hidden" directories and files, those whose names begin with a dot.  I'd start with .config which houses settings for many features and applications.
```

cd /home/username
sudo chmod a-w .config -R

```
The "-R" switch tells chmod to "recurse" through subdirectories below .config itself.

This can have other implications that may cause problems.  On the other hand, it sounds like you want to lock down the system in general, so this might be a good first step.

I use Kubuntu with the KDE interface, so I'm not certain whether this will work for Mate.

---

### Post by Habitual on 2017-04-02
"Kiosk Mode" may be a benefit, 
[http://www.omgubuntu.co.uk/2014/07/create-ubuntu-kiosk](http://www.omgubuntu.co.uk/2014/07/create-ubuntu-kiosk)

---

### Post by webmiester on 2017-04-02
> **Habitual said:**
> "Kiosk Mode" may be a benefit, 
[http://www.omgubuntu.co.uk/2014/07/create-ubuntu-kiosk](http://www.omgubuntu.co.uk/2014/07/create-ubuntu-kiosk)

This Kiosk system... Will I be able to configure it to work with different printers later on?  Let's say I want to install a printer on it, can I simply plug in a printer or configure CUPS?

This might work.  With this suggestion, do I manipulate the desktop so that it has the elements I would like on it, then simply apply this configuration so that their desktop look is "locked" into place afterwards?

> **SeijiSensei said:**
> You can try removing write privileges from the "hidden" directories and files, those whose names begin with a dot.  I'd start with .config which houses settings for many features and applications.
```

cd /home/username
sudo chmod a-w .config -R

```
The "-R" switch tells chmod to "recurse" through subdirectories below .config itself.

This can have other implications that may cause problems.  On the other hand, it sounds like you want to lock down the system in general, so this might be a good first step.

I use Kubuntu with the KDE interface, so I'm not certain whether this will work for Mate.

---

### Post by SeijiSensei on 2017-04-02
> **webmiester said:**
> This might work.  With this suggestion, do I manipulate the desktop so that it has the elements I would like on it, then simply apply this configuration so that their desktop look is "locked" into place afterwards?
Yes.Configure things the way you want them then remove the write permissions.  Obviously you should try it out on an account and see how it works.  If you find a configuration you like, you can edit the contents of /etc/skel to match.  Then any new accounts you create will have the same configuration.

---


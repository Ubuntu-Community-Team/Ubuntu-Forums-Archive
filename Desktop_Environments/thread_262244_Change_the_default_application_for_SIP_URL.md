---
title: "Change the default application for SIP URL"
date: 2006-09-21
forum: Desktop Environments
---

### Post by cybergypsy on 2006-09-21
Hi All

How do I change the default application when clicking on a SIP URL link , currently Firefox tries to start Ekiga , but I want to change its behaviour to use Twinkle instead.

I`m using Fluxbox under Ubuntu 6.06.1 on my Mac.

Any ideas ?

Thanks

---

### Post by stani on 2006-10-01
I guess this might help:
- type "about:config" in the location bar of firefox
- right click with your mouse and choose New>String
- give as name "network.protocol-handler.app.sip"
- give as value "twinkle" or "twinkle --call"

I have a question for you. How did you install twinkle, as I have the following problem:

```
stani@blue:~$ sudo apt-get install twinkle
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  twinkle: Depends: libccrtp1-1.4-0 but it is not going to be installed
E: Broken packages

```

So how can I install twinkle on Kubuntu edgy?

---


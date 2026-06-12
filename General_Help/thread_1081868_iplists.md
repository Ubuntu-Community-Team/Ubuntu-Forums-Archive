---
title: "iplists"
date: 2009-02-27
forum: General Help
---

### Post by mistypotato on 2009-02-27
Is it ok to install **iplist** even though I get a warning telling me that it's not authenticated and could be malicious?

thx

---

### Post by uljanow on 2009-02-27
It is required to import the key [1] because the package is signed.

[1] [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by mistypotato on 2009-02-27
Well, I installed iplist from synaptic so I assume it installed the key ahjamagically?

But even if not, I can't see how this would cause it to max out the cpu...


btw....this still is not resolved  :(

---

### Post by bodhi.zazen on 2009-02-28
It is hard to tell from your posting style what you are asking and what is not solved.

In therms of apt keys see : [https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

and

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

I see no relation of your first post :

> Is it ok to install **iplist** even though I get a warning telling me that it's not authenticated and could be malicious?

to your second post

> Well, I installed iplist from synaptic so I assume it installed the key ahjamagically?

But even if not, I can't see how this would cause it to max out the cpu...


btw....this still is not resolved  :sad:

What is your problem ? with keys ? what do keys have to do with your cpu ? What is "still not resolved" ?

this does not really seem to be a security question but rather a general help question so I am moving your thread to general help.

---

### Post by mistypotato on 2009-02-28
> **uljanow said:**
> It is required to import the key [1] because the package is signed.

[1] [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

Hi uljanow,

When I went back and read your installation post again, I noticed it says the key will be automatically installed using the sudo apt-get installation process so I guess that answers my initial question.

For some reason, the program is still maxing out the cpu and I've been through the logs and all but can't find the cause.  It must be hooking something that can't complete or something like that?  It does this even before I try to "enable" it.

Is there another process you know of that ipblock depends on that I might try re-installing to correct this?

Happy weekend! :KS

---


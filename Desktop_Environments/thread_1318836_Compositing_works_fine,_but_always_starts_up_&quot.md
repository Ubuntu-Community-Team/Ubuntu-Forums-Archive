---
title: "Compositing works fine, but always starts up &quot;temporarily disabled&quot;"
date: 2009-11-07
forum: Desktop Environments
---

### Post by PeEllAvaj on 2009-11-07
Whenever I start the computer, or logout and log back in to the desktop environment, compositing is "temporarily disabled" according to the System Settings manager.  It always works fine to hit alt+shift+F12 to re-enable it, but I can't figure out why it is turning off in the first place.

Everything in /var/log that contains "composit*" only talks about it being enabled successfully, and gives me no idea what is breaking it.

Any ideas, or logs I can post to figure this out?
Thanks in advance!

---

### Post by Untitled_No4 on 2009-11-08
Do you have an ATI graphic card using fglrx? It seems to be a problem reserved for us. Anyway, you don't have to live with it.

Open your System Setting, go to Desktop and in the Desktop Effects section go to Advanced. Tick Disable functionality checks, apply and you should be good to go.

---

### Post by vertago1 on 2010-01-10
> **Untitled_No4 said:**
> Do you have an ATI graphic card using fglrx? It seems to be a problem reserved for us. Anyway, you don't have to live with it.

Open your System Setting, go to Desktop and in the Desktop Effects section go to Advanced. Tick Disable functionality checks, apply and you should be good to go.

Thanks a ton!

---

### Post by pdaalder on 2010-01-11
Hi

I'm running 9.10 on a Dell D820 (2 years old). Doing what you suggest makes my screen turn grey, and then 10-15sec later the normal screen returns with the checkbox off. Any ideas?

---

### Post by huntz on 2010-02-12
> **Untitled_No4 said:**
> Do you have an ATI graphic card using fglrx? It seems to be a problem reserved for us. Anyway, you don't have to live with it.

Open your System Setting, go to Desktop and in the Desktop Effects section go to Advanced. Tick Disable functionality checks, apply and you should be good to go.

Thank you!

...and yes, I have an ATI with fglrx (ATI Mobility Radeon HD 4670).

Now, if only the resume/suspend issue will be fixed... I'll be an happy man :)

---


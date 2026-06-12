---
title: "copy/paste of text with accents &quot;lost in translation&quot;"
date: 2008-12-23
forum: Desktop Environments
---

### Post by liquidonline on 2008-12-23
Hi all,

I'm fortunate to work in an environment where I was given the choice of O/S to install on my system.   I installed ubuntu, but I'm running into a problem that greatly affects my work... and this is something that windows XP handles problem free.

It happens from time to time that I have to copy text from a client's email viewed through a web-based ticketing system and paste it into a prompt awaiting input in an ssh session.  Living in a bilingual city, I often have to input text written in french, containing accents.  When I copy/paste this into the terminal, it "appears" ok when I paste it, however, when the client winds up seeing the text that results, they get weird characters, or more commonly "blocks" instead of the letters with accents.  I've added language support for canadian french, and even when set prior to opening up the terminal, or the web browser, the same thing happens.  I've stopped short of changing the system language, as it forces too many other changes, not to mention it requires a session restart.

Does anyone have an idea how this quirk can be avoided, short of using windows, or some guidance as to where I need to look to find the root cause of this?

Thanks

---

### Post by Coder543 on 2008-12-23
perhaps... ssh only supports standard ascii? no, that can't be it... accents are standard ascii. Ok, this one I do not know. Why are you using SSH? That seems odd for a business/client model.

---

### Post by liquidonline on 2008-12-25
> **Coder543 said:**
> perhaps... ssh only supports standard ascii? no, that can't be it... accents are standard ascii. Ok, this one I do not know. Why are you using SSH? That seems odd for a business/client model.

I ssh to a netbsd server that I need to perform certain maintenance work on, and require inputing data provided to me  by  clients via email.

I get the impression that this requires setting the system language, which is highly annoying.

---

### Post by liquidonline on 2008-12-26
Anyone have any input on this? I'd really love to get this figured out, otherwise I'll have no choice but to run windows at work, and on my laptop, which I'm really trying to avoid...

---


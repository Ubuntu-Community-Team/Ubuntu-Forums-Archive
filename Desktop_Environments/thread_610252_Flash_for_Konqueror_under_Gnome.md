---
title: "Flash for Konqueror under Gnome"
date: 2007-11-11
forum: Desktop Environments
---

### Post by clintr on 2007-11-11
Hi,
I've got Ubuntu 7.10 installed, with the default desktop (GNOME?).  I installed Konqueror browser from the Synaptic Package Manager.
I tried to get Flash working in Konqueror with the instructions in this link:
[https://help.ubuntu.com/community/RestrictedFormats/Flash#head-4b931137affcbddef2ac9102a3d9fafde91f869f](https://help.ubuntu.com/community/RestrictedFormats/Flash#head-4b931137affcbddef2ac9102a3d9fafde91f869f)
(These instructions are for Ubuntu 7.04 but I couldn't find any specific to 7.10.)
When I get to the "extra step for Konqueror" I can't find 'Plugins' or 'Scan for new plugins'.  
Can you help me to get Flash plugin working in Konqueror?
Thanks,
Clint

---

### Post by djgenesis on 2007-11-12
Question (he says)
Why don't you just use firefox?

---

### Post by samwyse on 2007-11-12
[[img]http://xs221.xs.to/xs221/07461/plugins3.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs221&d=07461&f=plugins3.png)

---

### Post by clintr on 2007-11-12
Hello samwyse,

Thank you for your reply.  Unfortunately the "Plugins" choice in the left hand pane doesn't appear on mine.  (I will try to attach a screenshot.)

Thanks,
Clint

---

### Post by cookies on 2007-11-12
Try
```
sudo apt-get install konqueror-nsplugins
```

And then see if you get the plugins icon.

---

### Post by clintr on 2007-11-13
Thanks cookies, it worked!  I missed StrongBad...
How'd you come up with that magic incantation?  Could you send me a link to somewhere that explains how it worked?
Thanks again!
Clint

---

### Post by cookies on 2007-11-13
> **clintr said:**
> Thanks cookies, it worked!  I missed StrongBad...
How'd you come up with that magic incantation?  Could you send me a link to somewhere that explains how it worked?
Thanks again!
Clint

Well, I looked at the package description, and it seemed to be what you were missing. ;)

---


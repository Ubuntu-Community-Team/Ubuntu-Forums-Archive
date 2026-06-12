---
title: "Autologin not working in LXDE"
date: 2012-01-29
forum: Desktop Environments
---

### Post by Lars Noodén on 2012-01-29
I've got LXDE via Lubuntu and am trying to set autologin.  I've uncommented the line in [font=Courier New]/etc/lxdm/default.conf[/font] and added my account name, but nothing happens.

```

[base]
## uncomment and set autologin username to enable autologin
autologin=lars

```

What else needs to be changed for autologin to take effect?  This is in Precise Pangolin.

---

### Post by 2F4U on 2012-01-29
Did you also try this?

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LXDM)

---

### Post by Lars Noodén on 2012-01-29
Yes. I followed those instructions.  I have been using Precise and will try rolling back to Oneiric to see if that helps.

---

### Post by Lars Noodén on 2012-02-06
A recent upgrade seems to have gotten things working with no further changes needed on my part.

---


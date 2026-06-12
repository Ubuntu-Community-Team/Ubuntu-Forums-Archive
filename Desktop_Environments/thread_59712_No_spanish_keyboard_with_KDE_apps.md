---
title: "No spanish keyboard with KDE apps"
date: 2005-08-25
forum: Desktop Environments
---

### Post by elgaelo on 2005-08-25
Hello everybody!

I have a certainly easy problem to resolve but actually I don't know how. First, I installed Ubuntu with no problems at all. The keyboard layout was ok and I could type 'ñ' and accents. Sometimes later I installed de KDE package including the ES fonts but no special characters appears.

The key thing is that even opening a Terminal (from GNOME) I have the good keyboard config... How do I change the keyboard config? Obviously I checked the KDE Control Centrel and the keyboard layout is set to Spanish!!

Thanks a lot!!

---

### Post by biquillo on 2005-08-25
maybe there is a problem with your locales.
try to reconfigure them typing in your console "sudo dpkg-reconfigure locales" and setting up spanish as your default locale

---

### Post by jeremy on 2005-08-25
I don't know if this is any help to you, but I am using a spanish keyboard in Kubuntu without any problems.
Before I installed Kubuntu, I used Ubuntu and did apt-get kubuntu-desktop and used my keyboard in that KDE too, again no problems.

---

### Post by kairu0 on 2005-11-05
I have the same problem (ñ but no é á etc. in kubuntu.)

How can we track this down? Is this an xkb layout or a kde thing?

---


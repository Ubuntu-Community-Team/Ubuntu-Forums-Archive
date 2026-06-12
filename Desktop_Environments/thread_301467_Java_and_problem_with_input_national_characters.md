---
title: "Java and problem with input national characters"
date: 2006-11-17
forum: Desktop Environments
---

### Post by maximk on 2006-11-17
Today, I started NetBeans as usually and was unable to enter russian text in IDE. Neither in java source editor nor any other text input fields.

While keyboard layout is English - all is ok, but when I switch it to russian - keystrokes produce strange characters in any text input fields. Those characters appear to be Arabian or something-like.

I guess it's not Sun jre's bug, my test UI application started under GNU's gij acts alike.

It is seemed that some of low-level libraries JVM depends on are misconfigured or broken.

Some additional info:
Ubuntu 6.10,
NetBeans 5.0 (the same with NetBeans 5.5)
Sun JDK 1.5.0_09 (installed from Sun's bin-package)
LANG=ru_RU.UTF-8

Nothing had been changed in configuration since all did worked.

---

### Post by maximk on 2006-11-24
I don't know exatcly why that happened, but solution I've found is easy:

I just created symbolic link /usr/share/X11/locale/ru_RU.UTF-8 pointing to /usr/share/X11/locale/en_US.UTF-8. The thing is locale en_US.UTF-8 just works!

Nether the less, file /usr/share/X11/compose.dir contains line ru_RU.UTF-8 references en_US.UTF-8/Compose file.

It would be great, if someone from "xorg" package maintainers comment that.

---


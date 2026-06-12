---
title: "Change Gnome default theme globally"
date: 2008-04-27
forum: Desktop Environments
---

### Post by mattcen on 2008-04-27
Hi everyone,

I have just installed Edubuntu Server Hardy (or more correctly Ubuntu Hardy Alternate CD and then Edubuntu Addons) and don't really like all the colours used in the icons.
I have changed the theme from EdubuntuColors to EdubuntuPlain, and I much prefer this.
My question is this: How can I make EdubuntuPlain the global default for new users? I am not sure where the default gnome settings are stored. I considered trying to copy changes to **/etc/skel/** but feel there should be a better way. Any ideas?
Thanks in advance

Regards,
Mattcen

---

### Post by mattcen on 2008-05-08
*bump*

Any ideas?

---

### Post by inportb on 2008-05-08
> **mattcen said:**
> I considered trying to copy changes to **/etc/skel/** but feel there should be a better way.

I think you have the right idea. You can make the process easier by giving yourself superuser rights, making $HOME point to /etc/skel, then making the changes in the same terminal session.

---


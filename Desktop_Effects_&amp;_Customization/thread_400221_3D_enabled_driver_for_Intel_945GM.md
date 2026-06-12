---
title: "3D enabled driver for Intel 945GM"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-04-03
Trying to install Beryl on a HP Pavilion dv1000 laptop using this [guide]("http://doc.gwos.org/index.php/BerylOnEdgy").
The laptop has an Intel 945GM graphics card and /etc/X11/xorg.conf says it's using the "vesa" driver.
However, Beryl doesn't work and I think the problem is that "vesa" is not the appropriate 3D enabled driver for this card.
Can anybody help me locate the correct driver?

Thanks
Paul

---

### Post by PaulFXH on 2007-04-03
I've actually solved this by simply substituting "vesa" with "i810" in /etc/X11/xorg.conf.
Talk about simple.

---


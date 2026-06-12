---
title: "Jaunty Font Resolution problem"
date: 2010-01-20
forum: Desktop Environments
---

### Post by ayacopino on 2010-01-20
I have deployed a LTSP Ubuntu Server.
I have problem with some terminals, the font resolution appears as 72x72dpi instead of 96dpi.
In the gnome preferences the font resolution is configured for 96dpi but doing this:

xdpyinfo | grep dimension
  dimensions:    800x600 pixels (283x212 millimeters)
xdpyinfo | grep resolution
  resolution:    72x72 dots per inch

I get 72x72 instead of 96dpi.

How can i force 96 dpi to all users?.

The Xorg.conf file is blank, and i have differents monitor models.

Thanks a lot,

Andrew.

---


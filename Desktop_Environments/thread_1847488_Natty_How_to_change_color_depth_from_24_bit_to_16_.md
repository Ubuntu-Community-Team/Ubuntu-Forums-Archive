---
title: "Natty: How to change color depth from 24 bit to 16 bit"
date: 2011-09-20
forum: Desktop Environments
---

### Post by lalop on 2011-09-20
I want to play a legacy game that requires 16 bit color depth, but the standard instructions for changing it don't seem to be working for me, since it assumes an NVIDIA graphics card while I have a  Intel® GM965 Express Chipset.  When I tried using a simpler /etc/X11/xorg.conf:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    16
EndSection
```

This was the result:

[[IMG]http://img690.imageshack.us/img690/2716/screenshot1jk.th.png[/IMG]](http://imageshack.us/photo/my-images/690/screenshot1jk.png/)

I could barely see anything and it was mostly unusable.

I'm told by a friend he also had problems with natty colors and had to switch back to lucid to do this.  Is it possible to do so with natty?  My computer is a Sony Vaio VGN-NR498E; it's information can be found at: [http://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&partNumber=VGNNR498E/W](http://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&partNumber=VGNNR498E/W)

Any help appreciated, thanks.

---


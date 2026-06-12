---
title: "Ugly Gnome: Might be hitting Bug 5150"
date: 2007-08-21
forum: Desktop Environments
---

### Post by giosue_c on 2007-08-21
So I recently re-installed after a HD failure :I  Something has gone wrong in the install.  My system looks really crappy right now.  I have some minimalistic theme and no icons show in any menus.  In general I have the same symptoms as this bug: [https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/50150)

However the fix described there doesn't work and I get the following errors:

/usr/share/gconf/schemas/aisleriot.schemas:1822: parser error : Premature end of data in tag locale line 1820
    
    ^
/usr/share/gconf/schemas/aisleriot.schemas:1822: parser error : Premature end of data in tag schema line 1589
    
    ^
/usr/share/gconf/schemas/aisleriot.schemas:1822: parser error : Premature end of data in tag schemalist line 2
    
    ^
/usr/share/gconf/schemas/aisleriot.schemas:1822: parser error : Premature end of data in tag gconfschemafile line 1
    
    ^
/usr/share/gconf/schemas/CDDB-Slave2.schemas:1: parser error : Document is empty

^
/usr/share/gconf/schemas/CDDB-Slave2.schemas:1: parser error : Start tag expected, '<' not found

^

I ran the integrity check on the CD.  It says my disk is fine so I don't understand how all those files are corrupt.  I also don't understand what is going wrong.  

Here is a screenshot of how crappy things look right now.  (Note the weird buttons for close, maximize, minimize on all windows).
[http://www.flickr.com/photo_zoom.gne?id=1193887149&size=m](http://www.flickr.com/photo_zoom.gne?id=1193887149&size=m)

Please help!  Thanks in advance.

---

### Post by giosue_c on 2007-08-21
Ok.  Tried a complete re-install.  Now even the live CD looks like this.  wtf?  How can the live CD be affected?  Anyway, same problem after re-install.  I downloaded the ISO again from another location and did a diff.  No difference between them.  Totally confused.

---


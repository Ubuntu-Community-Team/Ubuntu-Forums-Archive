---
title: "Sourceforge forcing HTTPS breaks apt-get update"
date: 2016-12-21
forum: Debian
---

### Post by Dinsdale Piranha on 2016-12-21
I have this line in my /etc/apt/sources.list file to keep SeaMonkey updated:

 	Code:
 	deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main 
However today when I attempted an apt-get update it failed outright with this showstopper:

 	Code:
 	```
E: The method driver /usr/lib/apt/methods/https could not be found.
N: Is the package apt-transport-https installed?
``` 
Commenting out the Ubuntuzilla line in sources.list allowed me to  proceed with non-Ubuntuzilla packages, however it is clear that  Sourceforge must be forcing HTTPS on connections to the Ubuntuzilla repo  for this error to occur.

As we all know, very little is gained by using HTTPS with apt because  the packages are all verified by signature. Is there some way we can  force an HTTP connection with Sourceforge? I would rather do that than  install apt-transport-https (just another package to keep updated and  potentially cause hassles).

---

### Post by howefield on 2016-12-21
Moved to the "*Debian*" forum.

---

### Post by oldos2er on 2016-12-21
Thread closed.

---


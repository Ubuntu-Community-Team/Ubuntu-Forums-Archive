---
title: "Questions about universe/multiverse repositories"
date: 2005-10-25
forum: Desktop Environments
---

### Post by unkemptwolf on 2005-10-25
Will the ones from Hoary still work, or is it gonna fry my install? On a side note, can anyone tell me how to setup the wine repository (Supposedly [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) )? The information on their website is a bit outdated, and the beta was released today and I want it!:D Thx for the help.

---

### Post by ranf on 2005-10-25
[QUOTE=unkemptwolf]On a side note, can anyone tell me how to setup the wine repository (Supposedly [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) )? The information on their website is a bit outdated, and the beta was released today and I want it!:D [/QUOTE]
I wouldn't mock around with an additional repository. Just download the 2 packages without `-dev' in their names (from breezy) and install them with:
```
sudo dpkg -i <package name>
```
libwine... first, wine... after that.

---


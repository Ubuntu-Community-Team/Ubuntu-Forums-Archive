---
title: "Text Problem - Web Browsing"
date: 2005-09-23
forum: Desktop Environments
---

### Post by Velox Letum on 2005-09-23
In all of my browsers, certain blocks of text will not show up, namely quotes on forums, PHP.net code examples, some tables, etc.. I have no idea what is going on, despite many attempts at fixing by installing character sets, which is why I'm bringing my problem here to possibly have some light shed on my situation.. This happens in all three browsers: I tested with: FireFox, Konqueror, and Opera. When I select the text and paste it into a KJots page, or into a text area, or address bar, etc. it shows up just fine. I have linked picture examples (as links, 1280x1024 resolution, about 130kb each). Selecting doesn't help as shown in the last screenshot.

System info:
Distro: Kubuntu 5.04 Hoary
Processor: Intel Pentium 4 3.00ghz
Memory: 1024mb PC-3200 ram
Graphics: Nvidia GeForce FX 5950 Ultra 256mb
Graphics driver: Nvidia proprietary

[http://www.nanoshock.net/images/linux/missingtext.jpg](http://www.nanoshock.net/images/linux/missingtext.jpg) 
[http://www.nanoshock.net/images/linux/missingtext2.jpg](http://www.nanoshock.net/images/linux/missingtext2.jpg)
[http://www.nanoshock.net/images/linux/missingtext3.jpg](http://www.nanoshock.net/images/linux/missingtext3.jpg)
[http://www.nanoshock.net/images/linux/missingtext4.jpg](http://www.nanoshock.net/images/linux/missingtext4.jpg)

---

### Post by cwaldbieser on 2005-09-23
[QUOTE=Velox Letum]In all of my browsers, certain blocks of text will not show up, namely quotes on forums, PHP.net code examples, some tables, etc.. I have no idea what is going on, despite many attempts at fixing by installing character sets, which is why I'm bringing my problem here to possibly have some light shed on my situation.. This happens in all three browsers: I tested with: FireFox, Konqueror, and Opera. When I select the text and paste it into a KJots page, or into a text area, or address bar, etc. it shows up just fine. I have linked picture examples (as links, 1280x1024 resolution, about 130kb each). Selecting doesn't help as shown in the last screenshot.

System info:
Distro: Kubuntu 5.04 Hoary
Processor: Intel Pentium 4 3.00ghz
Memory: 1024mb PC-3200 ram
Graphics: Nvidia GeForce FX 5950 Ultra 256mb
Graphics driver: Nvidia proprietary

[http://www.nanoshock.net/images/linux/missingtext.jpg](http://www.nanoshock.net/images/linux/missingtext.jpg) 
[http://www.nanoshock.net/images/linux/missingtext2.jpg](http://www.nanoshock.net/images/linux/missingtext2.jpg)
[http://www.nanoshock.net/images/linux/missingtext3.jpg](http://www.nanoshock.net/images/linux/missingtext3.jpg)
[http://www.nanoshock.net/images/linux/missingtext4.jpg](http://www.nanoshock.net/images/linux/missingtext4.jpg)[/QUOTE]

It's somewhat weird this is affecting all your browsers, but I am going to guess that your fonts are somehow set to the same color as those pre-formatted regions.

Try going into your browser preferences and fiddle with the font colors.  You may be using system font colors, which would explain the commonality across browsers.

---

### Post by Galoot on 2005-09-23
[QUOTE=cwaldbieser]It's somewhat weird this is affecting all your browsers, but I am going to guess that your fonts are somehow set to the same color as those pre-formatted regions.[/QUOTE]Selecting would still show the text, though, wouldn't it?

---

### Post by Velox Letum on 2005-09-23
It isn't the font color...because also note the text is universally small when selected, though it doesn't show up.

---


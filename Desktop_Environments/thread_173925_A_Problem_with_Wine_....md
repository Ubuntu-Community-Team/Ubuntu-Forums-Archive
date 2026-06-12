---
title: "A Problem with Wine ..."
date: 2006-05-11
forum: Desktop Environments
---

### Post by pmilin@ptt.yu on 2006-05-11
Hi!
Recently, I put IE6 to work under Ubuntu, since I have stupid bank that insist on using that browser [ for the sake of security, they say :( ]. This is a combination of the whole IE and necessary libraries and, of course, Wine. However, all other programs that I managed to use with Wine (like some dictionary and Total Commander), are not working now. I have tried to look into the script for starting IE, but no idea and, consequently, no success. Can anyone help me with this?
I have installed [http://www.tatanka.com.br/ies4linux](http://www.tatanka.com.br/ies4linux) IE6 for Linux.
This is the script:
```
#!/bin/bash
cd
WINEPREFIX="/home/pmilin/.ies4linux/ie6" wine "/home/pmilin/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE" $@
```

And this is a line for starting Webster, which have worked previously:
```
wine /windows/Program\ Files/Zane\ Publishing/MW\ Dictionary-Thesaurus/DictionaryThesaurus.EXE
```

---


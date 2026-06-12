---
title: "How to remove symbolic links?"
date: 2006-04-18
forum: Desktop Environments
---

### Post by MichaelZ on 2006-04-18
Hello,

I have defined some symbolic links that I would like to remove. The links are e.g.,

> 
ln -s /usr/local/bin/ccache /usr/local/bin/gcc
ln -s /usr/local/bin/ccache /usr/local/bin/g++
ln -s /usr/local/bin/ccache /usr/local/bin/cc
 

Thank you very much.

Best wishes,
Michael

---

### Post by 5-HT on 2006-04-18
```
sudo rm /usr/local/bin/gcc
sudo rm /usr/local/bin/g++
sudo rm /usr/local/bin/cc 
```

At the beginning of the man page, 'man ln' , there is a little synopsis of the syntax for making links (which can come in handy when one wants to remove them as well).

Hope that helps.

---

### Post by MichaelZ on 2006-04-19
[quote=5-HT]```
sudo rm /usr/local/bin/gcc
sudo rm /usr/local/bin/g++
sudo rm /usr/local/bin/cc 
``` 
At the beginning of the man page, 'man ln' , there is a little synopsis of the syntax for making links (which can come in handy when one wants to remove them as well).

Hope that helps.[/quote] 
Thank you very much for the help:).

I have had a look before of the man ln, but I am still not very experienced with  the Terminal commands (coming from Windows XP).

Best wishes,
Michael

---


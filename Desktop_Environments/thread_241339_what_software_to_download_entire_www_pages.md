---
title: "what software to download entire www pages?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by tubunu on 2006-08-22
I used to have a programme on Win that would copy the entire contents of a web page on the hard drive for offline use. You could specify how many links i.e. how deep it would go to copy it. Is there an equivalent available for Dapper? Thanks.

---

### Post by sazabi on 2006-08-22
httrack maybe

---

### Post by jordilin on 2006-08-22
Yes, wget. Take a look here:
[http://jordilin.wordpress.com/2006/08/12/howto-wget-the-best-download-manager-out-there/](http://jordilin.wordpress.com/2006/08/12/howto-wget-the-best-download-manager-out-there/)
for a little howto, I made recently.
There are plenty as well on the internet. Wget is a very powerful app to download entire web pages.

---

### Post by bluenova on 2006-08-22
The gnome GUI for wget is [gwget](http://www.gnome.org/projects/gwget/)

[Enable the Universe repository](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html#id2542172) then in a terminal write:

```
sudo apt-get install gwget
```

---

### Post by tubunu on 2006-08-22
Thanks, everyone for the tips.

Is it also possible to download www for offline viewing without the graphics (just text)? 
Lynx is perfect for graphics less viewing but can I use wget to download pages as text only?

---

### Post by jordilin on 2006-08-22
> **tubunu said:**
> Thanks, everyone for the tips.

Is it also possible to download www for offline viewing without the graphics (just text)? 
Lynx is perfect for graphics less viewing but can I use wget to download pages as text only?

You can use the **scrapbook **extension for firefox as well. It does what you say flawlessly

---


---
title: "[SOLVED] gnome-open doesn't open url"
date: 2008-12-02
forum: General Help
---

### Post by cube3x3 on 2008-12-02
Hello
I have a problem with gnome-open. It doesn't open the url. 

When i give following command:
```
gnome-open http://google.com
```

It gives following error:
```
Error showing url: Operation not supported
```

Any idea?
I have set my default browser app as 'firefox' and it runs just fine.

---

### Post by dexter on 2008-12-02
What version of gnome-open do you have? It works fine here with
```
GNOME gnome-url-show 2.24.1
```

---

### Post by cube3x3 on 2008-12-02
It the same version here also: 2.24.1

I really have no clue why this is not working. 'Operation not supported' doesn't give any clue either :(

---

### Post by fragos on 2008-12-02
Very strange. Will it work if for example the url is an html file? That should come up in your preferred browser as well. Almost sounds like a missing or corrupt library. Whatever understands the mime type and protocol application relationship is confused.

---

### Post by cube3x3 on 2008-12-02
Solved..
Some of libraries in /usr/lib/gio/modules were of 32bit instead of 64bit. My system is 64bit and i had to change those to 32bit because of firefox problem. 

Thanks for your help fragos.

---


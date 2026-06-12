---
title: "google earth imediate colse"
date: 2009-02-03
forum: General Help
---

### Post by metalmaniac248 on 2009-02-03
just installed google earth 5 in my ibex machine, when i first opened it there was no earth or stars, i found a post somewhere that said to remove .config/Google and .googleearth from my home directory i did this but then when i opened google earth it showed the earth and stars as it should but then imediately closed. I have reinstalled many times but still no luck


any ideas?

---

### Post by metalmaniac248 on 2009-02-03
sorry about this wasnt concentrating put it in the wrong catagory

---

### Post by metalmaniac248 on 2009-02-03
just installed google earth 5 in my ibex machine, when i first opened it there was no earth or stars, i found a post somewhere that said to remove .config/Google and .googleearth from my home directory i did this but then when i opened google earth it showed the earth and stars as it should but then imediately closed. I have reinstalled many times but still no luck


any ideas?

---

### Post by LowSky on 2009-02-03
how did you install google earth?

---

### Post by metalmaniac248 on 2009-02-03
downloaded the GoogleEarthLinux.bin file then

> sh GoogleEarthLinux.bin

---

### Post by taurus on 2009-02-03
Everytime an app opens and closes, try running that from a terminal so you could view the error message.

---

### Post by metalmaniac248 on 2009-02-03
```
nick@nick-desktop:~$ /home/nick/google-earth//googleearth 
Warning: Unable to create prefs directory '/home/nick/.googleearth'. File exists.
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
nick@nick-desktop:~$ 

```

thats what i get when i run it from the terminal

---

### Post by bapoumba on 2009-02-03
Moved to General Help.

---

### Post by gjoellee on 2009-02-03
People! Try find a thread like this before posting! I have already been looking at 3 similar posts already... Lets put all in one!

---

### Post by bapoumba on 2009-02-03
Done ;)
Threads merged.

---

### Post by MisterM on 2009-02-03
From [http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en]("http://www.google.com/support/forum/p/earth/thread?tid=7b1b524777b9b982&hl=en"):

> Find the libcrypto.so.0.9.8 library in the Google Earth install directory and rename it. Google Earth will then use systems libcrypto and works at least on Intrepid.

> So just to review for Ubuntu users:

>sudo mv libcrypto.so.0.9.8  libcrypto.so.0.9.8.old
>ln -s /usr/lib/libcrypto.so libcrypto.so.0.9.8

It worked for me ;)

---

### Post by webweaver on 2009-02-03
Worked for me too!  Thanks  :)

---

### Post by metalmaniac248 on 2009-02-04
yer worked for me too thanks

---

### Post by Boynas on 2009-04-06
THANKS... It worked here too.

---

### Post by Redundant Username on 2009-04-06
If Google Earth opens, shows the splash screen, and then crashes, you’re probably experiencing a common issue. Running ~/google-earth/googleearth in a terminal will show this error:
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

To fix this, browse to the folder you installed Google Earth into. By default this will be google-earth in your home folder. Find the file libcrypto.so.0.9.8 and rename it to something else, like libcrypto.so.0.9.8.bak. Google Earth should now start correctly.

---


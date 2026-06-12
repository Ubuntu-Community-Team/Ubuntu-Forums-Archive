---
title: "[SOLVED] Ubuntu 8.04 LTS + 32-bit + Flash 10 = Fail..."
date: 2008-12-05
forum: General Help
---

### Post by viper474 on 2008-12-05
I have been trying different methods of trying to install a working form of Flash player 10.  If any of you out there are successfully using Flash Player 10 on a 32-bit version of Ubuntu 8.04, let me know how you got it to work.  If you don't match that description then your input doesn't matter in this instance, sorry...):P

---

### Post by Washer on 2008-12-06
well I'm using flash 10 64 bit, but fwiw i got a .so from one of the download.com sites & put it in the .mozilla/plugin folder

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by zvacet on 2008-12-06
```
gksudo gedit /etc/apt/sources.list
```

and add partner repo like this

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

save ans close file.

```
sudo apt-get update
```

Go to the synaptic and type in search box **adobe-flashplugin** and when you find package just install it.

---

### Post by glotz on 2008-12-06
flash == fail

---

### Post by viper474 on 2008-12-06
> **zvacet said:**
> ```
gksudo gedit /etc/apt/sources.list
```

and add partner repo like this

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

save ans close file.

```
sudo apt-get update
```

Go to the synaptic and type in search box **adobe-flashplugin** and when you find package just install it.

You are a life-saver and the only helpful person on this thread.

[QUOTE=glotz]
flash == fail
[/QUOTE]

Oops my bad...let me fix that:
fail = ( Ubuntu 8.04 LTS + 32-bit + Flash Player 10 );

---

### Post by zvacet on 2008-12-06
I just described a way I installed flash on 32-bit Hardy and I never notice any problem.Sorry if you have different expirience.

---

### Post by viper474 on 2008-12-06
> **zvacet said:**
> I just described a way I installed flash on 32-bit Hardy and I never notice any problem.Sorry if you have different expirience.

No, no, your method worked.  I was being serious in the fact that it was helpful and worked.  The Adobe site kept wanting me to download a file that just didn't seem to be working correctly.  Thanks for helping me solve my issue.

---

### Post by billgoldberg on 2008-12-15
The version on the adobe site works, but it could be that you'll have to do this in a terminal (one line at the time guys)

```
sudo ln -s /usr/lib/libssl3.so.1d /usr/lib/libssl3.so
sudo ln -s /usr/lib/libnss3.so.1d /usr/lib/libnss3.so
sudo ln -s /usr/lib/libnspr4.so.0d /usr/lib/libnspr4.so
sudo ln -s /usr/lib/libsmime3.so.1d /usr/lib/libsmime3.so
sudo ln -s /usr/lib/libplds4.so.0d /usr/lib/libplds4.so
sudo ln -s /usr/lib/libplc4.so.0d /usr/lib/libplc4.so
```

for it to work.

---


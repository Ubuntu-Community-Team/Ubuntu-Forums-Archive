---
title: "can not uninstall google earth 5"
date: 2009-02-11
forum: Desktop Environments
---

### Post by andrea000 on 2009-02-11
:(  I have installed google earth 5 and it will not start up.i have tried to 
uninstall it but it failed my question is how do i force it to uninstall?

Thank you all

XOXOXOXO

---

### Post by utnubuuser on 2009-02-11
the matrix has you...

---

### Post by xeddog on 2009-02-12
I have the same problem with Google Earth V5.  Installed it and when I try to run it it just vanishes about the time it opens the Tip of the Day.  

Anyway, I'm not sure how you went about uninstalling it, but this is how I did it:

cd ~/.loki/installed/bin/Linux/x86

In that directory will be a file called "uninstall"

code:  ./uninstall -l

That will list all installed products.  I suspect that google-earth will be the only one listed.  

Then just code:  ./uninstall google-earth

Hope that helps.

xeddog

---

### Post by bcooperb on 2009-02-12
Same thing with me, Looks like it is opening, and then closes. 

Dell XPS M1730 - NVIDIA v177

most everything else seems to work at the moment.

---

### Post by darkhole on 2009-02-18
> **andrea000 said:**
> :(  I have installed google earth 5 and it will not start up.i have tried to 
uninstall it but it failed my question is how do i force it to uninstall?

Thank you all

XOXOXOXO
The answer to uninstall Google Earth 5 installed using the .bin file like sudo:
[http://ubuntuforums.org/showpost.php?p=6753733&postcount=10](http://ubuntuforums.org/showpost.php?p=6753733&postcount=10)

---

### Post by binbash on 2009-02-18
you have to rename libcrypto.so.0.9.8 inside the google-earth folder to anything you want.Then it will work

---

### Post by adonet on 2009-03-01
Doesn't work for me on Intrepid Ibex. I renamed libssl.so.0.9.8 into something else, but QE 5.0 keeps crashing on startup

from terminal I read:

Warning: Unable to create prefs directory '/home/adolfse/.googleearth'. File already excists.
./googleearth-bin: relocation error: /usr/lib/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference

---

### Post by Channon on 2009-03-14
in the terminal, navigate to the installation directory:

```
cd google-earth
```

there is an uninstall command in this directory.  To run it, type:

```
./uninstall
```

that should remove everything that google installed.  You may have to manually remove the directory and any files which were modified after installation.

---


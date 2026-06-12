---
title: "Citrix ICA Client problems"
date: 2007-02-28
forum: Desktop Environments
---

### Post by linedpaper on 2007-02-28
I just went through the install for the Citrix ICA client.  I installed version 9.0 as that's what I need to use for my company.  Everything seemed to go fine, yet when I login to the web interface and click the 95% Desktop link nothing happens.  It doesn't give me the option to "Open With" or anything.  I've tried in both Mozilla and Firefox.  Any ideas?

---

### Post by kygil on 2007-03-06
I need help installing citrix onto ubuntu 6.10.
Here's the steps I've done so far:

downloaded v10.0 from citrix
gunzip <file>.tar.gz
tar -xvf <file>.tar
./setupwfc
finished install and closed
opened firefox & logged into citrix
clicked on link where it asked to "open with"
I selected this location: ....../ICAClient/linuxx86/wfica.sh
The small download box opens up but nothing else happens and the application doesn't load.

I'm new to linux and any help would be greatly appreciated.
Thanks

---

### Post by pt78 on 2007-03-20
Try running it like this (you may need to modify paths according your setup) :
```
/usr/lib/ICAClient/wfica.sh ~/Desktop/launch.ica
```

If you experience font problem, try running ```
xset fp rehash
```

Also, you must copy your certificate(s) to ICAclient /keystore/cacerts before connecting.

---

### Post by redevil34 on 2007-04-28
> **pt78 said:**
> Try running it like this (you may need to modify paths according your setup) :
```
/usr/lib/ICAClient/wfica.sh ~/Desktop/launch.ica
```

If you experience font problem, try running ```
xset fp rehash
```

Also, you must copy your certificate(s) to ICAclient /keystore/cacerts before connecting.

I ran 
```
/usr/lib/ICAClient/wfica.sh ~/Desktop/launch.ica
```

and got "/usr/lib/ICAClient/wfica: error while loading shared libraries: libXaw.so.6: cannot open shared object file: No such file or directory"

Did some more searching and found this 

```
sudo apt-get install libxaw6 libmotif3
```

I think I might be missing something though, but I tried 
```
/usr/lib/ICAClient/wfica.sh ~/Desktop/launch.ica
```

I got:
"An error occured. The error code is 10 (E_CANNOT_READ_INI_FILE)
Please refer to the documentation.
An error occured. The error code is 12 (E_MISSING_INI_ENTRY)
Please refer to the documentation."

---


---
title: "Can't enable desktop effects?"
date: 2009-05-08
forum: General Help
---

### Post by cptrohn on 2009-05-08
hmmm...

I didn't have this problem in intrepid... but when I went to turn on the desktop effects it went to a ```
searching for drivers
``` window for just a little bit and then opened up an error message saying ```
desktop effects could not be enabled
```  have not ran into this problem at all before... what could be causing this?

SOLVED

---

### Post by Yellow Pasque on 2009-05-08
What graphics card do you have? If you're unsure:
```
lspci | grep VGA
```
What driver are you using and is it loading correctly? Output of these commands might be useful:
```
cat /var/log/Xorg.0.log
LIBGL_DEBUG=verbose glxinfo
compiz --replace
```

---

### Post by cptrohn on 2009-05-08
> **Temüjin said:**
> What graphics card do you have? If you're unsure:
```
lspci | grep VGA
```
What driver are you using and is it loading correctly? Output of these commands might be useful:
```
cat /var/log/Xorg.0.log
LIBGL_DEBUG=verbose glxinfo
compiz --replace
```

well the graphics card comes back as an Intel mobile GM965/GL960 Integrated graphics controller (rev 030


boy there was a WHOLE lot of code that came back with those first 2 commands.... what would I be looking for there?

---

### Post by cptrohn on 2009-05-08
I do get back a ```
Checking for XLG: not present
xset can't reveal the location of the logfile. Using fallback /var/log/Xorg.0.log
Blacklisted PCIID '8086: 2a02' found
aborting and using fallback: /usr/bin/metacity
```

ran I ran the ```
compiz --replace
``` command

---

### Post by Yellow Pasque on 2009-05-08
Ok, that card was blacklisted by default. See this for overriding the blacklist:
[http://ubuntuforums.org/showpost.php?p=7129915&postcount=8](http://ubuntuforums.org/showpost.php?p=7129915&postcount=8)

---

### Post by cptrohn on 2009-05-08
Hmm I when I ran the command to bypass the blacklist I got back an error that says```
/home/user/config/compiz/compiz-manager: No such file or directory
```

And I installed compiz manager from synaptic and compiz icon before I even went to enable th desktop effects....


Nevermind, I know what I did wrong... it worked and desktop effects are running fine!

Thanks for the help!  Very much appreciated!

---


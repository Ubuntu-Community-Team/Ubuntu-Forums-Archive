---
title: "Cannot install 8.10 on my dell"
date: 2009-02-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Brzhk on 2009-02-13
Hello there,

I tried several times to install ubuntu on my new dell studio 15 and i'm always stuck in the middle of the process: i got I/O errors. The disc seems not to be read correctly.
Of course i checked the disc after burning and with the embedded tool.

any ideas? did anyone had a similar problem ?

the method i found on ubuntu-fr.org  to set up ubuntu with an usb 
key and the network wouldn't work as the key isn't recognized as bootable.

I got the centrino2 version of the laptop, if that might help.

---

### Post by JECHO on 2009-02-13
> **Brzhk said:**
> Hello there,

I tried several times to install ubuntu on my new dell studio 15 and i'm always stuck in the middle of the process: i got I/O errors. The disc seems not to be read correctly.
Of course i checked the disc after burning and with the embedded tool.

any ideas? did anyone had a similar problem ?

the method i found on ubuntu-fr.org  to set up ubuntu with an usb 
key and the network wouldn't work as the key isn't recognized as bootable.

I got the centrino2 version of the laptop, if that might help.

I have had the same problem... fortunatly there are two possible solutions:

1. Try installing the Latest release of Ubuntu 9.04. (that worked for me)
2. Get the Dell Factory OEM Release of Ubuntu 8.10 from here (its custom built to be compatible with all Dell models notebooks): [http://linux.dell.com/wiki/index.php/Ubuntu_8.10#Dell_OS_Factory_Recovery_8.10_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.10#Dell_OS_Factory_Recovery_8.10_DVD_ISO)

---

### Post by Brzhk on 2009-02-13
THAT IS JUST FANTASTIC ! 

Thank you very much, i was getting mad with opensuse...
=)

---

### Post by JECHO on 2009-02-13
> **Brzhk said:**
> THAT IS JUST FANTASTIC ! 

Thank you very much, i was getting mad with opensuse...
=)


You're welcome! Hopefully you get it working!  I used to use opensuse but a few years ago switched to ubuntu and haven't found anything better :)

---

### Post by Brzhk on 2009-02-14
sadly, it didn't work:
after i configure the first account  (and keyboard, time and stuff) the screens goes completely wrong and looks like a strange colored patchwork... :'(

edit: i suscribed to dell's mailing lists hoping to get an answer abt that, if they have a workaround i'll post it.

---

### Post by Brzhk on 2009-02-14
ok, live cd then installation just worked fine with an USB Key made from dell version of ubuntu 8.10!

---

### Post by superm1 on 2009-02-14
> **Brzhk said:**
> sadly, it didn't work:
after i configure the first account  (and keyboard, time and stuff) the screens goes completely wrong and looks like a strange colored patchwork... :'(

edit: i suscribed to dell's mailing lists hoping to get an answer abt that, if they have a workaround i'll post it.
Is this with AMD graphics by chance?

---

### Post by Brzhk on 2009-02-14
yes, HD34xx. i've setup the fglrx then, but i had to do it the apt way - the driver manager didn't work when i wanted to activate the proprietary driver.


anything i could do to help?

---

### Post by superm1 on 2009-02-14
> **Brzhk said:**
> yes, HD34xx. i've setup the fglrx then, but i had to do it the apt way - the driver manager didn't work when i wanted to activate the proprietary driver.


anything i could do to help?
There appears to be a bug in the AMD graphics driver when using it with an OEM installation.  There isn't any opened bug for it yet though.

---

### Post by coolbeans777 on 2009-02-15
When you said I/O issues, did you mean that your computer spontaneously crashed at about 94% into installation, because the same thing happened to mine. I guessed it has to do with dells having awful cooling, so i turned of my computer and unplugged it for about 10 minutes. Then when I turned it back on i put a fan blowing at the air vent. Surprisingly, this actually worked and thats how im using linux now. I also found out that dvds are a lot better for installation.

---

### Post by superm1 on 2009-02-17
> **superm1 said:**
> There appears to be a bug in the AMD graphics driver when using it with an OEM installation.  There isn't any opened bug for it yet though.
This issue with AMD graphics has been addressed in the latest image.  Please download it again from the website.

Here is the bug that ended up causing it:
[https://bugs.edge.launchpad.net/dell/+bug/330188](https://bugs.edge.launchpad.net/dell/+bug/330188)

---


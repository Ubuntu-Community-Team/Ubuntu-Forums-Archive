---
title: "Debian install hangs"
date: 2008-02-22
forum: Debian
---

### Post by igknighted on 2008-02-22
Installing Debian Lenny from the weekly netinstall CD, the installer has hung at "configuring ssl-cert" and will not budge.  Anything I can do to recover or do I need to start over?

---

### Post by Fred_E _krugar on 2008-02-22
Which comp in your signature are you using??

---

### Post by igknighted on 2008-02-22
> **Fred_E _krugar said:**
> Which comp in your signature are you using??

laptop

---

### Post by kerry_s on 2008-02-22
you should grab the etch and then upgrade that to lenny. lenny is moving really fast right now, updates almost daily.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

all you have to do is change were it says etch to lenny and "apt-get update" "apt-get dist-upgrade"

i use both etch and lenny repos, cause i want the kernel from etch, which works best on my rig.

here's my sources.list

```
deb http://ftp.debian.org/debian/ etch main contrib non-free  
deb http://ftp.debian.org/debian/ lenny main contrib non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

```

---

### Post by dw79 on 2008-02-24
I am experiencing the same problem here trying to install from debian-testing-amd64-netinst.iso

I don't think that using etch to then upgrade to lenny is possible for me, since I need SATA Raid support (Intel ICH9R) from the moment of partitioning onwards.

Any further suggestions?

---

### Post by FuturePilot on 2008-02-24
I ran into this same problem :(

---

### Post by dw79 on 2008-02-24
after a little bit of searching I found the bug report relating to this issue, at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465279](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465279) - the short answer is it's fixed and the fix is in ssl-cert 1.0.16 which is in the unstable/sid branch or can can be found at ftp.debian.org/debian/pool/main/s/ssl-cert/

on the other hand, if you just want a way round the issue so you can finish your installation, then here is how i got mine to complete:

At the point that it is hung, switch to another terminal to find the process id that has hung, and the name of the temporary file that it's reading it's configuration from.
e.g.
```
# ps
.
.
[COLOR="Blue"]25289 [/COLOR]root  1836 S   openssl req -config [COLOR="Blue"]/tmp/tmp.NAYCo25287[/COLOR] -new -x509 ...
```

You will then need to use nano to edit the tmp file:
```
# nano /target/tmp/tmp.NAYCo25287
```

in this file you will see a line saying
```
RANDFILE = $ENV::RANDFILE
```
change this to
```
RANDFILE = /dev/urandom
```
save, and exit.
now to manually run openssl:
```
# chroot /target
# openssl req -config [COLOR="Blue"]/tmp/tmp.NAYCo25287[/COLOR] -new -x509 -days 3650 -nodes -out /etc/ssl/certs/ssl-cert-snakeoil.pem -keyout /etc/ssl/private/ssl-cert-snakeoil.key
Generating a 1024 bit RSA private key
................................................++++++.......++++++
writing new private key to '/etc/ssl/private/ssl-cert-snakeoil.key'
-----

```

finally, terminate the hung process
```
# kill [COLOR="Blue"]25289[/COLOR]
```
at which point your installation will resume.
When it reports that some packages failed to install, simply re-run the package installation option from the installer which will finish configuring any packages that were dependent on ssl-cert.

---

### Post by sonichedgehog on 2008-02-24
Hi, new to forum, my problem as we speak is with Debian Lenny I386, before I give up & go back to etch... 

thanks FuturePilot for the advice, but, as I do not yet have an OS on the box I am building, how would I go about opening another terminal?-Phil

---

### Post by sonichedgehog on 2008-02-24
sorry I mean thanks dw79..!

---

### Post by dw79 on 2008-02-24
> **sonichedgehog said:**
> ..., as I do not yet have an OS on the box I am building, how would I go about opening another terminal?-Phil

When you're running the debian installer (in text mode - not sure about gui installer) you can press Alt+F2/F3 to switch to a different virtual terminal, then Alt+F1 to go back to the installer. Also on Alt+F4 you can see in more detail what the installer is doing.

---

### Post by sonichedgehog on 2008-02-25
Hi dw79, that advice was probably the most effective fix I've ever used. I prefer installing from the testing image and have used that code twice now. Many thanks- Phil

---

### Post by atrus123 on 2008-02-27
> **dw79 said:**
> after a little bit of searching I found the bug report relating to this issue, at [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465279](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=465279) - the short answer is it's fixed and the fix is in ssl-cert 1.0.16 which is in the unstable/sid branch or can can be found at ftp.debian.org/debian/pool/main/s/ssl-cert/

on the other hand, if you just want a way round the issue so you can finish your installation, then here is how i got mine to complete:

At the point that it is hung, switch to another terminal to find the process id that has hung, and the name of the temporary file that it's reading it's configuration from.
e.g.
```
# ps
.
.
[COLOR="Blue"]25289 [/COLOR]root  1836 S   openssl req -config [COLOR="Blue"]/tmp/tmp.NAYCo25287[/COLOR] -new -x509 ...
```

You will then need to use nano to edit the tmp file:
```
# nano /target/tmp/tmp.NAYCo25287
```

in this file you will see a line saying
```
RANDFILE = $ENV::RANDFILE
```
change this to
```
RANDFILE = /dev/urandom
```
save, and exit.
now to manually run openssl:
```
# chroot /target
# openssl req -config [COLOR="Blue"]/tmp/tmp.NAYCo25287[/COLOR] -new -x509 -days 3650 -nodes -out /etc/ssl/certs/ssl-cert-snakeoil.pem -keyout /etc/ssl/private/ssl-cert-snakeoil.key
Generating a 1024 bit RSA private key
................................................++++++.......++++++
writing new private key to '/etc/ssl/private/ssl-cert-snakeoil.key'
-----

```

finally, terminate the hung process
```
# kill [COLOR="Blue"]25289[/COLOR]
```
at which point your installation will resume.
When it reports that some packages failed to install, simply re-run the package installation option from the installer which will finish configuring any packages that were dependent on ssl-cert.

Thanks for posting this.  It took care of the problem for me.

---


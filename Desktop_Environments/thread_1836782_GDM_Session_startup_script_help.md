---
title: "GDM Session startup script help"
date: 2011-08-31
forum: Desktop Environments
---

### Post by atomicfire on 2011-08-31
Recently due to the DigiNotar SSL issue I want to setup a startup script for GDM session to automatically add the CRL to the Firefox CRL list.

I already have crlutil installed and working; I have verified that I was able to import the CRL and have Firefox recognize it. This works when done by hand:
```
crlutil -B -I -i /path/to/crl.file -d ~/.mozilla/firefox/profile.default
```

The type of environment we are working with is a diskless "smart terminal" netboot environment. One server (the "image server") takes care of serving the read-only filesystem for Ubuntu - the other server (the "home server") serves a rw NFS mount for the /home/username filesystem. We are running 10.10 Maverick with Firefox 6 PPA.

To simplify applying the CRL, I want to modify a GDM startup script to import the CRL into the user's mozilla profile automatically. Something like this (pulled from memory so it might not be syntactically 100% correct).
```
for i in `grep Path /home/$USER/.mozilla/firefox/profiles.ini`; do crlutil -B -I -i /path/to/crl.file -d /home/$USER/.mozilla/firefox/$i/; done
```

Since I want it to run post-login but before the user interacts with the desktop, I figure the best place to put it in is in the GDM presession init script:
```
/etc/gdm/presession/Default
```

I know the $USER environment variable is correct in the init file since I can do debug statements like:
```
echo $USER > /tmp/user.txt
```

However, completely 100% refuses to run the bit of code to insert the CRL into the mozilla keystore. Specifically, when this particular snippit is in the Default init file, it doesn't do anything at all:
```
for i in `grep Path /home/$USER/.mozilla/firefox/profiles.ini`; do crlutil -B -I -i /path/to/crl.file -d /home/$USER/.mozilla/firefox/$i/; done
```

I've tried to use 
```
2&>1 > /tmp/error.txt
```

However, this doesn't output anything (file is blank). If anyone has any insight into why this isn't working, or has any other creative ideas on how to force this script to run on login to add the CRL to FireFox, I'm be very interested in hearing and I do appreciate any help anyone can provide. 

Thanks!

---


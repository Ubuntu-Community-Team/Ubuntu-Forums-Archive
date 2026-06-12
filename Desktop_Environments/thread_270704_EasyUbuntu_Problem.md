---
title: "EasyUbuntu Problem"
date: 2006-10-03
forum: Desktop Environments
---

### Post by jheath on 2006-10-03
Hi,

I have a fresh install of Ubuntu 6 and I am trying to attempt to install EasyUbuntu for MP3 and WMV file support. However I recieve the following when I attempt to try and add codec support in the interface. After this error appears it seems to install everything in the background. But this error still worries me. Has anybody had or seen it before?

```
W: GPG error: http://easyubuntu.cafuego.net main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
```

Thanks for any support in advance! :p

---

### Post by ZipoTe on 2006-10-03
Uff... easyubuntu didn't work for me for Breezy and of course Dapper. I always use automatix.


[http://getautomatix.com/](http://getautomatix.com/)

It installs tons of software (sure you won't need it all :P, but you can check what do you want to install, of course) very easy, just follow the instructions.

---

### Post by jheath on 2006-10-04
ZipoTe,

Thanks for the reference to Automatix. Installed that, and it installed its own PGP keys. :p Joy!

And it does indeed have a wide selection of software and it fixed my NVIDIA graphics issues too!

Thanks so much!

---

### Post by ty_oftrans on 2006-10-07
ZipoTe,

Thank you very much for the link to Automatix. I was having the same problems like jheath and your link saved me from a terrible headache. Automatix is just fantastic!

Many thanks, again!

Ty

---

### Post by lemonsCC on 2006-10-07
use these commands

```
# gpg --keyserver subkeys.pgp.net --recv [COLOR="Red"]KEY[/COLOR]
# gpg --export --armor [COLOR="Red"]KEY[/COLOR] | sudo apt-key add -
```

where key is that number/letter combo at the end of the error

---


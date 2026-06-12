---
title: "Synaptics error message, any ideas?"
date: 2009-04-13
forum: General Help
---

### Post by WOOHOOHOO on 2009-04-13
Hi,

I was just having a browse of Synaptics package manager. It opens fine. I clicked Reload, and it dowloads package info, then i get this error message:

"W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 423A2125D782A00F"

What is it and is it going to ruin my day? :)

Thanks

---

### Post by RuleMaker on 2009-04-13
Dont worry about that, you just need to add the the GPG key from launchpad, or even easier let [this]("http://ubuntuforums.org/showthread.php?t=1056099") script do it for you.

---

### Post by WOOHOOHOO on 2009-04-13
thats cool, thanks. so will it ever go away?

---

### Post by RuleMaker on 2009-04-13
Of course it will :)
It's not an error, just a warning that you dont have that key. Not a problem at all but you can solve it to stop that annoying popup.

---

### Post by zvacet on 2009-04-13
@ **WOOHOOHOO**

You can add key by typing in terminal

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 423A2125D782A00F
gpg --export --armor 423A2125D782A00F | sudo apt-key add -
```

---

### Post by WOOHOOHOO on 2009-04-13
it didnt like the above code. I tried it exact as below, it said permissions denied. So i put sudo at the end. This came out:

jamie@jamie-laptop:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 423A2125D782A00F
gpg: WARNING: unsafe ownership on configuration file `/home/jamie/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
jamie@jamie-laptop:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 423A2125D782A00F
gpg: WARNING: unsafe ownership on configuration file `/home/jamie/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


good or bad or am i dumb? cheers Jamie

---

### Post by RaveJunkie on 2009-05-19
zvacet's post fixed my problem  THANK YOU SIR

---


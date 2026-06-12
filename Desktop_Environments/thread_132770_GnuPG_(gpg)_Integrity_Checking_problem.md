---
title: "GnuPG (gpg) Integrity Checking problem"
date: 2006-02-18
forum: Desktop Environments
---

### Post by jchau on 2006-02-18
I installed gpg a while ago through Synaptic. Can someone tell me if I can trust the integrity of this install? What sort of security is there? Should I try to verify the gpg install another way?

Another thing. I downloaded gpg for my Windows installation too and I downloaded the signature for my gpg download.  I figured the easiest way to verify that my downloaded copy of gnupg can be trusted is to use my Ubuntu gpg install to run `gpg --verify gnupg-w32cli-1.4.2.1.exe.sig`.  However, when I run this, I realize that I don't have the public signing key on my computer.  I know I can get the key from the gnupg website, but I want to get the public key from a trusted source.  Can someone tell me where I can find a copy of the public key? I know I can find a copy of the key at [http://www.gnupg.org/(en)/signature_key.html](http://www.gnupg.org/(en)/signature_key.html) but I want to get it from a trusted source (preferably in a place already on my computer).

Can someone tell me where to find the GnuPG Public key on my computer?  

Please note, that since I installed GnuPG through Synaptic (not installed from source), I cannot find the key in doc/samplekeys.asc .

Thanks in advance for the help.

---

### Post by cwaldbieser on 2006-02-19
[QUOTE=jchau]I installed gpg a while ago through Synaptic. Can someone tell me if I can trust the integrity of this install? What sort of security is there? Should I try to verify the gpg install another way?

Another thing. I downloaded gpg for my Windows installation too and I downloaded the signature for my gpg download.  I figured the easiest way to verify that my downloaded copy of gnupg can be trusted is to use my Ubuntu gpg install to run `gpg --verify gnupg-w32cli-1.4.2.1.exe.sig`.  However, when I run this, I realize that I don't have the public signing key on my computer.  I know I can get the key from the gnupg website, but I want to get the public key from a trusted source.  Can someone tell me where I can find a copy of the public key? I know I can find a copy of the key at [http://www.gnupg.org/(en)/signature_key.html](http://www.gnupg.org/(en)/signature_key.html) but I want to get it from a trusted source (preferably in a place already on my computer).

Can someone tell me where to find the GnuPG Public key on my computer?  

Please note, that since I installed GnuPG through Synaptic (not installed from source), I cannot find the key in doc/samplekeys.asc .

Thanks in advance for the help.[/QUOTE]

Synaptic and apt-get automatically check the MD5 sums of the packages they download.  You can lookup the hash with:
```

$ apt-cache show <package-name> | grep MD5sum

```
The actual package files are downloaded to /var/cache/apt/archives.

---

### Post by jchau on 2006-02-21
Well, thanks for that. I didn't know that.  But chances are the MD5 sum is downloaded from the same site as my copy of gnupg for linux (Please correct me if I'm wrong here).  If my connection was comprimised (eg. man in the middle attack), using the MD5 sum from my possibly compromised connection to check my download from my possibly compromised gnupg download doesn't really reassure me.  Are there any other measures to ensure that I got the real gnupg? 

I was look for something like two independent sources giving me the same md5 sum and the md5 sum matching.  But I'm pretty confident that the copy of gnupg I already have installed is a good copy (just want to be sure though).  

I'm really looking for a reliable copy of the gpg public key so I can check their signature.  I downloaded a copy of gnupg for my windows install & I would like to verify it before I install it.  I could just download the public key from the gpg website, but I want something to compare that key against (maybe a copy of the key already on my computer, maybe a copy from a few other reliable source online, etc.). 

Thanks again!

---


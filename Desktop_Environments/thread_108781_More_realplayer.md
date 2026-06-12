---
title: "More realplayer?"
date: 2005-12-27
forum: Desktop Environments
---

### Post by harisund on 2005-12-27
Is there any particular way to install realplayer so that it automatically works? 

I looked at the wiki and people's complaints in this forum after doing what was said in the wiki. 

Does EasyUbuntu or Automatix install RealPlayer? 

Thanks !

I want to listen to npr.org and bbc and cnn..

---

### Post by Perfect Storm on 2005-12-27
add this to your souce list

## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

```

sudo apt-get update
sudo apt-get install realplay

```

Only works if you're using i386 arch

---

### Post by harisund on 2005-12-27
Hmm..didn't quite work for me.. I used the .bin file directly from
[http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner](http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner)
Thanks anyway..

---


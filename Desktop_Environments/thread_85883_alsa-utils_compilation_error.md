---
title: "alsa-utils compilation error"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Navyblue on 2005-11-03
Hi guys,

I am trying to compile alsa-utils that i downloaded from [www.alsa-project.org](www.alsa-project.org). Because for some reason alsaconf is removed from alsa-utils in Ubuntu. And I need it to detect my ISA sound card. Please suggest if you have better ways of to do this.

Anyway, during the "make" command, I get this:

```

Making all in include
make[1]: Entering directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/include'
make  all-am
make[2]: Entering directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/include'
make[2]: Leaving directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/include'
make[1]: Leaving directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/include'
Making all in alsactl
make[1]: Entering directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/alsaconf'
Making all in po
make[2]: Entering directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/navyblue/Desktop/alsa-utils-1.0.9a/alsaconf'
make: *** [all-recursive] Error 1

```

What is wrong here?

Thanks in advance. :)

---

### Post by Navyblue on 2005-11-04
Just for the reference of those who have proble doing this. I have gone the easy way by installing it from the Debian unstable repository and it works. :)

---


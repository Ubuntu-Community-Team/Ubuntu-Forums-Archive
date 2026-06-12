---
title: "Java update 5 not working"
date: 2005-10-27
forum: Desktop Environments
---

### Post by anarhistu on 2005-10-27
Ok, so I try to install java update 5:

I did this:
download from sun jdk-1_5_0_05-linux-amd64.bin

Install fakeroot and java-package


```

$chmod +x jdk-1_5_0_05-linux-amd64.bin 
$ fakeroot make-jpkg jdk-1_5_0_05-linux-amd64.bin 
Creating temporary directory: /tmp/make-jpkg.XXXX8Fhmir
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

```

Also, if I run the .bin it works but the default java sdk remains the gcj.
I try to remove java-gcj-compat , it states that ubuntu-desktop (between others) has to be removed :D

No,that is not a good ideea now, is it?

I am a long-time gentoo user , and the command from gentoo was something like java-config to change the jdk.

Ok, what should I do?

---

### Post by flyingbrass on 2005-10-27
After it has been installed you want to:```
sudo update-alternatives --config java
```
Select the Sun version.  Not sure if this helps your current situation.

---


---
title: "Install Sun JDK from .bin downloaded file"
date: 2008-12-27
forum: General Help
---

### Post by ehsun7b on 2008-12-27
I have downloaded file **jdk-6u11-linux-i586.bin** from *Sun website*. How can I **install** it on my ubuntu _8.10_? :confused:

---

### Post by cb951303 on 2008-12-27
> **ehsun7b said:**
> I have downloaded file **jdk-6u11-linux-i586.bin** from *Sun website*. How can I **install** it on my ubuntu _8.10_? :confused:

why?

install ubuntu-restricted-extras and you have JAVA + everything (DVD, Codecs, MS Fonts..0 etc.)

EDIT: Sryi you needed jdk in that case install sun-java6-jdk from rpos.

---

### Post by ehsun7b on 2008-12-27
How?
You mean Sun JDK? or Runtime?

---

### Post by namdung on 2008-12-27
> **ehsun7b said:**
> I have downloaded file **jdk-6u11-linux-i586.bin** from *Sun website*. How can I **install** it on my ubuntu _8.10_? :confused:

To install a bin file.
Go to the the folder where the download file is
```
cd folder_with_the_downloaded_file
```

Make the file executable
```
sudo chmod +x filename
```

Install the file
```
sudo ./filename
```

However, I strongly recommend u use the Synaptic Package Manager for hassle free installation of sun-java6-jdk from the Ubuntu repository.

---

### Post by cb951303 on 2008-12-27
> **ehsun7b said:**
> How?
You mean Sun JDK? or Runtime?

it doesnt mater, jdk, jre etc are all in the repos. you don't have a reason to install it from *.bin file

package names are sun-java6-jre and sun-java6-jdk

---

### Post by ehsun7b on 2008-12-27
> **cb951303 said:**
> it doesnt mater, jdk, jre etc are all in the repos. you don't have a reason to install it from *.bin file

package names are sun-java6-jre and sun-java6-jdk


I know, but I have already downloaded it! So it is better to install it than wait again to be downloaded by apt-get!!!

---

### Post by cb951303 on 2008-12-27
> **ehsun7b said:**
> I know, but I have already downloaded it! So it is better to install it than wait again to be downloaded by apt-get!!!

apt-get has dependency checking, easy uninstalling, updating to a new version. with a bin file you install it and your system is not aware of it. when you will try to install a java application (like azureus) it will try to reinstall java6 from repos.

in linux world, package manager is the way to go. use bin files if you don't have any other chance

---


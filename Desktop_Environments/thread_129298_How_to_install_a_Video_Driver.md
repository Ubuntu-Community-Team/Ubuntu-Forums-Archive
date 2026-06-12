---
title: "How to install a Video Driver"
date: 2006-02-13
forum: Desktop Environments
---

### Post by racsw on 2006-02-13
Hi folks,
  I'm not familiar with the Debian system and Umbutu, but after I install Umbutu, I need to also install a video driver from Intel for the Inspiron laptop. This is a tarball from Intel.
Can you tell me the best way to do this under Umbutu?

Thanks,
Robert

---

### Post by zxee on 2006-02-13
[QUOTE=racsw]Hi folks,
  I'm not familiar with the Debian system and Umbutu, but after I install Umbutu, I need to also install a video driver from Intel for the Inspiron laptop. This is a tarball from Intel.
Can you tell me the best way to do this under Umbutu?

Thanks,
Robert[/QUOTE]

The usual way to do this in most linux distros is to open a terminal
making sure you know where the tarball is located on your system.
Do tar -xzvf 'name of tarball' Note there is commandline completion in the terminal so you only need to start to type the name of the tar.gz file and hit the tab key to have it filled in.
After the tar.gz is unpacked and the directory is created cd to the directory
e.g cd /somefilename. In the directory you then do ./configure or check the README with less README. After ./configure then you would issue make and if that completes with no errors then sudo make install will install it-hopefully.

---

### Post by racsw on 2006-02-13
I'll give that a try, as that is the traditional method I'm familiar with.
I thought that Umbutu might have automated the tarball installation procedure somehow similar to the RPM model.

Thanks for your help,
Robert

---


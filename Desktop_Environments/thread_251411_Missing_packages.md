---
title: "Missing packages?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by jkh107 on 2006-09-05
I've just installed Dapper (6.06.1) on a friend's computer and I've been trying to install all the packages necessary for most multimedia things using the Restricted Formats page of the Wiki and the following forum post:

[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

Most of it seems to have installed fine (just as it did on my own computer) except for a few pacakges which aptitude (and apt-get) seemed to be unable to find:

libxine-extracodecs
flashplugin-nonfree
sun-java5-bin
sun-java5-jdk
sun-java5-plugin
msttcorefonts

Before anyone asks, yes I've added the Universe and Multiverse repositories and updated aptitude. So why the problems with these individual packages?

---

### Post by chicken101 on 2006-09-05
I think you have to enable the ubuntu extras repository.  I had to do that one time on my brother's ubuntu box.  

ALthough a quick look at my repository list reveals none that resemble what I remember.

I think I'm going mad.

A quick look in your repos, and you'll probably figure it out.

---

### Post by jkh107 on 2006-09-05
You're right - my repos weren't what I thought they were. Very embarrassing. However, I still can't install msttcorefonts. It's coming up with the error message:

> msttcorefonts: subprocess post-installation script returned error exit status 1

---

### Post by chicken101 on 2006-09-06
Maybe you could try to force it into a different version (using synaptic)

---


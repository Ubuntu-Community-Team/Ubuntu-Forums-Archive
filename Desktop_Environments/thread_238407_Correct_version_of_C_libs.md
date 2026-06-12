---
title: "Correct version of C libs"
date: 2006-08-17
forum: Desktop Environments
---

### Post by mssever on 2006-08-17
A while back, I decided to upgrade to the latest version of BZFlag from the edgy repos (I'm running dapper), and I broke my system. See [this thread]("http://ubuntuforums.org/showthread.php?t=234482"). I now believe that the problem is with the new versions of the C libraries that the upgrade brought in. Unfortunately, I'm not sure which libs are the problem. Synaptic lists the following libs as not installable. I'm assuming they are the ones from edgy. So, can someone provide the correct version for each of these libs for dapper (along with any other bits of wisdom)?
```
[FONT=Courier New]<Package name>       <My installed version>
gcc-4.1-base         4.1.1-9ubuntu1
libc6                2.4-1ubuntu7
libc6-dev            2.4-1ubuntu7
libc6-i686           2.4-1ubuntu7
libcrypt-simple-perl 0.06-1
libgcc1              1:4.1.1-9ubuntu1
libglib2.0-0         2.12.1-0ubuntu1
libglib2.0-data      2.12.1-0ubuntu1
libglib2.0-dev       2.12.1-0ubuntu1
libssl0.9.8          0.9.8b-2build1
libstdc++6           4.1.1-9ubuntu1[/FONT]
```

---

### Post by mlind on 2006-08-17
Try removing libc6 using aptitude and only accept solution which downgrades the package. aptitude should dowgrade dependencies also
```

sudo aptitude purge libc6

```

---

### Post by mssever on 2006-08-17
Thanks. That seems to have solved my C lib problem. However, it also reminded me why I don't use aptitude.

The problem I have with aptitude is that it has some bogus ideas about my system. For example, during this process, aptitude told me:
```
The following packages are unused and will be REMOVED:
  gqview libtagc0 thunar-media-tags-plugin
``` This is bogus. And there is no way to let aptitude do what I want it to do while preventing aptitude from removing those files, as far as I can tell. I stopped using aptitude when it removed xfce-desktop and all dependencies automatically claiming it was unused. It has also made bogus claims about broken packages.

Apt-get and Synaptic have no problems with these packages, and they all work fine. How can I fix aptitude?

---

### Post by mlind on 2006-08-17
> **mssever said:**
> Thanks. That seems to have solved my C lib problem. However, it also reminded me why I don't use aptitude.

The problem I have with aptitude is that it has some bogus ideas about my system. For example, during this process, aptitude told me:
```
The following packages are unused and will be REMOVED:
  gqview libtagc0 thunar-media-tags-plugin
``` This is bogus. And there is no way to let aptitude do what I want it to do while preventing aptitude from removing those files, as far as I can tell. I stopped using aptitude when it removed xfce-desktop and all dependencies automatically claiming it was unused. It has also made bogus claims about broken packages.

Apt-get and Synaptic have no problems with these packages, and they all work fine. How can I fix aptitude?

That's weird. aptitude *should* only remove packages that previously depended on package you installed - and now have removed. Usually this means libraries..
Did you install xubuntu with aptitude previously and have now removed it?

Try pin down these packages by creating **/etc/apt/preferences** file (if it doesn't already exist)
```

Package: gqview
Pin: a=dapper
Pin-Priority: 600

Package: thunar
Pin: a=dapper
Pin-Priority: 600

```

This pinning (by Archive) may not work, but you can find other pinning options from apt_preferences (man apt_preferences) manual page.
Pinning by origin, label or version may work better.

---


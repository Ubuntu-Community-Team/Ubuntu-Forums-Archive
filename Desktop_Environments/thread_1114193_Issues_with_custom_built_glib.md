---
title: "Issues with custom built glib"
date: 2009-04-02
forum: Desktop Environments
---

### Post by lgp171188 on 2009-04-02
I built the latest version of glib and installed it with appropriate usage of ldconfig. But after the install, a lot of Nautilus's behaviour has gone awry.

I want to uninstall the built glib and use ubuntu's version. But unfortunately I deleted the source folder where I built it. So I now have the tarball of the source.

When I do a make uninstall on the extracted source, it gets uninstalled but gdm doesn't start till i do a 'make install' again. I want to use the version of glib shipped with ubuntu. How to do it?

---

### Post by LinuxGuy1234 on 2009-04-02
> **lgp171188 said:**
> I built the latest version of glib and installed it with appropriate usage of ldconfig. But after the install, a lot of Nautilus's behaviour has gone awry.

I want to uninstall the built glib and use ubuntu's version. But unfortunately I deleted the source folder where I built it. So I now have the tarball of the source.

When I do a make uninstall on the extracted source, it gets uninstalled but gdm doesn't start till i do a 'make install' again. I want to use the version of glib shipped with ubuntu. How to do it?

Do a make install in your glib directory, then do:

```
sudo apt-get remove libglib2.0
sudo apt-get install libglib2.0
```

---


---
title: "Gnome schedule 2.30?"
date: 2017-08-13
forum: Desktop Environments
---

### Post by xendistar2 on 2017-08-13
I want to install the above software (installing it from a separate deb file not from the repo) but it requires a file that is no longer available python-support 0.90>=, so my question is, is there a way to get around this or can anybody suggest an alternative scheduling program?

---

### Post by vocx on 2017-08-13
> **xendistar2 said:**
> I want to install the above software (installing it from a separate deb file not from the repo) but it requires a file that is no longer available python-support 0.90>=, so my question is, is there a way to get around this or can anybody suggest an alternative scheduling program?
If you are installing with "dpkg" I think you can force the installation of your ".deb" file while ignoring some dependencies. It seems this is safe to do because the "python-support" is apparently a virtual package that does not do much. I guess this functionality is handled by one of the other python packages, maybe "python-minimal".

So maybe you need to do something like
```

sudo dpkg -i --ignore-depends=python-support file.deb
sudo dpkg -i --force-depends file.deb

```

If that program, Gnome schedule, is old and obsolete, you should probably look for an alternative that runs with modern systems.

---


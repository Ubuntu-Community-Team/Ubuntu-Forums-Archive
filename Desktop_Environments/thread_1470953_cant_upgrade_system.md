---
title: "cant upgrade system"
date: 2010-05-03
forum: Desktop Environments
---

### Post by nerdy_kid on 2010-05-03
hey all, i reported a bug at [https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/573893](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/573893) but nothings happening, so i thought maybe you guys could help me fix it.  basicy i hit the refresh button in kpackagekit's update modual and after it downloads the respitory stuff i get an error:

```

Error Type:
Error Value: coercing to Unicode: need string or buffer, exceptions.SystemError found
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2216, in
main()
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2213, in main
run(args, options.single)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 2175, in run
backend.dispatcher(args)
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 699, in dispatcher
self.dispatch_command(args[0], args[1:])
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 606, in dispatch_command
self.refresh_cache(force)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 202, in _locked_cache
func(*args, **kwargs)
File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1498, in refresh_cache
format_string(error.message))
File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 723, in format_string
txt = unicode(text, encoding, errors='replace')

```

this is a lucid thing cause the same kde version (4.4.2) was working fine in karmic.

is there any way that i can fix this? thanks :)

---

### Post by rockinrobstar on 2010-05-03
I'm getting the same problem. 

Are you trying to use a proxy that requires authentication by any chance ?

---

### Post by nerdy_kid on 2010-05-04
> **rockinrobstar said:**
> I'm getting the same problem. 

Are you trying to use a proxy that requires authentication by any chance ?

nope :(

---

### Post by nerdy_kid on 2010-05-04
ok fixed it, had a bad entry in my sources.list

---

### Post by jbruni on 2010-05-10
In fact, there was a bug in KPackageKit, recently fixed:

**[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/546607](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/546607)**

---


---
title: "pytvgrab?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by amadeus_z on 2006-08-17
Hello,

Does anyone have this working? I can't get it to install under Ubuntu - lots f python errors.

I filed a bug with the developers. Would be nice to have a .deb some day!

Thanks

Amadeus

---

### Post by amadeus_z on 2006-08-28
The solution is posted on their bugs section; just disable tests and it installs:

The tests are run from the setup.py file.
> > You just need to change one line of code.  (line 51)
> >
> >
> > - if os.name == 'posix' or True:
> > + if False:
> >
> >
> > Then it will skip doing the tests.

---


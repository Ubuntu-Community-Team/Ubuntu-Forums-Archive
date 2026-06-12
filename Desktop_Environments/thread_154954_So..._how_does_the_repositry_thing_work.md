---
title: "So... how does the repositry thing work?"
date: 2006-04-04
forum: Desktop Environments
---

### Post by Sunnz on 2006-04-04
Umm... how should I ask this...

Well you know how Ubuntu uses apt to install softwares and stuff like Debian, except it has its own repositry and stuff... using synatic is really the same thing, is it not?

Well the thing is, softwares such as firefox has release their lastest version for some time now, but apt doesn't update them yet... so what is going on? Are they being marked as un-stable or something?

---

### Post by Sef on 2006-04-04
The repositories are updated every 6 months with the release of the new os. (Dapper Drake will be the next one.) So once that is out, they will be updated.

---

### Post by frodon on 2006-04-04
No, for exemple firefox as some dependencies that couldn't be solved in breezy because it would affect other packages therefore the new release of firefox will be in the repositories only for dapper drake (which has all the dependencies that firefox require), however you can install it yourself and it's really easy (it won't be in the repositories for breezy).

---

### Post by Sunnz on 2006-04-04
So... what about those regular updates?

---

### Post by localzuk on 2006-04-04
Repositories are the store of all packages that will work with each other for that release of Ubuntu. For example, Firefox relies on a specific set of packages at specific versions. If it were to be updated (other than security updates) then it would require new dependencies, which in turn are relied upon by other packages which would also need updating.

So, if the maintainers updated a single package in a fundamental way, it could cause a major knock-on effect for many other packages.

The way around this is the Ubuntu-Backports project. (There is a forum linked to from the front page of this site, and repositories are available also). This project aims to allow new packages to be used, unofficially, without damaging others...

---

### Post by Gustav on 2006-04-04
> So... what about those regular updates?
They are security updates and critical bug fixes

---


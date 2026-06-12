---
title: "how do i get iwlib.h? and where does it belong."
date: 2006-09-13
forum: Desktop Environments
---

### Post by aoalneowlknsadflkafgibj on 2006-09-13
im trying to install xsupplicant.1.2.7 and when i type ./configure i get this error
```

checking for iwlib.h... no
configure: error: header file <iwlib.h> is required for Xsupplicant
```

where can i find this file, and how do i put it where it needs to be? thanks.

---

### Post by halfvolle melk on 2006-09-13
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Set "Distribution" to your flavor, I chose Dapper.
Go to "Search the contents of packages"
Paste "iwlib.h" where it says keyword and press enter/click search.
So "sudo apt-get install libiw-dev" seems to be the way to go.

---

### Post by makaira on 2007-06-30
I'm in the same boat. I followed the directions above and I'm still receiving the same exact error as the op.

---

### Post by RagingOcelot on 2007-09-29
Thanks!  I found iwlib.h was in fact in the libiw-dev package.

---


---
title: "Where get make"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Branta on 2006-10-03
I need '**_make_**'

system error msg: **command not found**

Have installed```
sudo apt-get install gnome-devel
```


--- Bob ---

---

### Post by ropers on 2006-10-03
System -- Administration -- Synaptic -- Search -- make
(All repositories need to be enabled)

---

### Post by po0f on 2006-10-03
Branta,

```
sudo apt-get install build-essential
```

---

### Post by az on 2006-10-03
If you have no network access, it is on the install cd.  Just put in the cd and let the package manager start.  You probably want to install "build-essential" which will install make along with other essential bits of the toolchain.

---

### Post by ronmarley1 on 2006-10-03
Install "build-essential" in Synaptic.

---

### Post by ropers on 2006-10-03
build-essential installs make? I seem to recall that it didn't on my default Dapper 6.06 LTS box?

---

### Post by Sef on 2006-10-03
> build-essential installs make? I seem to recall that it didn't on my default Dapper 6.06 LTS box?

To compile, you need to install build-essential.  It is not installed by default.

```


sudo aptitude update

sudo aptitude install build-essential


```

---

### Post by ropers on 2006-10-03
Ah, so you were saying that the OP really needs to install build-essentials and make, That's very true of course.

---

### Post by az on 2006-10-03
> **ropers said:**
> Ah, so you were saying that the OP really needs to install build-essentials and make, That's very true of course.

No.  Build-essential depends on make so it will be installed when you install build-essential.  Always has.

---

### Post by ropers on 2006-10-03
Apologies, my bad. You are correct. I had installed build-essential, then wrecked and rebuilt my box and then thought that I appeared to have to manually install make when I found it missing. I've just seen that I did not in fact have build-essential installed following the rebuild.

---


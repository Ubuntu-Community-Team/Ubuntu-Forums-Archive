---
title: "How do I add plugins to compiz"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by Khuezy on 2007-10-20
I want to add the unofficial "3d windows" and snow
thanks

---

### Post by Espreon on 2007-10-20
Do these in a terminal:

3D:

```

git-clone git://http://gitweb.beryl-project.org/fusion/plugins/3d
cd 3d
make
cd ..

```

Snow:

```

git-clone git://http://gitweb.beryl-project.org/fusion/plugins/snow
cd snow
make

```

If this don't work, type this in a terminal:

```

sudo apt-get install compiz-bcop

```

---

### Post by Khuezy on 2007-10-21
Hmm, it said it failed fetching it

---


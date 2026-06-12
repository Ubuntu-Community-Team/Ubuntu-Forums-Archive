---
title: "Additional AWN Seperators?"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by SupraBlur on 2007-11-27
So out of curiousity, is there any way to add more seperators in AWN?  I used to use AquaDock for Windows, and with seperators I could at least group different types of applications together.

-Ray

---

### Post by Ub1476 on 2007-11-27
If you awn-extras installed, open AWN manager>Applets>Click on Separator>Move to "active applets".

If you don't have awn-extras installed, here's how to do it:

1. [Download]("https://launchpad.net/awn-extras/+download") the source from Launchpad.

2. Extract it.

3. Open the terminal and write:

```
cd awn-extras-applets-0.2.1

./configure

make

sudo make install
```

Note that this package is in beta stage, but it works fine for me:)

---

### Post by SupraBlur on 2007-11-29
Yes I've activated the seperator from the applets, but unfortunately it only adds a seperator to the applets section, and I can't seem to move it over to where my regular program launchers are.

-Ray

---


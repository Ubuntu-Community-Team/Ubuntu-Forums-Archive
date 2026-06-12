---
title: "awn help please."
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by Parms on 2007-08-24
I installed compiz-fusion + emerald. which work successfully. Now I want to install awn. I followed this guide...

[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn](http://ubuntuforums.org/showthread.php?t=385981&highlight=awn)

which was the same as this one (except adding dependencies)
[https://launchpad.net/awn](https://launchpad.net/awn)

I get to the part where it says:  ./autogen.sh

I get the no such file or directory found. am I missing something??

64 bit amd 7.04 fiesta

---

### Post by praet on 2007-08-28
What you are missing is making that script executable.

Try this in terminal:

```
chmod +x autogen.sh
```

then try the script again

```
./autogen.sh
make
sudo make install
```

---


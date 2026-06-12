---
title: "Ark"
date: 2005-10-20
forum: Desktop Environments
---

### Post by ColinG on 2005-10-20
I cannot run Ark. When I try as normal user I'm told it is not in my path and when i try to run it as sudo I get

colin@ubuntu:~$ sudo ark
Password:
ERROR: Communication problem with ark, it probably crashed.
colin@ubuntu:~$

I unintslled and reinstalled but the problem remains.

Help please

Thanks
Colin

---

### Post by GeneralZod on 2005-10-21
That's a weird one.  What is the output of 

```

ls -l  /usr/bin/ark

```

and

```

echo $PATH

```

?

As for the lack of sudo support, this is oddly common with KDE apps (kate is another offender).  It doesn't work here, either.

```

kdesu ark

```

does, though, but I don't recommend you run ark as root ever.

Edit:

Have you tried

```

sudo apt-get install ark

```

?

---


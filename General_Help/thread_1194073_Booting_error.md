---
title: "Booting error"
date: 2009-06-22
forum: General Help
---

### Post by michael1384 on 2009-06-22
Sometimes, when I try to boot up Ubuntu, it displays an error. When this happens it drops to the shell and I type, 'reboot' and it might do it again, it might not.

Here's a screenshot:

[IMG]http://img194.imageshack.us/img194/719/errorcak.jpg[/IMG]

---

### Post by clonne4crw on 2009-09-28
Happened to me with some old hard drives. Yours is beginning to fail. There's no real way to know how much life is left in it. Can you hear anything going on while the DRDY error messages scroll by?

You can almost always just wait for the messages to stop before trying to log in, but that may take hours or days to finish. I guess if you are like me and just want to make it go away, you just edit /etc/fstab to skip any kind of disk checks:

edit the line that has the troubled hard drive, and change the last digit from a 1 to a 0

```

UUID=cd26de7d-85ff-48cd-9d52-9a02bf4ff078    /     ext3    defaults     0       1

```

becomes

```

UUID=cd26de7d-85ff-48cd-9d52-9a02bf4ff078    /     ext3    defaults     0       0

```

Of course, the proper thing to do is use something like [SpinRite]("http://www.grc.com/spinRite.htm") and actually repair the hard drive. It's a little expensive, but I have only heard good things about it.

---


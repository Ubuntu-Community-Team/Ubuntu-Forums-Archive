---
title: "about vmware workstation"
date: 2005-12-20
forum: General Help
---

### Post by Element.Ren on 2005-12-20
i installed vmware workstation on breezy,and i run it in terminal.it shows:```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** attempt to put segment in horiz list twice

```

what should i do? i am new to here,please help me.
thanks.

---

### Post by zoiks on 2005-12-20
[QUOTE=Element.Ren]i installed vmware workstation on breezy,and i run it in terminal.it shows:```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** attempt to put segment in horiz list twice

```

what should i do? i am new to here,please help me.
thanks.[/QUOTE]

I get the same message, but vmware seems to work fine nonetheless in breezy.

---

### Post by Element.Ren on 2005-12-20
i don't want to run it in terminal.
application-->systemtool-->vmware,it doesn't work.i want it work from here.
anyone can help me?
thanks.

---

### Post by shadow07 on 2005-12-20
You never stated what version of Vmware Workstation you are running.  Technically, only v5.x works on Breezy.  V5.5 is the only official supported version of Workstation on Breezy.

---

### Post by rcerreto on 2005-12-20
I'm using VMware Workstation V5.0.0
If I start it from the shell, I get the same error message you're reporting.
But vmware starts and works OK.
Applications -> System Tools -> VMware Workstation works fine too.
Hard to understand what's wrong with your config.

I installed VMware using vmware-any-any-update94.
Could that make a difference?

---

### Post by imagine on 2005-12-22
You didn't try to use the rpm archive in Ubuntu, did you?
If so then uninstall it and grab the tar.gz file.

---


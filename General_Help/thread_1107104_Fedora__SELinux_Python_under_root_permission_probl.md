---
title: "Fedora:  SELinux Python under root permission problems"
date: 2009-03-26
forum: General Help
---

### Post by sayeo87 on 2009-03-26
Hi,

I'm running Fedora and Currently I have this problem where when I run a python script under a normal user, it works, but I get errors when running it under root:
```
[root@cypher PerlC]# ./xdot.py
Traceback (most recent call last):
  File "./xdot.py", line 35, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 48, in ?
    from gtk import _gtk
ImportError: /opt/mono-1.9/lib/libpng12.so.0: cannot restore segment prot after reloc: Permission denied
[root@cypher PerlC]# ./xdot.py
Traceback (most recent call last):
  File "./xdot.py", line 35, in ?
    import gtk
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 48, in ?
    from gtk import _gtk
ImportError: /opt/mono-1.9/lib/libpng12.so.0: cannot restore segment prot after reloc: Permission denied
```

This is what is shown in var/log/messages:
```
Mar 26 10:30:10 cypher kernel: audit(1238077810.738:17): avc:  denied  { execmod } for  pid=24382 comm="python" name="libpng12.so.0.1.2.5" dev=sda2 ino=4262289 scontext=user_u:system_r:unconfined_t:s0 tcontext=user_u:object_r:usr_t:s0 tclass=file
```

I did some searching and realized its an SELinux permission issue, and here is some of the permission info for the files in question:
```
[root@cypher mono-1.9]# ls -aZ /usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py
-rw-r--r--  root root system_u:object_r:lib_t          /usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py
```
```
[root@cypher mono-1.9]# ls -aZ /opt/mono-1.9/lib/libpng12.so.0
lrwxrwxrwx  root root user_u:object_r:usr_t            /opt/mono-1.9/lib/libpng12.so.0 -> libpng12.so.0.1.2.5

```

I really don't know where to go from here. I've read about chcon but I'm not sure what to change for my case. Would really appreciate any help!

---

### Post by NullHead on 2009-03-26
You might get more fedora specific help on the [fedora forums]("http://fedoraforum.org/")

---

### Post by Simian Man on 2009-03-26
[LIST]
[*]If it works under normal user, why run it as root?
[*]Do you need SELinux?  For desktops, I disable it as some SW still is written improperly and violates it
[/LIST]

It sounds like it is the problem with relocatable segments.  This *could* be used to write malicious code, but a few programs still use it.  If that's the case, you're mostly SOL w/o rewriting the app.

---

### Post by sayeo87 on 2009-03-26
Well, its messy, but with the setup we now have it would be best if I could find a way to run it as root. And this is all on a server, so I think disabling SELinux is not such a good option. So Simian Man, you think there is no way I can use chcon etc to modify the permissions to make this work? Because I was under the impression that was all that had to be done....

---

### Post by Simian Man on 2009-03-26
OK I had the same problem with Google Earth a while back.  I just disabled SELinux, but it seems there is a workaround for this ([I found this here]("http://dnmouse.org/googleearth.html")).

Try running the following command:
```

chcon -t textrel_shlib_t '/opt/mono-1.9/lib/libpng12.so.0'

```

That should change the security context of that shared object to allow the relocatable segments.

---


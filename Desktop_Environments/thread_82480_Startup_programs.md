---
title: "Startup programs"
date: 2005-10-26
forum: Desktop Environments
---

### Post by christooss on 2005-10-26
Where can I find list of al programs wich start at boot up. For example xscreensaver is program which I don't want to start at Boot

Thanks for the anwsers

---

### Post by Xian on 2005-10-26
With xscreensaver you'd probably just be better off removing that program. I'm not sure what calls it into action but most likely it is in the actual Gnome configuration. As for control of runlevel system services I would go this route:

$ sudo apt-get install sysv-rc-conf
$ sudo sysv-rc-conf

---

### Post by gillion on 2005-10-26
**BUM**

Install it and use it.


```

Boot-Up Manager  version 1.3.4

Graphical runlevel configuration editor for Debian-based systems.
 
BUM allows to configure init services when the system boots up or re_boots. It displays a list of every service which could be started at boot. User can toggle individual services on and off.

```

A detailed documentation on the program could be read at: [http://www.marzocca.net/linux/bumdocs.html](http://www.marzocca.net/linux/bumdocs.html).

A link is here
[http://gnomefiles.org/download.php?soft_id=1004&where=http%3A%2F%2Fpackages.debian.org%2Fbum](http://gnomefiles.org/download.php?soft_id=1004&where=http%3A%2F%2Fpackages.debian.org%2Fbum)

and here...

[img]http://www.marzocca.net/Immagini/bum1_new.jpg[/img]

---

### Post by Xian on 2005-10-26
Yeah, BUM puts a pretty face on sysv-rc-conf if you like that kind of thing.
It or something like it should be a default installed program.

That idea transferred to xorg.conf editing would be golden.

---

### Post by christooss on 2005-10-27
when installing Bum and than runing it I get this error
```
matic@ubuntu:~/Desktop$ sudo bum
Can't locate Gtk2/GladeXML.pm in @INC (@INC contains: /usr/lib/bum /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/bum/bum_app.pm line 44.
BEGIN failed--compilation aborted at /usr/lib/bum/bum_app.pm line 44.
Compilation failed in require at /usr/bin/bum line 27.
BEGIN failed--compilation aborted at /usr/bin/bum line 27.

```

---


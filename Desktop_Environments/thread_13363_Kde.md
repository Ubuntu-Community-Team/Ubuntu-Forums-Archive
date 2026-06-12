---
title: "Kde?"
date: 2005-01-30
forum: Desktop Environments
---

### Post by squeakypants on 2005-01-30
Sorry if this is obvious, but I'm new to almost everything linux (though I have a little experience in PHLAK). Does warty come with KDE? If not, what is the easiest way to install it? If so, where can I access it?

I only posted it here because I'm not sure if it is preinstalled, though it wasn't listed.

---

### Post by bitfoo on 2005-01-30
Ubuntu comes with gnome by default.  I'm not sure, but if you edit your sources.list to include universe (and maybe multiverse?), you can probably just "sudo apt-get install kde".  Don't quote me on that though, gnome is enough for me. :D

---

### Post by squeakypants on 2005-01-30
[QUOTE=bitfoo]if you edit your sources.list to include universe (and maybe multiverse?), you can probably just "sudo apt-get install kde"[/QUOTE]

all i got was:
> you can probably just "sudo apt-get install kde"

---

### Post by squeakypants on 2005-01-30
[QUOTE=squeakypants]all i got was:[/QUOTE]
 I've figured out wher sources.list is, but what is universe/multiverse???

---

### Post by bitfoo on 2005-01-30
here :|

[http://www.ubuntulinux.org/wiki/InstallingKDE](http://www.ubuntulinux.org/wiki/InstallingKDE)

---

### Post by squeakypants on 2005-01-30
[QUOTE=bitfoo]here :|

[http://www.ubuntulinux.org/wiki/InstallingKDE](http://www.ubuntulinux.org/wiki/InstallingKDE)[/QUOTE]
 doin it now, thanks!

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=squeakypants]doin it now, thanks![/QUOTE]

The hoary development version has 3.3 in its repos now..

Kubuntu- [http://www.ubuntulinux.org/wiki/Kubuntu](http://www.ubuntulinux.org/wiki/Kubuntu)

---

### Post by poofyhairguy on 2005-01-31
By the way BIG WARNING!

Only run K3B with this command:

gksudo k3b

or risk borking your setup.

---

### Post by valadil on 2005-01-31
Can we get some more info on gksudo k3b or risk borking your setup?  I've seen this message a few times with little to no explanation.  k3b has treated me fine.

---

### Post by nocturn on 2005-02-01
[QUOTE=valadil]Can we get some more info on gksudo k3b or risk borking your setup?  I've seen this message a few times with little to no explanation.  k3b has treated me fine.[/QUOTE]

I'm wondering about that too.

On my system, k3b works fine as a user, on my wife's system, the writer gets detected as a reader, while it works under root...

---


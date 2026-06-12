---
title: "cannot remove broken package"
date: 2009-04-04
forum: General Help
---

### Post by razored on 2009-04-04
I have tried to play around with installing iscan but somehow I corrupted the package and synaptic is unable to remove it. When I try to remove it from terminal by typing sudo apt-get -f install
I get this error : 


```
(Reading database ... 162653 files and directories currently installed.)
Removing iscan ...
/var/lib/dpkg/info/iscan.postrm: 50: Bad substitution
dpkg: error processing iscan (--remove):
 subprocess post-removal script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 iscan
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now, I try to go to the synaptic GUI and press APPLY to remove the package, I get the following error : ```
E: iscan: subprocess post-removal script returned error exit status 2

```

I do not know what to do. Can anyone help?

---

### Post by gettinoriginal on 2009-04-05
Found this, look about 2/3 of the way down.  Hope it helps.

---


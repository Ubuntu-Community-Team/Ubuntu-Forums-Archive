---
title: "Vmware tools - I'm Using Ubuntu as guest on vmware"
date: 2009-02-14
forum: General Help
---

### Post by sharif_aly on 2009-02-14
I'm using vmware as guest OS in vmware and I try to check the bath

I did use the following commands :
>     cp /cdrom/*.gz /tmp/

    cd /tmp

    tar xvzf VM*.gz

    cd vmware*

    sudo ./vmware-install.pl


But i Have no idea what is the path ?
> What is the directory that contains the init directories (rc0.d/ to rc6.d/)?

I don't know where is the path what is the answer this question ?


I'm stuck and waiting to know what to answer to this script.

---

### Post by hyper_ch on 2009-02-14
it's

/etc

and for future reference

(1) run
```

sudo updatedb

```

(2) search
```

locate NAME

```

e.g.
```

locate rc0.d

```

---

### Post by sharif_aly on 2009-02-14
Thanks,

I just don't know why vmware tools not in synaptic

---


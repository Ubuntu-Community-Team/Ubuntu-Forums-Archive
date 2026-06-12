---
title: "Update and Upgrade errors"
date: 2009-05-02
forum: General Help
---

### Post by OxentroT on 2009-05-02
Hello, 

I am trying to fetch some updates and an upgrade for newly re-installed 8.10.
updates happens as follows:

```
sudo apt-get updates
COMMAND NOT FOUND
```

and when I attempt to fetch an upgrade it goes smoothly in the beginning until I am shown a Sub-process gzip returned an error code (1) for several of the pkgs eg:

```
E:Sub-process /usr/bin/dpkg returned an error code(1)
```

any ideas would be greatly appreciated. thankyou!

---

### Post by B4RR13N705 on 2009-05-02
I think that is not "updates", is "update"
>  sudo apt-get update 

---


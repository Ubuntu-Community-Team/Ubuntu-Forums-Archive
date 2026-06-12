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

and when I attempt to fetch an upgrade it goes smoothly in the beginning until I am shown a Sub-process gzip returned an error code (1) for several of the pkgs.

any ideas? thankyou

---

### Post by zvacet on 2009-05-03
```
sudo apt-get update
```

and if something is not right try with 

```
sudo dpkg --configure -a
```

---

### Post by OxentroT on 2009-05-03
thankyou

---


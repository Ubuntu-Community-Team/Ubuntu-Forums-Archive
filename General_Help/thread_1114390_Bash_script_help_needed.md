---
title: "Bash script help needed"
date: 2009-04-02
forum: General Help
---

### Post by headlice on 2009-04-02
Hi,

I have a bunch of files that need to be renamed.

Basically after conversion, these files are now named like this:

filename.m4p.wav

I need to remove the .m4p from the file name.

Can someone help me with this?

Thanks!

---

### Post by dpirotte on 2009-04-02
This should take care of it for you:

```
for i in *.m4p.wav ; do mv "$i" "${i/.m4p.wav}".wav ; done
```

Cheers,

Dave Pirotte

---

### Post by headlice on 2009-04-02
> **dpirotte said:**
> This should take care of it for you:

```
for i in *.m4p.wav ; do mv "$i" "${i/.m4p.wav}".wav ; done
```

Cheers,

Dave Pirotte

OH SWEET!  Works!  Thanks!

---


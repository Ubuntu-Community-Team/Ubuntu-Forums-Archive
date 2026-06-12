---
title: "apt-get install problem"
date: 2009-03-30
forum: General Help
---

### Post by Inane_Asylum on 2009-03-30
I'm trying to install the screensaver compiz plugin, but when I try and sudo apt-get install compiz-bcop, I get the error
```

andrew@Vault-13:~/compiz/screensaver$ sudo apt-get install compiz-bcop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
E: Package compiz-bcop has no installation candidate
andrew@Vault-13:~/compiz/screensaver$

```

any ideas?

---

### Post by kanikilu on 2009-03-30
Have you tried what it suggests and use *compiz-fusion-bcop* instead?

---

### Post by Inane_Asylum on 2009-03-30
DOH!
Now I'm getting
```

andrew@Vault-13:~/compiz/screensaver$ make
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema'ing: build/screensaver.xml -> build/compiz-screensaver.schemawarning: failed to load external entity "/schemas.xslt"
cannot parse /schemas.xslt
make: *** [build/compiz-screensaver.schema] Error 4
andrew@Vault-13:~/compiz/screensaver$ 

```

---

### Post by Inane_Asylum on 2009-03-30
Nevermind...fixed:)

---

### Post by sailingAL20 on 2009-04-02
> **Inane_Asylum said:**
> Nevermind...fixed:)

How did you fix it because i'm having the same issue.
adam@adam-laptop ~/compiz/screensaver $ make
convert   : screensaver.xml.in -> build/screensaver.xml
bcop'ing  : build/screensaver.xml -> build/screensaver_options.h
bcop'ing  : build/screensaver.xml -> build/screensaver_options.c
schema'ing: build/screensaver.xml -> build/compiz-screensaver.schemawarning: failed to load external entity "/schemas.xslt"
cannot parse /schemas.xslt
make: *** [build/compiz-screensaver.schema] Error 4

---

### Post by Inane_Asylum on 2009-04-02
My problem was that I was using the install directions for the wrong Ubuntu version.  I was trying the Gutsy install (for some weird reason...) but after following the Intrepid install it worked.

That being said, the screensaver plugin didn't really work for me.  As long as I set the initiate timer to less than 4.8 minutes or so, it'd work.  Otherwise, nothing.  After disabling it and re-enabling my screensaver and power management, they didn't work either.  So I ran make uninstall.  Screensaver/monitor shut-off still not working, so...I have a week ahead of me figuring this one out :-/

---


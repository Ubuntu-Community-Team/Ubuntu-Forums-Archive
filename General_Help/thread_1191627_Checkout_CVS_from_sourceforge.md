---
title: "Checkout CVS from sourceforge"
date: 2009-06-19
forum: General Help
---

### Post by mikeym on 2009-06-19
Hi,

Could someone tell me how to get a CVS from sourceforge anonymously?

I'm looking for PCSX (as directed on [this page]("http://pcsx-df.sourceforge.net/download.php")) because I want to see if they've got any other plugins that arn't in the repo. I've tried:

```
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/pcsx-df login
```

but when I hit enter for the password I get:

```
cvs [login aborted]: connect to cvs.sourceforge.net(216.34.181.96):2401 failed: Connection refused
```

I am able to ping *cvs.sourceforge.net*, but I can't connect.

---

### Post by andrew.46 on 2009-06-20
Hi mikeym,

Your syntax is not quite right. Try:

```

cvs -d:pserver:anonymous@pcsx-df.cvs.sourceforge.net:/cvsroot/pcsx-df login

```

and then:

```

cvs -z3 -d:pserver:anonymous@pcsx-df.cvs.sourceforge.net:/cvsroot/pcsx-df co -P pcsx-df

```

This certainly worked for me.

Andrew

---


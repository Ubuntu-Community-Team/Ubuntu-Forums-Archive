---
title: "Self-signed certificates stops Kazehakase"
date: 2008-12-11
forum: Desktop Environments
---

### Post by TylerMD on 2008-12-11
When visiting with Kazehakase a web site with a self-signed certificate like this one: [https://mail.gna.org/public/kazehakase-cvs/](https://mail.gna.org/public/kazehakase-cvs/). the following message appears:

```
mail.gna.org uses an invalid security certificate.

The certificate is not trusted because it is self signed.

(Error code: sec_error_untrusted_issuer)
```

I only can click "OK" and the nothing happens. It is impossible to go on like in Firefox where you can add an exception.

Is there any way I can workaround this?

---

### Post by TylerMD on 2008-12-27
Hi again. A working solution was posted here: [https://gna.org/bugs/?12390](https://gna.org/bugs/?12390)

---


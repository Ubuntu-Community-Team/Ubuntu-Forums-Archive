---
title: "Error when running update manager"
date: 2009-05-01
forum: General Help
---

### Post by user 123 on 2009-05-01
Every time i try to run update manager and check for new updates i get this error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

Anyone know what this is?

---

### Post by mb_webguy on 2009-05-01
```
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -

```

You could alternatively add the key by downloading it from Launchpad and adding it through the Authentication tab in Software Sources, but the process is a bit awkward and a bit too complicated.

---

### Post by calvinps on 2009-05-01
> **mb_webguy said:**
> ```
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
gpg --export --armor 6AF0E1940624A220 | sudo apt-key add -

```

Run this in Terminal (Applications --> Accessories --> Terminal)

---

### Post by user 123 on 2009-05-01
Thanks, worked perfectly!

---


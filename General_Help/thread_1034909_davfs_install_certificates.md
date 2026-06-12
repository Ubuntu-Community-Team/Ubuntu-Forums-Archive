---
title: "davfs: install certificates"
date: 2009-01-09
forum: General Help
---

### Post by RikoW on 2009-01-09
Dear all,

how do I install a specific server certificate for ssl. I'm using davfs to access some webdav resources from my ubuntu box. When mounting webdav resource, I'm warned about a missing certificate:

```
/sbin/mount.davfs: the server certificate is not trusted
  issuer:      X
  subject:     XX
  identity:    webdav.server.com
  fingerprint: xx:xx:xx:xx
You only should accept this certificate, if you can
verify the fingerprint! The server might be faked
or there might be a man-in-the-middle-attack.
Accept certificate for this session? [y,N] y
```

Just accepting works, but I'd like to get rid of this warning. I have the needed certificate as .pem file. How do I install it?

Thanks,

                  Riko

---

### Post by Bill Day on 2009-11-16
Bump.  I am having the same issue in Karmic Koala 9.10.

---

### Post by RikoW on 2009-11-16
Hi,

I actually solved that recently (a few days ago), but completely forgot to update the thread. It's actually quite simple. Get hold of the certificate in .pem format and copy the file to 

```
> sudo cp example.pem /etc/davfs2/certs
```

then update the davfs2 config in /etc/davfs2

```
> cat /etc/davfs2/davfs2.conf
[...]
# WebDAV Related Options
# ----------------------

# use_proxy       1                 # system wide config file only
# proxy                             # system wide config file only
servercert	example.pem
[...]
```

This make the certificate available system wide. According to the man pages for mount.davfs you can also install it just in the user config.

Cheers,

        Riko

---

### Post by Stocken on 2012-05-03
Sorry to be bumping an old thread but I haven't been able to find an answer anywhere else.

How do I get hold of a certificate in pem format? I have read in some other forum that it is possible to create a self-signed certificate, but how do I do that?

/J

---


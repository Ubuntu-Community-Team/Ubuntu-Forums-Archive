---
title: "Force Accept Certificates when Using mount.davfs?"
date: 2008-03-31
forum: Desktop Environments
---

### Post by RAdams on 2008-03-31
**NOTES:**
[LIST=1]
[*]I provided as much detail as I thought relevant. It may be overload, which is why I included "The Short Story".
[*]The URIs and confidential information was deliberately obfuscated, but the content is otherwise verbatim.
[*]I'm not sure if I need to involve the davfs2.conf here, it doesn't seem to have any helpful options for this problem. FWIW, mine is unchanged from defaults.
[*]Yes, I realize I could just purchase an SSL cert and this warning would go away, that's not the point.
[/LIST]

**The Short Story:**
I'm in need of a way to bypass the untrusted server warning you get when mounting a secure WebDAV share with davfs2, or a workaround that does effectively the same thing. That's probably not enough to go on, so...

**The Long Story:**
CPanel 11 has this great WebDAV interface called "Web Disk". It's just an easy-to-configure WebDAV share, using SSL to talk on port 2078. However, their instructions for accessing the share with Gnome are rubbish, so I had to find my own path.

I found the package davfs2, which meets my needs... almost. I can use it to make an fstab entry like:
```

https://example.com:2078 /media/example.com davfs uid=user,gid=group 0 0

```

Then in /etc/davfs2/secrets:
```

https://example.com:2078    username        password

```

This does what I'm looking for: mounts the Secure WebDAV share to /media/example.com using a given username/password.

BUT, it prompts each time with a security warning:
```

/sbin/mount.davfs: the server certificate does not match the server name
/sbin/mount.davfs: the server certificate is not trusted
  issuer:      Unknown, Unknown, Unknown, Unknown, US
  subject:     Unknown, Unknown, Unknown, Unknown, US
  identity:    host.example.com
  fingerprint: a1:1a:11:af:11:11:11:1f:11:ad:1c:11:1a:11:11:11:aa:1b:db:fd
You only should accept this certificate, if you can
verify the fingerprint! The server might be faked
or there might be a man-in-the-middle-attack.
Accept certificate for this session? [y,N]

```

I can't figure out how to avoid this prompt. I saw this in /etc/davfs2/secrets:
```

# Password for Client Certificate
# -------------------------------
# It must contain the name of the certifcate file and the encryption passord.

# Examples
# otto_private.crt              "this is extraordinary secret"
# "otto private.crt"            this\ is\ secret,\ too.

```

So I generated a self-signed certificate (via WHM, but that's just a frontend) and saved it as example.crt in /etc/davfs2/certs:

```

-----BEGIN CERTIFICATE-----
AREALLYLONGSTRINGOFNUMBERSANDLETTERS1234
-----END CERTIFICATE-----

```

Then put this into secrets:
```

/etc/davfs2/certs/example.crt  password

```

Nothing. I also tried it without the absolute path. Do I need to put the RSA key into private or something? I'm not clear on how the Certificates work here.

**So what can I do to avoid that warning every time I start up or mount the share?**

---


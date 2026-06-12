---
title: "Nautilus, webdav and authentication"
date: 2009-02-15
forum: Desktop Environments
---

### Post by gnutered on 2009-02-15
It seems I have a problem with using webdav in Nautilus.  My root cause is that I can't successfully write (create folders or upload files) using webdav in Nautilus, to my gallery2 webapp.

Note that I can make it work in cadaver, because when I "put" a file with cadaver, it asks for username and password, and can then write.

So I suspect that Nautilus doesn't choose to ask for extra credentials when a write operation occurs.

I tested this hypothesis by running a packet capture.  In none of the packets is there any string that matches my username.

Is this right?  Is there a way to force Nautilus to use credentials?  Note that I tried putting in a username in the dialog under "Connect to server" but it didn't help.

My other option is to stop the webdav server allowing anonymous connections.  However I don't know that the webapp has the smarts for this.

Tony

---

### Post by terrrorr on 2009-06-07
Hi,

This is quite old post, so I hope somebody has some kind of solution. I just installed Apache and enabled basic WebDAV functionalities. If I use Cadver from shell everything seems to work like a charm, but no glory if Nautilus is used. Is there any workarounds or is it possible that I have missed something when I configured my Apache2-WebDAV environment.

Please notice. WebDAV access works from MS Windows XP and Cadver

---

### Post by ibuclaw on 2009-06-07
To connect to a webdav file server in nautilus, you use the "**davs://**" prefix, in the address bar.
ie:
```
davs://the-site.com
```

Other than that, I think you should really open a new thread on your issue :)

Regards
Iain

---

### Post by reto on 2011-12-14
Nautilus seems to behave differently when the username is entered in the first dialog were the servername is specified. While connection fails if the username is entered in this dialog it suceeds when enetering username and password when asked for it.

Cheers,
Reto

---

### Post by Matt_Fussell on 2011-12-22
> **ibuclaw said:**
> To connect to a webdav file server in nautilus, you use the "**davs://**" prefix, in the address bar.
ie:
```
davs://the-site.com
```

Other than that, I think you should really open a new thread on your issue :)

Regards
Iain

I know this is two+ years after the fact, but thank for the instructions - I was ready to break things.

@Reto - Is webdav working for you then?

Apologies if I'm violating rules for thread-rez-ing.

---


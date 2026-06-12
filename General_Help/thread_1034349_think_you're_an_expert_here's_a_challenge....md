---
title: "think you're an expert? here's a challenge..."
date: 2009-01-08
forum: General Help
---

### Post by vsccreative on 2009-01-08
Hi all, top marks for whoever can figure this one out:

I have two servers, both running Ubuntu 8.04.

One called 'clients', the other 'smartest'.

I am trying to get public key authentication working on both of them, so that I can SSH from my Mac using public key auth.

I generated ONE DSA key, some time ago, which has been in use successfully with another unrelated Debian server.

With the first of my two servers, 'clients', I scp'ed the .pub file to my home directory, and concatenated it to .ssh/authorized_keys, restarted ssh with '/etc/init.d/ssh restart', and hey presto, it works!

ssh -v ... outputs:

debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /Users/marcus/.ssh/id_dsa
debug1: Server accepts key: pkalg ssh-dss blen 434
...
debug1: Entering interactive session.

Second server, I try the exact same thing, and it doesn't work. I am prompted for a password: 

ssh -v ... again:

debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /Users/marcus/.ssh/id_dsa
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
marcus@smartest's password:

I scp'ed my ~/.ssh/authorized_keys from clients to a file called 'clients_authorized_keys.txt' on smartest and ran a diff on them. No output - in other words, they are identical.

I copied the /etc/ssh/sshd_config file from clients to my home dir on smartest and ran a diff on them too - also identical.

Then I ran 'dpkg -l | awk '{print $2}' > installed_packages.txt' on both servers to see the installed packages on them. These are the 59 packages installed on clients that are not installed on smartest (where the pub key auth fails). They are mostly there because I was building PHP with lots of extensions. Could any of them be the reason? If not, what's the problem?

apache2-threaded-dev, libbz2-dev, libc-client2007, libc-client2007-dev, libcurl4-gnutls-dev, libfontconfig1-dev, libfreetype6-dev, libgcrypt11-dev, libgd2-xpm, libgd2-xpm-dev, libgdbm-dev, libgnutls-dev, libgnutlsxx13, libgpg-error-dev, libgsasl7, libgsasl7-dev, libidn11-dev, libjpeg62-dev, liblockfile1, liblzo2-dev, libmagic-dev, libmysqlclient-dev, libmysqlclient15-dev, libmysqlclient16, libntlm0, libopencdk10-dev, libpam0g-dev, libpng12-dev, libpthread-stubs0, libpthread-stubs0-dev, libtasn1-3-dev, libtidy-0.99-0, libtidy-dev, libvmime-dev, libvmime0, libx11-dev, libxau-dev, libxcb-xlib0-dev, libxcb1-dev, libxcrypt-dev, libxdmcp-dev, libxpm-dev, libxslt1-dev, make-doc, mlock, php5-tidy, php5-xsl, procmail, sendmail, sendmail-base, sendmail-bin, sendmail-cf, sensible-mda, tidy, whois, x11proto-core-dev, x11proto-input-dev, x11proto-kb-dev, xtrans-dev

---

### Post by hyper_ch on 2009-01-08
(1) on the mac create a key
```

ssh-keygen -t dsa

```

(2) transfer the key to the "remote" computers
```

cat ~/.ssh/id_dsa.pub | ssh -l user server 'cat >> ~/.ssh/authorized_keys'

```
where user is the user to login at the remote and server is the remote computer.

Well, not sure if that works on mac but as it's a BSD running it should be.

---

### Post by vsccreative on 2009-01-14
Yes, thanks, I did that without a problem before posting here.

This what I'm saying, and this is why this is tagged as difficult - I did this twice identically, once for each server. I worked on one, but not the other.

The ssh and sshd configurations are the same (checked with diff), the OS is the same (Ubuntu 8.04 - from same image both times), and the file .ssh/authorized_keys is the same (again did a diff. Even permissions are identical).

Even my username on the two boxes is the same, yet on one it accepts the key and the other it doesn't.

No idea why as all of the most obvious options are covered.

---


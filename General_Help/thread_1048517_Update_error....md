---
title: "Update error..."
date: 2009-01-23
forum: General Help
---

### Post by x C0MMAND0 x on 2009-01-23
When I run

```
sudo apt-get update
```

Everything runs okay, but then I get this message at the very end:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BBD133164234534
W: You may want to run apt-get update to correct these problems
```

I checked my **/etc/apt/sources.list** and the only items with ppa.lauchpad are all my entries for XBMC (Xbox Media Center), which are

```

# XBMC
deb http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu intrepid main
deb http://ppa.launchpad.net/xbmc-addons/ubuntu intrepid main
deb-src http://ppa.launchpad.net/xbmc-addons/ubuntu intrepid main
deb http://ppa.launchpad.net/team-xbmc-svn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/team-xbmc-svn/ubuntu intrepid main

```

What is the issue and work around here?  I have not seen this issue before and I am not sure if it is really critical at all...

---

### Post by kellemes on 2009-01-23
Not critical..

Type from a terminal window.
```
sudo gpg --keyserver subkeys.pgp.net --recv 2BBD133164234534
sudo gpg --export --armor 2BBD133164234534 | sudo apt-key add -
sudo apt-get update

```

---

### Post by x C0MMAND0 x on 2009-01-23
Thank you, but when I ran the first command, this is the output.

```
brent@Prometheus:~$ sudo gpg --keyserver subkeys.pgp.net --recv 2BBD133164234534gpg: WARNING: unsafe ownership on configuration file `/home/brent/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

What does that mean?  Thank you very much for your help, I appreciate it a lot.

---

### Post by kellemes on 2009-01-23
Yes, it should be..
```
gpg --keyserver subkeys.pgp.net --recv 2BBD133164234534
gpg --export --armor 2BBD133164234534 | sudo apt-key add -
sudo apt-get update

```

---

### Post by x C0MMAND0 x on 2009-01-23
Thanks a ton that worked.  Thank you very much.

---

### Post by blackgr on 2009-01-23
I made this small bash script. it will check you intrepid system for all launchpad sources and will download and install the keys for you!

Who ever wants this for Hardy. Just edit the script and change intrepid to hardy

edit:
you have to run this with sudo

---

### Post by x C0MMAND0 x on 2009-01-23
Thank you very much.

What exactly is the program **Curl** anyways?

---

### Post by blackgr on 2009-01-23
its like wget. but it prints the source code of the page to the default output

---

### Post by onesojourner on 2009-03-16
I am having an issue with this:

```
 gpg --keyserver subkeys.pgp.net --recv 2BBD133164234534
gpg: requesting key 64234534 from hkp server subkeys.pgp.net
gpg: can't open `/home/peter/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

```

```
sudo gpg --keyserver subkeys.pgp.net --recv 2BBD133164234534
gpg: WARNING: unsafe ownership on configuration file `/home/peter/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

```

---

### Post by onesojourner on 2009-03-16
bump

---

### Post by forger on 2009-03-17
don't use sudo and gpg.

Try this perl script:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---


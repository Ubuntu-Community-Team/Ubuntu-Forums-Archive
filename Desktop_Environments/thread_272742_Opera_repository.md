---
title: "Opera repository"
date: 2006-10-06
forum: Desktop Environments
---

### Post by megamaced on 2006-10-06
I've been using the Opera repositories: deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free & deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free for a while now with no problems. But within the last month i get the error: 

```
W: GPG error: http://deb.opera.com unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791

```

Where can I download the key? Is that the problem?

Thanks

---

### Post by Cable on 2006-10-06
In the terminal...
```
[FONT=monospace]
[/FONT]gpg --keyserver subkeys.pgp.net --recv [FONT=monospace][/FONT]6A423791
[FONT=monospace][/FONT]gpg --export --armor 6A423791 | sudo apt-key add -

```

---

### Post by Buffalo Soldier on 2006-10-06
why not use the dapper commercial repo by canonical? 

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by megamaced on 2006-10-07
Thanks guys. Problem solved :)

---

### Post by TheRingmaster on 2006-11-08
that repo doesn't update enough for me (concerning opera)

---

### Post by miguelm on 2008-06-19
me too.

Thanks!

---


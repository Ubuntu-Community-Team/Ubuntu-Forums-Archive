---
title: "netbook remix dell mini 9 ubuntu 8.10 trouble"
date: 2009-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yeayea911 on 2009-03-03
I recently purchased a dell mini 9 with windows xp. I decided to load ubuntu 8.10 on the laptop. Everything works great so far. However, I am also trying to install the netbook remix on it and get the following error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE

All of my other software packages have installed perfectly except for the above stated one.

Kind of frustrating. Please help!

Thanks!

---

### Post by sirebral on 2009-03-04
read this post: [http://ubuntuforums.org/showthread.php?t=1086146](http://ubuntuforums.org/showthread.php?t=1086146)

---

### Post by mtbsoft on 2009-03-04
I had a similar issue yesterday and found the following really useful page via Google... [http://cultoffree.wordpress.com/2009/02/03/w-gpg-errorno_pubkey-60d11217247d1cff-wtf/](http://cultoffree.wordpress.com/2009/02/03/w-gpg-errorno_pubkey-60d11217247d1cff-wtf/)

---

### Post by anjilslaire on 2009-03-04
+1^^^^^^+1

```

gpg --keyserver keyserver.ubuntu.com --recv 3F2A5EE4B796B6FE

```

```

gpg --export --armor 3F2A5EE4B796B6FE | sudo apt-key add -

```

will fix you up nicely

---

### Post by galv on 2009-03-07
> **anjilslaire said:**
> +1^^^^^^+1

```

gpg --keyserver keyserver.ubuntu.com --recv 3F2A5EE4B796B6FE

```

```

gpg --export --armor 3F2A5EE4B796B6FE | sudo apt-key add -

```

will fix you up nicely

It worked for me, thanks :)

---

### Post by lennon2x on 2009-03-09
thanks a lot!it was very helpful!

---

### Post by anton_es on 2009-03-10
he, thanks, had the same problem and google'd for it, your help came up and it solved my problem.

---

### Post by yeayea911 on 2009-03-10
That all worked like a champ! Thanks for all the replies.

So what to do when Ubuntu 9.04 comes out :-)

Thanks,


Anthony

---

### Post by anjilslaire on 2009-03-10
then do the same with the new key if needed ;)

---


---
title: "Software Sources bad behaviour"
date: 2009-06-03
forum: General Help
---

### Post by afrodeity on 2009-06-03
Can anybody understand what is going on here, or suggest a workaround?

```

W: Failed to fetch http://www.salatti.net_repo_dists_hardy-salatti_main_source/dists/hardy/Release.gpg  Could not resolve 'www.salatti.net_repo_dists_hardy-salatti_main_source'

W: Failed to fetch http://www.salatti.net_repo_dists_hardy-salatti_main_source/dists/hardy/main/i18n/Translation-en_ZA.bz2  Could not resolve 'www.salatti.net_repo_dists_hardy-salatti_main_source'

W: Failed to fetch http://launchpad.net/epidermis/+download/dists/hardy/main/binary-amd64/Packages.gz  404 Not Found

W: Failed to fetch http://launchpad.net/epidermis/+download/dists/hardy/main/source/Sources.gz  404 Not Found

W: Failed to fetch http://www.salatti.net/repo/dists/hardy-salatti/main/binary-amd64/Packages.gz  403 Bad Behavior

W: Failed to fetch http://www.salatti.net/repo/dists/hardy-salatti/contrib/binary-amd64/Packages.gz  403 Bad Behavior

W: Failed to fetch http://www.salatti.net/repo/dists/hardy-salatti/non-free/binary-amd64/Packages.gz  403 Bad Behavior

W: Failed to fetch http://www.salatti.net/repo/dists/hardy-salatti/main/source/Sources.gz  403 Bad Behavior

W: Failed to fetch http://www.salatti.net/repo/dists/hardy-salatti/contrib/source/Sources.gz  403 Bad Behavior

W: Failed to fetch http://www.salatti.net/repo/dists/hardy-salatti/non-free/source/Sources.gz  403 Bad Behavior

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

which affects this
```
afrodeity@afrodeity-desktop:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/www.salatti.net_repo_dists_hardy-salatti_main_source_Sources - open (2 No such file or directory)

```


also this problem with public keys?

```

signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7C5BAD1320A0D1DA
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AC9D76CD6E73CA45
```

---

### Post by afrodeity on 2009-06-03
I opened my software sources and edited some of the salatti sources which had hardy-salatti instead of just hardy. They worked. The rest, I had to unselect. Maybe you have the correct address?  As for the gpg issues, still to be resolved.

---

### Post by michy99 on 2009-06-03
I hope this will fix it for you. Replace the word KEY in both lines with the key you want to get (for example, EF4186FE247510BE). Do this for each key.


```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
gpg --export --armor KEY | sudo apt-key add -
```

Then```
sudo apt-get update
```

Keeping my fingers crossed.

---

### Post by afrodeity on 2009-06-03
```
 gpg --keyserver hkp://subkeys.pgp.net --recv-keys 632D16BB0C713DA6
gpg: requesting key 0C713DA6 from hkp server subkeys.pgp.net
gpg: key 0C713DA6: "Launchpad PPA for Fabien Tassin" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

```
afrodeity@afrodeity-desktop:~$ gpg --export --armor KEY | sudo apt-key add -
OK
```

The key appears to be added. But when I run update. I get the the same error message with the same ppas.

```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

```

This makes me inclined to think there is something wrong either with the way I have gpg set up, or there is something wrong with the five ppas listed above?

---

### Post by afrodeity on 2009-06-03
Hahaha, I see what I am doing wrong. I have to enter the second KEY field!

```
Fetched 1547B in 28s (55B/s)
Reading package lists... Done

```

Where others have failed, you suceeded. Thank you so much, this thread is solved, apart from the epidermis ppas.

---

### Post by michy99 on 2009-06-03
When you run the second line, you also have to replace the word KEY with the actual key. Sorry if I didn't make that clear.

Edit: By the time I typed this you had figured it out.

---

### Post by afrodeity on 2009-06-03
I've posted this on my blog. Hope you don't mind. [http://indlovu.wordpress.com](http://indlovu.wordpress.com)

---

### Post by sevoir on 2009-08-07
Adding a Launchpad PPA's key to Ubuntu with Firefox plugin by Sevoir:

[http://www.youtube.com/watch?v=ft-CvWwJ5OU](http://www.youtube.com/watch?v=ft-CvWwJ5OU)

---


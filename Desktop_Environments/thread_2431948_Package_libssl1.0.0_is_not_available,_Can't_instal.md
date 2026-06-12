---
title: "Package libssl1.0.0 is not available, Can't install Eagle 7.7.0. on xubuntu 19.19"
date: 2019-11-24
forum: Desktop Environments
---

### Post by vidar-vidnes on 2019-11-24
Hi

I run xubuntu 19.10 pr. today.
I tried to installl Cadsoft Eagle 7.7.0 but was not able to do so due to missing libssl1.0.0.

```

/tmp/eagle-setup.30959/eagle-7.7.0/bin/eagle: error while loading shared libraries: libssl.so.1.0.0: cannot open shared object file: No such file or directory
```

Tried first to install  libssl1.0.0, but it has no candidate and was indicated to be obsolete. While searching for others with same problem it might seem to be so., 
However, could I add repositories from earlier Ubuntu versions like 18.04 which successfully run Eagle, and install libssl  from earlier xubuntu versions? Would that work?
Or, could i rebuild libssl (or have it built by someone) for 19.10?

breg
Vidar

---

### Post by vidar-vidnes on 2019-11-25
To get the installation to succed I did the following

> cd /usr/lib/x86_64-linux-gnu
sudo ln -s libssl.so.1.1 libssl.so.1.0.0
sudo ln -s libcrypto.so.1.1 libcrypto.so.1.0.0

After this Eagle installs well, but when running application it fails with

> /opt/eagle/bin/eagle: symbol lookup error: /opt/eagle/bin/eagle: undefined symbol: CRYPTO_num_locks



This seems to be an known issue but I found no post that had a solution.
Any suggestions

---

### Post by TheFu on 2019-11-25
Open a bug with the eagle project?

---

### Post by vidar-vidnes on 2019-11-27
> **TheFu said:**
> Open a bug with the eagle project?

Found this solution
[URL="https://gist.github.com/ayjayt/08b8701cc25ac372d7b384cb5a6bd45d"]https://gist.github.com/ayjayt/08b8701cc25ac372d7b384cb5a6bd45d

[/URL]> git clone -b OpenSSL_1_0_2-stable [https://github.com/openssl/openssl](https://github.com/openssl/openssl)
cd openssl
./config shared
make
make test

But instead of using LD_LIBRARY_PATH=$EAGLEHOME/lib/ $EAGLEHOME/eagle as the link suggests,
I just copied the newly built libssl.so.1.0.0 and libcrypto.so.1.0.0 into /lib/x86_64-linux-gnu/ after removing the symlink I created earlier.

The solution was for Eagle version 8.4.1, but it fixed the issues I had for Eagle 7.7.0. aswell

This worked like a charm.

[SIZE=1]*For the record, if you wondered why I don't use newer versions of Eagle like 9.5.0, this is because After 7.7.0 Eagle was bought by Auto-desk and they started to use subscription based licensing. Thus when you decide to not pay anymore you also loose access to previous version. Thats a nogo for me. 7.7.0 is the last real Eagle standing...*[/SIZE]

---


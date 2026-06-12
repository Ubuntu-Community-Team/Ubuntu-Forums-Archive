---
title: "XGL Repository Problem ( http://www.beerorkid.com/compiz/quinn.key.asc)"
date: 2006-07-17
forum: Desktop Environments
---

### Post by blanc11 on 2006-07-17
I installed XGL on my computer this morning and  [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) worked fine.

I am trying to get the gpg key from it now and the connection keeps timing out. Should I wait, or is there another repository that I can use?

---

### Post by mmcmonster on 2006-07-17
These are the relavant lines from my sources.list:
```

# XGL & compiz
# wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
deb http://xgl.compiz.info/ dapper main
deb http://www.beerorkid.com/compiz/ dapper main


```

---

### Post by blanc11 on 2006-07-17
> **mmcmonster said:**
> These are the relavant lines from my sources.list:
```

# XGL & compiz
# wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
deb http://xgl.compiz.info/ dapper main
deb http://www.beerorkid.com/compiz/ dapper main


```


Now I am getting this:

```
Failed to fetch http://www.beerorkid.com/compiz/dists/dapper/Release.gpg  Could not connect to www.beerorkid.com:80 (208.97.133.175), connection timed out
Reading package lists... Done
W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by blanc11 on 2006-07-17
Thanks problem solved!

---


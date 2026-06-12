---
title: "Connecting to wifi router"
date: 2010-04-28
forum: Desktop Environments
---

### Post by anon_private on 2010-04-28
I know that I can connect to my router though the desktop, but can I connect through the command prompt?
 
If so, please can you give details.
 
Please include details for disconnecting.
 
Thanks

---

### Post by iponeverything on 2010-04-28
This might work for you. Grab cnetworkmanager and install it like so:

```

wget http://vidner.net/martin/software/cnetworkmanager/cnetworkmanager-0.21.1.tar.gz
tar -zxvf cnetworkmanager-0.21.1.tar.gz
cd cnetworkmanager-0.21.1
sudo make install

```

connect with:

```
cnetworkmanager --wifi=true

```

disconnect with:

```
cnetworkmanager --wifi=false

```

[http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/)

---

### Post by wojox on 2010-04-28
Nevermind.

---


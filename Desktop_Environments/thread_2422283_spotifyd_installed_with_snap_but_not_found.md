---
title: "spotifyd installed with snap but not found"
date: 2019-07-04
forum: Desktop Environments
---

### Post by holiday on 2019-07-04
19.04/MATE

```

     $ snap list | grep spotifyd
     spotifyd           0.2.3          6     stable    simonpersson 

```
But 

```

     $which spotifyd

```

And 

```

# systemctl enable spotifyd 
Failed to enable unit: Unit file spotifyd.service does not exist

```

And I find nothing in the menus.

Is there a trick I'm missing, or is there an error?

---

### Post by Frogs Hair on 2019-07-04
Do you have a spotify premium account?

[https://github.com/Spotifyd/spotifyd](https://github.com/Spotifyd/spotifyd)

---

### Post by holiday on 2019-07-04
Yes.

---

### Post by holiday on 2019-07-05
Fixed with :

```

systemctl enable snap.spotifyd.spotifyd.service
systemctl start snap.spotifyd.spotifyd.service

```

---


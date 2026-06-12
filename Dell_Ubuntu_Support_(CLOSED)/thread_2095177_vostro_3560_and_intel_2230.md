---
title: "vostro 3560 and intel 2230"
date: 2012-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chrabja on 2012-12-16
Hi

I have Dell Vostro 3560 with intel 2230 wifi.
I have problem with connection when i am working on battery, on ac everything is ok.
When i use notebook on battery, ping to my gateway rises to 500-800ms. When i plug in ac power, ping is 1-2 ms. I try load module with 11n_disable=1 or bt_coex_active=N, but that didn't work.

---

### Post by mikewhatever on 2012-12-19
It could be related to wifi power managment turned on when on battery. Check if it's on, by running iwconfig, and if it is, run
```
sudo iwconfig eth1 power off
```

...assuming eth1 is the wireless interface.

---


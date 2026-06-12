---
title: "More Madwifi Make Errors"
date: 2005-12-20
forum: General Help
---

### Post by thezerogroup on 2005-12-20
I am attempting to install the latest madwfi-ng drivers and am getting tons of errors.

```

root@kaya:/usr/src/madwifi-ng# make
Checking requirements... ok.
Checking kernel configuration... ok.
mkdir -p ./symbols
for i in ./ath_hal ./net80211 ath_rate/sample ./ath ./tools ; do \
        make -C $i || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi-ng/ath_hal'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi-ng/ath_hal MODVERDIR=/usr/src/madwifi-ng/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi-ng/ath_hal/.hal.o.cmd for /usr/src/madwifi-ng/ath_hal/hal.o
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/usr/src/madwifi-ng/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-ng/net80211'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi-ng/net80211 MODVERDIR=/usr/src/madwifi-ng/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/madwifi-ng/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi-ng/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/usr/src/madwifi-ng/net80211/if_media.o] Error 1
make[2]: *** [_module_/usr/src/madwifi-ng/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/madwifi-ng/net80211'
make: *** [all] Error 1

```

Then I try make install, just to give it a shot and get

```

root@kaya:/usr/src/madwifi-ng# make install
sh scripts/find-madwifi-modules.sh /lib/modules/2.6.12-10-386

WARNING:
It seems that there are modules left from previous MadWifi installations.
You should consider removing them before you continue, or else you might
experience problems during operation. Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ?
r
for i in ./ath_hal ./net80211 ath_rate/sample ./ath ./tools ; do \
        make -C $i install || exit 1; \
done
make[1]: Entering directory `/usr/src/madwifi-ng/ath_hal'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi-ng/ath_hal MODVERDIR=/usr/src/madwifi-ng/ath_hal/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /usr/src/madwifi-ng/ath_hal/.hal.o.cmd for /usr/src/madwifi-ng/ath_hal/hal.o
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
test -d //lib/modules/2.6.12-10-386/net || mkdir -p //lib/modules/2.6.12-10-386/net
strip -S ath_hal.ko
cp ath_hal.ko //lib/modules/2.6.12-10-386/net
make[1]: Leaving directory `/usr/src/madwifi-ng/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-ng/net80211'
make -C /usr/src/linux-headers-2.6.12-10-386 SUBDIRS=/usr/src/madwifi-ng/net80211 MODVERDIR=/usr/src/madwifi-ng/net80211/../symbols modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /usr/src/madwifi-ng/net80211/if_media.o
cc1: warnings being treated as errors
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /usr/src/madwifi-ng/net80211/if_media.c:60:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
make[3]: *** [/usr/src/madwifi-ng/net80211/if_media.o] Error 1
make[2]: *** [_module_/usr/src/madwifi-ng/net80211] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/madwifi-ng/net80211'
make: *** [install] Error 1

```

---

### Post by thezerogroup on 2005-12-20
bump

---

### Post by thezerogroup on 2005-12-22
bump again!

---

### Post by hajk on 2005-12-22
Bump, bump, bump... May I ask why you are trying to compile the madwifi driver when it is already provided in Breezy? All you have to do is install the linux-restricted-modules package for your kernel -- it's not installed by default -- and it contains the madwifi driver. No need to compile it from source...

---


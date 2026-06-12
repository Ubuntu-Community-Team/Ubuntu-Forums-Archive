---
title: "installing madwifi"
date: 2009-04-22
forum: General Help
---

### Post by nordmar on 2009-04-22
Hi,

I used [this doc]("https://help.ubuntu.com/community/WifiDocs/Driver/Madwifi") to help me install madwifi on my comp. But there are some problems - when I do *make*, in the end it returns

```

make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'            
make -C ./tools all || exit 1                                                   
make[1]: Entering directory `/usr/src/madwifi-ng/tools'                         
for d in ath_info; do \
                make -C $d || exit 1; \
        done
make[2]: Entering directory `/usr/src/madwifi-ng/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
ath_info.c: In function 'main':
ath_info.c:2847: warning: ignoring return value of 'fwrite', declared with attribute warn_unused_result
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/usr/src/madwifi-ng/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../ath_hal -I.. -I../ath  athstats.c
athstats.c: In function 'main':
athstats.c:288: warning: format not a string literal and no format arguments
athstats.c:290: warning: format not a string literal and no format arguments
athstats.c:310: warning: format not a string literal and no format arguments
athstats.c:312: warning: format not a string literal and no format arguments
athstats.c:347: warning: format not a string literal and no format arguments
gcc -o 80211stats -g -O2 -Wall -I. -I../ath_hal -I..  80211stats.c
80211stats.c: In function 'main':
80211stats.c:287: warning: format not a string literal and no format arguments
gcc -o athkey -g -O2 -Wall -I. -I../ath_hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../ath_hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../ath_hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../ath_hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../ath_hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../ath_hal -I..  wlanconfig.c
wlanconfig.c: In function 'list_keys':
wlanconfig.c:779: warning: ignoring return value of 'system', declared with attribute warn_unused_result
wlanconfig.c: In function 'ieee80211_status':
wlanconfig.c:895: warning: ignoring return value of 'system', declared with attribute warn_unused_result
gcc -o wpakey -g -O2 -Wall -I. -I../ath_hal -I..  wpakey.c
make[1]: Leaving directory `/usr/src/madwifi-ng/tools'

```

ant after *make install* when I type *wlanconfig* it gives me an i/o error. 

Then wifi works until I reboot or suspend my comp. What should I do? Please help me

(i386)

---

### Post by nordmar on 2009-04-23
No help?

---

### Post by thewolfman on 2009-04-23
> **nordmar said:**
> No help?

Hi,

there is plenty of help but you must tell everyone what kind of wifi device you want to use and maybe people have a better insight into what you want to do.

Why are you installing madwifi?, is it absolutely necessary for your needs?,
what type of wifi device is it you are installing.

For example, broadcom, atheros etc.

So fill in the blanks and then maybe with the info someone can HELP you!.

Regards thewolfman

---

### Post by nordmar on 2009-04-23
actually it was atheros ar5007 with which most people have great problems.

Anyways I blacklisted ath5k and added ath_pci into modules. After the reboot it then worked.

But thank you for you effort ;)

---


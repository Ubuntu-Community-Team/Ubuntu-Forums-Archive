---
title: "problem with fiiregl v3200 and winex / cedega"
date: 2006-06-30
forum: Desktop Environments
---

### Post by holr on 2006-06-30
Hi, i have a strange problem when using either normal wine, or cedga with a t43p laptop (has an ati firegl v3200 graphics card), if i use the standard radeon driver with kubuntu dapper, i can get cedega / wine running fine with games that do not need 3d accelleration. However, as soon as i install and enable the fglrx driver, whenever I try to load a game, the initial window pops up, but just the border of it (so i can drag it around my desktop) but the contents, nothing. Its like the games freeze as soon as I load them up!

Am i missing a special setting in my xorg.conf especially for firegl based cards? The weird thing is, 3d is working, quake 4 native works fine, but cedega doesnt want to with the ati drivers, only with the generic radeon ones.

thanks for any help!

---

### Post by holr on 2006-07-01
any ideas? can some others who have had better luck with an ati card and cedega / wine post their xorg.conf stuff?

---

### Post by holr on 2006-09-04
ok, found the answer, in the device section of your xorg.conf file, add the following line:

Option "UseFastTLS" "2"

This used to be configured when the older ati binary driver used fglrxconfig to configure itself. Now that we use aticonfig, I havent found a method to do this, other than the manual way.

This option does not effect my native games (such as quake 4) but does make cedega / wine work nice. Well, as nice as you can with an ati card! :o

---


---
title: "Is there PPA for Latest Wesnoth? 1.7.14 - 1.8-beta7"
date: 2010-03-14
forum: Gaming &amp; Leisure
---

### Post by Kdar on 2010-03-14
Just like in title...

Is there PPA for unstable version of Wesnoth? like version 1.7.14?

---

### Post by Kdar on 2010-03-14
Hello? :)

---

### Post by Tropcon on 2010-03-19
I found one here:

[https://launchpad.net/~stikonas/+archive/ppa]("https://launchpad.net/~stikonas/+archive/ppa")

It has 1.7.14, but the latest version now is actually 1.7.15 - 1.8 rc1. I think the ppa ought to updated soon enough, though.

I could never understand how to work with the compiling programs that Wesnoth uses.

---

### Post by Perfect Storm on 2010-03-19
It's pretty simple to compile it: [http://gwos.org/doku.php/guides:64bit:battle_for_wesnoth](http://gwos.org/doku.php/guides:64bit:battle_for_wesnoth)

---

### Post by Kdar on 2010-03-20
thanks. I will try it.
I had some problems with some libraries before, but maybe it will work after that link you gave me.


By the way.. Anyone know what is new in Wesnoth 1.8-beta?

---

### Post by Tropcon on 2010-03-20
Just have a look at the [changelog.]("http://svn.gna.org/viewcvs/*checkout*/wesnoth/trunk/players_changelog")

______________________


Version 1.7.15-1.8rc1:
 * AI:
   * Set RCA AI to be the default AI for single-player campaigns.

 * Language and i18n:
   * Updated translations: Chinese (Traditional), Czech, German, Hungarian,
     Japanese, Serbian.

 * Multiplayer:
   * Fix bug #15541: fix OOS on [unit] tag generating different
     traits because of usage of local RNG instead of MP RNG.
   * Fix bug #15560 for Dark Forecast: fix OOS in Dark Forecast caused by
     unit advancement not properly synced across the network.

 * Music and sound effects:
   * Added new music track, "Weight of Revenge" by Doug Kaufman

 * User interface:
   * Avoid the scrollbar on the entire MP lobby when possible.
_____________________

By the way, thanks for the howto, Artificial Intelligence. That makes it look much easier than the wesnoth readme does. :)

---


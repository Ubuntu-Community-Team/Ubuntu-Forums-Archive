---
title: "Quake live not working in ubuntu 9.10 x64-bit"
date: 2010-02-01
forum: Gaming &amp; Leisure
---

### Post by toupeiro on 2010-02-01
I decided to jump back into quake-live the other day and I haven't played since going to 9.10.  I've recently learned that quake-live gets an error "core entry point not found" every time I try to play.  This definitely work with 9.04 x64-bit on the same machine (core i7).  Anyone else experience this and find a workaround?

---

### Post by toupeiro on 2010-02-02
*hopeful bump*

---

### Post by toupeiro on 2010-02-05
*less than hopeful final bump* :(

This is starting to look like a genuine fail.  I've successfully proven this is ubuntu related, I cannot reproduce this issue in SuSE on the same hardware.  Nobody?

---

### Post by Asraniel on 2010-02-06
sorry, only playing quake live in 32bit kubuntu. but at least i know now that installing 64bit is still a bad idea

---

### Post by Bölvaður on 2010-02-06
9.10 64 bit.

it works.
it's probably the browser.


the only thing I can complain about is that it feels like there is fps lag even though there probably isnt.

---

### Post by benmoran on 2010-02-06
I can also confirm that it works on AMD64 under 9.10.

---

### Post by toupeiro on 2010-02-07
> **Bölvaður said:**
> 9.10 64 bit.

it works.
it's probably the browser.


the only thing I can complain about is that it feels like there is fps lag even though there probably isnt.

Which version of firefox are you using?

---

### Post by toupeiro on 2010-02-07
> **Asraniel said:**
> sorry, only playing quake live in 32bit kubuntu. but at least i know now that installing 64bit is still a bad idea

The common denominator is not 64-bit.  I was playing this in 9.04 x64 bit and have been running x64-bit since 6.10.  When I said it was working in SuSE, that was also x64-bit.

---

### Post by toupeiro on 2010-02-07
Seems I just fixed this issue.  I completely uninstalled AppArmor from my machine and its playing just fine after that.  Hopefully someone involved in ubuntu upstream reads this and will take a look at the apparmor install in ubuntu.

Note, I had to **ununstall** apparmor to correct this.  Disabling the firefox apparmor profile did not work, which was reported to work in older versions of ubuntu on Quake Lives tech support forums.

---

### Post by jeditalian on 2010-07-23
well i dont have apparmor (unless it comes in ubuntu by default) and on 9.10 64 bit with a amd 64 4000+ quakelive played awesome and performed better than it ever did in windows. in windows i would have major lag on space maps. anyway, i am in the same situation you were, i haven't played quakelive in a while, and i upgraded ubuntu.. using 10.04, once i try to join a game, my mouse disappears and moving it doesnt make it come out of the quakelive window, its just gone.. then it acts like its about to get me to where i click join, or pick teams and join the action, but then firefox just closes with no messages.  so im going to download 10.04 64 bit onto cd or use the 32 bit cd i have, and do a fresh installation instead of the upgrade, then see if i still can't play.

---


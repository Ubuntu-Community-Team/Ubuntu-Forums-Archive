---
title: "[SOLVED] Compiz-Fusion ABI version Issue"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by indieboy445 on 2007-08-20
This is a new version of an old problem (or at least I think it is). I couldn't get any of the suggested fixes to work for me, hopefully someone can help.

Compiz fusion had been working, however, since this evening when I try to start it I get the following:

```
brad@DeepRed:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070815
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
```


I tried a complete removal and re-install of compiz with no luck.

I'm running Gutsy on this computer, so install/updates come from the Ubuntu repositories.

Any suggestions would be appreciated.

---

### Post by XTREEM|RAGE on 2007-08-21
I'm sorry i dont be any help, but i have the same problem:
I did an update with the automaic update function and that borked compiz ffs
i have [searched](http://www.google.nl/search?q=can't+load+plugin+ccp&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:nl:official&client=firefox-a) but the fixes i tried didnt worked. I hope they just update it so it will be compatible, but if not. How can we complet remove compiz?

---

### Post by indieboy445 on 2007-08-21
I still haven't found a fix yet, but here's how you can purge compiz:

```
sudo apt-get --purge remove compiz* libcompizconfig*
```

Don't miss the little *'s there.

I'm going to try installing it off of a different repo (if I can find one). I'll let you know if that works.

---

### Post by XTREEM|RAGE on 2007-08-22
> **indieboy445 said:**
> I still haven't found a fix yet, but here's how you can purge compiz:

```
sudo apt-get --purge remove compiz* libcompizconfig*
```

Don't miss the little *'s there.

I'm going to try installing it off of a different repo (if I can find one). I'll let you know if that works.


That would be nice, i will  try to remove it and then try to reinstall it!

---

### Post by Colonel Kilkenny on 2007-08-22
I had same problem. I manually deleted all compiz lib*.so-files from my computer because there were multiple places where files like libexpo.so was found. I guess they should at one place (for me it's /usr/local/lib/compiz). Anyway I deleted all those plugins and used installation script to install all again. Now everything is pretty much working.

---

### Post by XTREEM|RAGE on 2007-08-22
After reading this page, [http://ubuntuforums.org/showthread.php?t=495549](http://ubuntuforums.org/showthread.php?t=495549) , i think it's just an update issue? Because they all had a version mismatch but when the update was avail, the problem was fixed :x

---

### Post by indieboy445 on 2007-08-22
Yes, its definatly an update issue. In may case it came about because I had some exta repositories added that also happened to have compiz in them. One repository got updated while the other didn't, leading to the problem. I just removed all but the standard repos and re-installed everything. Now I'm back to normal.

---

### Post by umanzor on 2007-08-22
Well, I'm having this problem right now, no way to start compiz.

---

### Post by XTREEM|RAGE on 2007-08-22
> **indieboy445 said:**
> Yes, its definatly an update issue. In may case it came about because I had some exta repositories added that also happened to have compiz in them. One repository got updated while the other didn't, leading to the problem. I just removed all but the standard repos and re-installed everything. Now I'm back to normal.

ok which howto did you follow to install compiz?
because i have a lot of repostory of compiz, then i just delete them and follow the 1 you fixed the prob :D. Or can u give us the repository you are using?

> **umanzor said:**
> Well, I'm having this problem right now, no way to start compiz.
Did you als update it? Because a lot of people having this after the update. Remove it and reinstall it and try to add right repository (if indieboy445 gives them ;D)

---

### Post by XTREEM|RAGE on 2007-08-22
ok i got it fixed with the help of this page: [http://ubuntuforums.org/showthread.php?t=488385&page=17](http://ubuntuforums.org/showthread.php?t=488385&page=17) like we all said it's an update problem. Follow the instruction in there and it should work again! And remove the other compiz repository and use the 1 that's in the little how to ;)

sorry for my poor english >_<

---

### Post by indieboy445 on 2007-08-23
Sorry, I really should have mentioned with repo I meant. I'm using Gutsy on this computer, so compiz is in the standard Ubuntu repository.

But, if you're using in Feisty, XTREEM|RAGE is right, Treviño's repository should work.

---

### Post by umanzor on 2007-08-23
Something is not right. I apt-get remove --purge 'ed  compiz* and delete the compizsettings folder in my home folder. I reinstalled from Treviño's Repository but it doesn't work. I still get the same error.

---

### Post by XTREEM|RAGE on 2007-08-25
> **umanzor said:**
> Something is not right. I apt-get remove --purge 'ed  compiz* and delete the compizsettings folder in my home folder. I reinstalled from Treviño's Repository but it doesn't work. I still get the same error.

then i think you still had some compiz files left.

```
sudo apt-get --purge remove compiz* libcompizconfig*
```

You did this with the * etc?

edit
[http://ubuntuforums.org/showthread.php?t=533201](http://ubuntuforums.org/showthread.php?t=533201)

---


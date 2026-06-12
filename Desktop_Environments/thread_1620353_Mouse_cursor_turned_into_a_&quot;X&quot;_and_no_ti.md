---
title: "Mouse cursor turned into a &quot;X&quot; and no title bar on window"
date: 2010-11-13
forum: Desktop Environments
---

### Post by Kenchinito on 2010-11-13
Hello, 

I just got into big troubles, or at least that's what i think, hopefully not. Well, I've been using  ubuntu for a few months now and i love it. today the mouse cursor turned into a X and the windows doesn't have title bars, i can't swtich between apps using the alt+tab method, the show desktop button doesn't work, cannot minimize applications. long story short, i can't do anything.

Wish i could provide anymore clues, but i have no idea how to diagnose. I'm a decent windows user, but i have no experience on ubuntu whatsoever, so please, any help will be greatly apreciated.

---

### Post by Kenchinito on 2010-11-13
Ok, if there was anyone who entered this post in hope for a solution, I managed to fix mine.
This is what i did:
since the desktop was close to non-workable, i decided to change de X server to metacity, because compiz was apparently messed up. 

so type in console "metacity --replace"  

After that you should have a workable desktop. afterwards i went to synaptic and checked the status of compiz, guess wut? it was totally uninstalled!! maybe i delete it by mistake on some uninstalls procedures. So just reinstall compiz and you should have it working back again.

---

### Post by Fospherous on 2010-11-20
I had this problem too. Just came on one evening and I had the exact same problem. What I did was similar to this, but much easier. I simply uninstalled Compiz, then reinstalled it. I then rebooted and everything was back to normal. :)

---


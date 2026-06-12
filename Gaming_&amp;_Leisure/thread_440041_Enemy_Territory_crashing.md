---
title: "Enemy Territory crashing"
date: 2007-05-11
forum: Gaming &amp; Leisure
---

### Post by Memory.Dump on 2007-05-11
so I got Enemy territory installed but now when I join a server after connecting and awaiting gamestate for about 5 seconds it crashes tosses me out and has a huge resolution, no msg no warning, no reason, I do have my video drivers all installed and configured and what not

---

### Post by lakersforce on 2007-05-11
Try to run it from a terminal. You should then get a error message.

---

### Post by Stephen Howard on 2007-05-11
Bring up a terminal and run the program from there (executable is 'et').  At least that way you can get some more info.

There's also a [bug that looks close to your problem]("http://www.rtcw.jolt.co.uk/content/faq/enemyterritory_faq.html#ET_serverlistcrash"), might be worth trying the fix.  

PS:  its working fine on my Feisty - indeed its always worked without a hitch.

---

### Post by Memory.Dump on 2007-05-11
ok will try running it from ternal and seeing what happens

---

### Post by Memory.Dump on 2007-05-11
ok so I tried running it from the terminal and I didn't have keyboard or mouse response at all in the game...am I missing something tin the terminal command?

just typed out et (no flags)

---

### Post by lakersforce on 2007-05-11
ok, that sounds wierd.

---

### Post by houstonbofh on 2007-05-11
How did you install it, and what version?

---

### Post by Memory.Dump on 2007-05-11
umm...version # is 1.4 I think soemthing like that I got it straight from the enemy-territory site 

and it was a .run file so I did sh $installname.run

---

### Post by Memory.Dump on 2007-05-11
it seems to mostly crash when its trying to download stuff form what I can see

---

### Post by pragmatine on 2007-05-11
Does your .etwolf directory have the correct permissions? The same thing was happening to me, since after I installed et I ran it first time as root without realising it. Try a:

sudo rm -rf ~/.etwolf

And see how you go after that.

---

### Post by houstonbofh on 2007-05-13
I am on ver 2.6, so I hope you remember wrong. :)  A good howto is here...
[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)
The TC:E install there is not totally correct, however.

---


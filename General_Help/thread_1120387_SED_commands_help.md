---
title: "SED commands help"
date: 2009-04-08
forum: General Help
---

### Post by brazemcee on 2009-04-08
Hi there!
I got a huge file with html strings (it's a babylon GLS file). Somehow I managed to convert new babylon glossaries into old babylon glossaries...
It gives me an old GLS file which can be imported with Babylon Builder (an old version, too) and then I can compile it AND FINALLY convert it to StarDict. Anyway, since it was converted from the new version... it contains a lot of html strings that should erased.

I wanna replace this:
<a href="('cd68');" style="color:red;text-decoration:underline;"

NOTE: the expression "cd68" is constantly changed all the time... so I have cd68, cd69, cd3043, cd21111

with this:
<style="color:red;text-decoration:underline;"

Note: the GLS file fails to compile since there's no 'cd68' stuff.

Somebody told me it can be done with SED... but how?
Can somebody give me a hand?
:D

Thankssssss.

---

### Post by ibuclaw on 2009-04-08
Backup the file
```
cp **file.html** backup.html
```

Then run
```
sed -i 's/a\s*href="(.*);"\s*//g' **file.html**
```

Replace all file references with the actual filenames, of course :)

Regards
Iain

---

### Post by brazemcee on 2009-04-08
OH MY GOD!

How can that happen??? you guys are SO FAST!

I'm gonna try it right now!

---

### Post by brazemcee on 2009-04-08
Testing...

THANK YOU SO MUCH!

---


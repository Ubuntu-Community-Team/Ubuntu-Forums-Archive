---
title: "America's Army: SF Not Working!"
date: 2006-04-09
forum: Gaming &amp; Leisure
---

### Post by jon_benge on 2006-04-09
I downloaded Amercia's army the other day - all 780MBs of it! I installed it by going to the terminal and typing ./<filename>. The installation went OK and a shortcut has appeared under Applications > Other > Armyops.

When I click on this shortcut nothing happens! Absolutely nothing - not even a squeek. Whats gone wrong? What am I not doing right? Do I need to install some additional software?

My computer specs are:

Ubuntu Breezy badger
Pentium 3 1GHz
384MB RAM
Geforce2 Ultra 64MB (using the nVidia Legacy drivers)

---

### Post by Kurt` on 2006-04-09
Try launching the program from a terminal, it'll display what is happening/going wrong

---

### Post by jon_benge on 2006-04-09
Thanks for the quick response.

This is the error message:

armyops
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by jon_benge on 2006-04-09
I've cracked it :D 

If anyone receives the same error as I did, simply open up a terminal and type:

```
sudo apt-get install libstdc++5
```

Thanks for your help Kurt!

---

### Post by ericesque on 2006-04-10
What version of AA are you running?   How well does it run?

---

### Post by Kebekoi on 2006-04-10
What a crack! :rolleyes:

Well good job anyway ^o^v

---

### Post by TheRealPhate on 2006-04-12
Hi I had the same problum with AA and the libstdc fixed it, my only problum is now it is choppy, I haev a Dell Inspirion 6000 1.5Ghz 512mb Ram 40gb HD, I finally got the sound working any one know how to get it running smooth, sry this is my first week of ever running Linux or Ubuntu

---

### Post by Perfect Storm on 2006-04-13
Did you setup your graphic card?

---

### Post by TheRealPhate on 2006-04-13
oops posted twice

---

### Post by TheRealPhate on 2006-04-13
[QUOTE=Artificial Intelligence]Did you setup your graphic card?[/QUOTE]
I dont think so, I installed automatix and enemy territory and it seems to run a little smoother but I have no idea how to set up the graphics card in Ubuntu. Would anyone be able to help me with that, it is a Dell inspirion 6000, 1.5Ghz 512mb ram 40gb HD intel wireless pro card, I believe it's a Intel Graphics Media Accelerator 900 GM but am not sure. all help is very much apreciated

---

### Post by Perfect Storm on 2006-04-13
[http://ubuntuforums.org/showthread.php?t=75393&highlight=card](http://ubuntuforums.org/showthread.php?t=75393&highlight=card)

---


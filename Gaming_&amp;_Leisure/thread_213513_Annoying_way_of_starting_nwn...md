---
title: "Annoying way of starting nwn.."
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by PriceChild on 2006-07-11
Hey there, i've had nwn running well for ages.

However, there's an annoying little routine that i am forced through every time.

I have to cd to /usr/local/games/neverwinter before being able to type nwn

If i don't do this, then it complains about nwmain not being found. (because its looking in /usr/local/bin where my executable is placed.

What can i do to sort this out? I'm sure i must be able to have a little line of code to move directory in the terminal before executing nwn. But simply cd in a script won't work will it? :)

Thanks for any help, Pricey.

---

### Post by vem0m on 2006-07-11
creat an icon that loads '/ust/local/games/neverwinter/nwn' and if that don't work tell it to start in the directory /usr/local/bin hope this helps :)

---

### Post by mazirian on 2006-07-11
How about aliasing nwn or run-nwn or whatever you like to something like "cd /ust/local/games/neverwinter && /usr/local/games/neverwinter/nwn"  See man alias.

Or make a wrapper script in bash that cds to the directory you need before running the script, and then make a launcher for that script.

Just some thoughts.

---

### Post by PriceChild on 2006-07-11
Wahey sorted!!! :)

Had a bit of a sily problem... acciadently looped the script on itself so it spawned hundreds of processes :P

But all is good now with a 
```
cd /usr/local/games/neverwinter && nonXgl /usr/local/games/neverwinter/nwn
```
Thanks for help :)

---


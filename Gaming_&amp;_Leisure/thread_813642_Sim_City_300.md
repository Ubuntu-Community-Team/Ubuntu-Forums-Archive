---
title: "Sim City 300"
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by Vrekk on 2008-05-31
Hey i got the Sim City 300 Ultiamte Linux verion disc the other day.  I installed it but now i cant get it to run, can anyone help?

---

### Post by Sam Lars on 2008-05-31
Is it not in the Applications menu?
Do you know where it installed to?

---

### Post by Vrekk on 2008-05-31
Nope it is not in the application menu, and i dont know where it installed to, i will look for it though

---

### Post by atomkarinca on 2008-05-31
> **Vrekk said:**
> Nope it is not in the application menu, and i dont know where it installed to, i will look for it though

Open up a terminal (Applications > Accessories > Terminal) and type:

```
which sc3u
```

this should print out where the executable is. However I didn't understand your problem. Do you not know how to launch the game or are you having problems launching the game? Type in the terminal

```
sc3u
```

and if there's a problem just copy and paste here the output.

---

### Post by doorknob60 on 2008-06-01
More complicated than that, trust me :P [http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/](http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/) It's for edgy, but it works fine in gusty too, and I'll assume it works in hardy. Not that you first have to follow the guide on how to get it to run in dapper (linked in the 2nd paragraph).

---

### Post by Vrekk on 2008-06-03
Hey sorry for the delay.  How do i patch the game, i cant figure out how and runnin ```
sh sc3u-2.0a-x86.run -keep
``` dosnt work. It says something about ```
Can not open "+6" no such file of directory
``` and i dont know where the sc3u-2.0a-x86.run thing should be located when running it.

---

### Post by FoGia on 2008-06-16
Same problem here, can someone help? this patch is mandatory to run the game!

A few links to make the game work:
[http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)
[http://bashu.wordpress.com/2007/02/17/simcity-3000-on-ubuntu-dapper/](http://bashu.wordpress.com/2007/02/17/simcity-3000-on-ubuntu-dapper/)
[http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/](http://bashu.wordpress.com/2007/04/15/simcity-3000-on-ubuntu-edgy/)

---

### Post by TheIdiotThatIsMe on 2008-07-26
Fogia:

In the link [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games) under SimCity 3000 if you read carefully you'll find instructions about "patching the patch". This is absolutely necessary in order to get the patch to work. This is the step I kept missing over and over again. Now I have the game up and running great :)

---

### Post by donmatas on 2010-02-22
> **Vrekk said:**
> Hey sorry for the delay.  How do i patch the game, i cant figure out how and runnin ```
sh sc3u-2.0a-x86.run -keep
``` dosnt work. It says something about ```
Can not open "+6" no such file of directory
``` and i dont know where the sc3u-2.0a-x86.run thing should be located when running it.

anyone knows where is the patch?

saludos
DM

---

### Post by donmatas on 2010-02-24
> **TheIdiotThatIsMe said:**
> Fogia:

In the link [http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games) under SimCity 3000 if you read carefully you'll find instructions about "patching the patch". This is absolutely necessary in order to get the patch to work. This is the step I kept missing over and over again. Now I have the game up and running great :)

the link seems to be broken...help please!

saludos
DM

---


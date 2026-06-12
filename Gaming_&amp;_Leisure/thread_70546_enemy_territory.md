---
title: "enemy territory"
date: 2005-09-30
forum: Gaming &amp; Leisure
---

### Post by aran384 on 2005-09-30
every tme i connect to a punkbusters server i get no cdkey set or something like that and banned for 5mins 

how do i fix this ??? ...

---

### Post by geekchic9 on 2005-09-30
May I ask a stupid question? Are you using your Enemy Territory CD when you connect to the punkbusters server? Is its key registered? Have you updated to the latest release? I don't play ET so I may have no idea what I'm talking about, though.

---

### Post by aran384 on 2005-09-30
ET is a free game that you download....

so what am trying to say is how can i have this error ???

i never had it on windows...

---

### Post by DancingSun on 2005-09-30
Hmm, I didn't have this problem when I installed ET on Ubuntu...

Did you update ET to the latest version with all the patches?

---

### Post by aran384 on 2005-10-01
i downloaded the lastst one i think....

what is the latest version atm?

---

### Post by DancingSun on 2005-10-01
2.60

---

### Post by websavages on 2005-10-01
Have a look at the punkbuster [FAQ]("http://www.punkbuster.com/index.php?page=faq-et.php") for ET

Cheers ws

---

### Post by Hobgoblin on 2005-10-01
There have been a few problems with the Punkbuster servers lately, I would guess that is your problem and it will go away as soon as Evenbalance fix their servers.

Even though ET is a free game it still requires a CDkey.  The first time you connect to a server you should get a CDkey issued (without you knowing about it).  You'll find it in a file called etkey.

---

### Post by bob_c_b on 2005-10-02
I have found a number of ET/PB issues fixed by remember to change the owner of the ./etwolf directory under your home directory...
```
sudo chown username:groupname .etwolf
```
I believe that Ubuntu creates a groupname identical to your username during set up (someone correct me if I am wrong). Try that and see if it helps, I had all kinds of issues with ET until I did that.

---


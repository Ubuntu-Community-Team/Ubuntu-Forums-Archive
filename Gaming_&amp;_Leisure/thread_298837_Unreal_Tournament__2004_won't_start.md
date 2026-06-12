---
title: "Unreal Tournament  2004 won't start"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by Möller on 2006-11-13
Ok, I installed UT2004, got it up and running, and all of a sudden it wont start. I get this message when i try to run it:

```
Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 149]

History: 

Exiting due to error
```

Can someone tell me why?

---

### Post by Hemmer on 2006-11-13
> **Möller said:**
> Ok, I installed UT2004, got it up and running, and all of a sudden it wont start. I get this message when i try to run it:

```
Assertion failed: sizeof(*this)==GetClass()->GetPropertiesSize() [File:UnGame.cpp] [Line: 149]

History: 

Exiting due to error
```

Can someone tell me why?

Have you tried running it as root?

```
sudo ut2004
```

if that works, then you can either run it as root each time you play or you will need to re-install the game as root:

```
sudo sh /cdrom/linux-installer.sh
```

---

### Post by holylucifer on 2006-11-28
well my ut 2004 starts and then crashes and i get , [http://img140.imageshack.us/img140/9407/screenshotcz6.png](http://img140.imageshack.us/img140/9407/screenshotcz6.png)

---

### Post by MyKal on 2008-07-18
i am having the same problem as Möller and i have tried running it as root and it does the same thing

i really hope someone has an answer to this one you see my family (me my wife and our ten year old son) have family night lan parties (geeky as hell right?) and this is putting quite a cramp on family game time :D haha

---

### Post by evets25 on 2008-07-18
holylucifer, your problem looks to be different than moller's. Mostly likely, you don't have the nvidia (or ati, or intel) driver installed. 

Mollier, I have no ideas about that crash, try reinstalling ut2004. I know I've gotten it to work before, so keep trying. Also, since ut2004 is just a game, there should never *ever* be a need to run it as root. Ever. If it's a permissions problem (which it's clearly not), then you would change the permissions on the files it can't access, rather than running it as root. Running regular programs like this as root is a *bad* habit to get in to, so don't do it!

---

### Post by Brebs on 2008-07-19
Try resetting your ut2004 settings:
```
mv ~/.ut2004{,-bak}
```

---

### Post by MyKal on 2008-07-20
> **Brebs said:**
> Try resetting your ut2004 settings:
```
mv ~/.ut2004{,-bak}
```

OH MY GOD IT WORKED!!!

and it was so simple that i am shamed

but seriously thanks so much brebs your a lifesaver 

Möller, i hope this works for you as well maybe i will see you in the tournament sometime

---

### Post by Mercerism on 2008-07-20
Hm, did not work for me, having the same problem as Möller.
First i installed ut2004 and applied the latest patch, but couldn't get it to run, then i reinstalled it, changed some permissions and it worked, although it showed me that i had to install the latest patch to play online, so i applied the patch again and now it is screwed.
I might just reinstall it again and make sure to apply the patch before running it the first time.

---


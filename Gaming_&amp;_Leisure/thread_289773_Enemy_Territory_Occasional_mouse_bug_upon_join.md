---
title: "Enemy Territory: Occasional mouse bug upon join"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by pbaehr on 2006-10-31
I've searched high and low with no avail for an answer to this problem.

When I start Enemy Territory the mouse works fine until I join a game. Then (and not always) as soon as I move the mouse the littlest bit the camera focuses straight down and any movement of the mouse causes the camera to spin wildly. The mouse no longer functions for any menus, either.

If I use the keyboard I can exit the game at which point the mouse starts behaving itself again. Then I can restart the game and cross my fingers that it won't happen again. Sometimes it will take several tries before it works properly.

I am running the x86 version of Ubuntu Edgy on AMD64 with the latest (9625) version of the nvidia drivers. This was a problem for me with the older drivers and Dapper, as well, though.

Has anyone else ever encountered this? Any thoughts to a solution? Anything else I can tell you about my setup that would help?

Thanks!

---

### Post by chavo on 2006-10-31
I had this happen to me and I ended up restoring all of my configs to default by deleting all of the etconfig.cfg files within my .etwolf directory. Then when I started up again I exec my autoexec.cfg file to get my settings back.

I later discovered the command /cvar_reset, type it in the console to restore all settings to default, then type /exec autoexec to restore your settings. This should work also, but I haven't used it to try to fix this issue. 

You can backup your .etwolf directory or just the etconfig.cfg files first just in case.

---

### Post by pbaehr on 2006-10-31
I knew I couldn't be the only person that had that problem.

Thanks for the tip. I'll give it a shot when I get home.

---

### Post by qrm on 2006-10-31
usually it is a problem of cheap mice and way too high sensitivity. Lowering your sensitivity a lot might help, it will give you some effect (the twisting wont occur so often). There was a way to get out of the spin/twist but I cant remember how - used a cheap crappy led mouse about 2 years ago - it has never occurred with logitech mx series mice or razer products.

---

### Post by maxol on 2006-11-02
I have had this problem with dapper and edgy.

It seems to happen on some servers but not others and occurs as soon as I move the mouse when I'm in the limbo menu.

I'd love to be able to fix this!

---

### Post by Mickeysofine1972 on 2006-11-02
Hi

I used to get this happening on almost every game I connected to.

Since then I've reinstalled ubuntu a couple of time and also changed the way I install the program.

I usually do this:

```
sudo su
```
then type
```
sh <name of the file>.run
```

I find this installs better than installing into your home folder.

I also think that this may overcome permissions etc, which MIGHT, have something to do with the mouse problems.

Anyway, give that a try, you never know!

Mike

---

### Post by justinlb on 2006-11-03
I've just recently started to get this problem as well and chavo's suggestion worked for me so thanks a lot.

---


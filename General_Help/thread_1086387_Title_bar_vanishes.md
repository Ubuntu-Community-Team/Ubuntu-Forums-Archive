---
title: "Title bar vanishes"
date: 2009-03-04
forum: General Help
---

### Post by leutnant on 2009-03-04
Hi, here's my issue:

[[IMG]http://img133.imageshack.us/img133/8027/screenshot1.th.png[/IMG]](http://img133.imageshack.us/my.php?image=screenshot1.png)

How do I solve it? Do I mess around with xserver?

---

### Post by leutnant on 2009-03-04
Can anyone please help me :popcorn:?

---

### Post by theozzlives on 2009-03-04
You running compiz-fusion? If so, go to Add/Remove and search for compizconfig. Put a check next to Advanced Desktop Settings and click apply. Then go to System > preferances > Advanced desktop effects settings or Compizconfig Settings Manager (depending on the version). Make sure Window Borders is checked.

---

### Post by fooman on 2009-03-04
is that only when you are using firefox?

if so...

open firefox and press f11 *twice*.  that should get you to a normal firefox screen.

click on the unmaximize button.

close firefox,  then reopen firefox.

click the maximize button.

see if that fixes things for you.

---

### Post by barbolanero on 2009-03-04
That some thing started happening to me with Intrepid. I just press F11 twice and everythign is solved. Hope that helps.

---

### Post by leutnant on 2009-03-04
Thanks for the replies. The problem is not limited to just Firefox; it happens when I open Nautilus too. I know about F11 but this problem is pretty annoying and I just want to solve it once and for all.

Also, yes, I'm using compiz-fusion.

---

### Post by fooman on 2009-03-04
install compizconfig-settings-manager if it is not installed already.

in a terminal (applications > accessories > terminal),  type or copy/paste the following:

```
sudo apt-get install compizconfig-settings-manager
```

then press enter,  followed by your password.

after it installs,  open it in system > preferences > advanced desktop effects settings....find the "windows decorations" plugin and put a check next to it.

see if that fixes things.

---

### Post by leutnant on 2009-03-04
The windows decoration plugin was already checked. I unchecked it and then checked it again. It still didn't fix the problem. Any other suggestions?:popcorn:

---

### Post by leutnant on 2009-03-11
> **barbolanero said:**
> That some thing started happening to me with Intrepid. I just press F11 twice and everythign is solved. Hope that helps.

Did you do a fresh install or upgrade?

---

### Post by UbuntuNerd on 2009-03-11
are you also missing the top panel?

---

### Post by green69 on 2009-03-11
> **leutnant said:**
> The windows decoration plugin was already checked. I unchecked it and then checked it again. It still didn't fix the problem. Any other suggestions?:popcorn:

I have exactly the same problem using Intrepid (ab-initio installation) from a week. I can't solve it. The title bar of every kind of windows disappear when maximized, but top pannel is present. Decoration windows in compizconfig-settings-manager is already checked.

PLEASE CAN SOMEONE HELP US??

---

### Post by ercsv on 2009-03-11
i just got the same problem after changing resolution (new screen)

---

### Post by leutnant on 2009-03-16
I removed the top panel, btw, so that's not a problem.

I think that the least painful way (and only known way) to get rid of this problem is to just do a fresh install :popcorn:

---


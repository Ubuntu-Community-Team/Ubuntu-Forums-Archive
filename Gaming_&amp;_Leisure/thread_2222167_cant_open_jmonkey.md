---
title: "cant open jmonkey"
date: 2014-05-05
forum: Gaming &amp; Leisure
---

### Post by faneleshezitiger on 2014-05-05
hi all ubuntu users i nead healp with this game engine called jmonkey 

im on ubuntu 14.04 and i can not open it can you pls help me.[IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

---

### Post by oldrocker99 on 2014-05-05
It's a Java game, so do this:

```
sudo apt-get install openjdk-7
```

Then look at the jmonkey executable with a file manager and make sure in the Permissions tab that the "executable" box is ticked.

Then, right-click the executable and select "Open with OpenJDK"

You should be okay.

---

### Post by faneleshezitiger on 2014-06-04
it works tax man :D

---

### Post by oldrocker99 on 2014-06-04
Yelcome!

---

### Post by Peter_Solver on 2014-06-05
Good answer, oldrocker99.  Two days ago I attempted to open jMonkey Engine but with no luck. I did the same just like you taught here, it only took me a few minutes to navigate and find its source.

---

### Post by richmondster on 2014-06-15
thanks for info oldrocker999, my friend had this problem also. and i find this post, thanks.it works on other game too

---

### Post by oldrocker99 on 2014-06-15
The majority of Java games do **not** have the executable bit set, so either do as I said above or:

```
chmod +x [name of file]
```

And you're all welcome!

---


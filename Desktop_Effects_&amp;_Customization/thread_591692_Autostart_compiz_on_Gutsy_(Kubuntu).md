---
title: "Autostart compiz on Gutsy (Kubuntu)"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by kub-fu on 2007-10-25
Hi,

I installed and configured compiz, and it works beautifully, except I have to manually start it each time I turn on my PC.

How do you make it start automatically on boot?

Thanks!

---

### Post by rundee_f on 2007-10-25
Go to System > Preference > Sessions, and click Add, the type name : Compiz (or anything u want associated with compiz fusion) and type in the command box "compiz --replace"..

hope this helps u..

---

### Post by kub-fu on 2007-10-25
I think that's for GNOME right? I'm using Kubuntu, and hence KDE :-)

---

### Post by rundee_f on 2007-10-25
oops sorry... :D got no idea since i never use kde..

---

### Post by jaygo on 2007-10-26
Possible solutions:

If compiz is just a point & click, you can copy a link into /home/yourname/.kde/Autostart/

If compiz runs as a system service, I'm sure you can add it to startup, but I don't know how. :?

---

### Post by nickelby on 2007-10-26
Jaygo has given the heads up on starting compiz automatically when you run KDE.

IMHO, I don't think you should run it as a system service unless you want every user on your PC to have Compiz Fusion by default. I don't really recommend this since Compiz Fusion might cause issues such as corrupted OpenOffice in my case (needed to switch off CF in order to use OO).

---

### Post by kub-fu on 2007-10-26
Oh right, I did knew how to start something as a service, but the .kde thing is what I was looking for.

Thanks!

---


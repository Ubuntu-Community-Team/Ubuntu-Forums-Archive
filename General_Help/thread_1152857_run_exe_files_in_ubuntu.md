---
title: "run exe files in ubuntu"
date: 2009-05-08
forum: General Help
---

### Post by muctadir on 2009-05-08
how can i run exe files in ubuntu????

after installing can i use the application just like windows???

pls tell me in detail.
thank you..

---

### Post by N_Nick on 2009-05-08
Yes.

Yes.

What you need is an application called Wine.

Take a look at:   > [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by muctadir on 2009-05-08
thanksss.....

i am trying to apply the system...
lets see if it works......

---

### Post by 3rdalbum on 2009-05-08
> **muctadir said:**
> thanksss.....

i am trying to apply the system...
lets see if it works......

It works for some programs, but not a large percentage of Windows programs will work with it. Some will work with some tweaking.

Find Linux equivalents wherever possible.

---

### Post by Anxious Nut on 2009-05-08
you might be able to install/use Microsoft Office (there are always some addicts)

[see this ]("http://www.programmerfish.com/roffice-2007-in-linux")

---

### Post by Legace on 2009-05-08
> **Anxious Nut said:**
> you might be able to install/use Microsoft Office (there are always some addicts)

This is easier: [http://ubuntuforums.org/showthread.php?t=1122687](http://ubuntuforums.org/showthread.php?t=1122687)

---

### Post by luigi_mb on 2009-05-08
> **muctadir said:**
> how can i run exe files in ubuntu????

after installing can i use the application just like windows???

pls tell me in detail.
thank you..

Mono files also have the .exe extension. To run them, 

```


mono <filename>.exe


```

/luigi

---

### Post by muctadir on 2009-05-08
i am confused. anyone tell me exactly what to do?????????

---

### Post by cariboo on 2009-05-08
THe easiest way to install wine is to go to System-->ADministration-->Synaptic Package Manager and type wine in the quick search box, right-click wine and mark it for installation, then click apply.

---

### Post by merkourio on 2009-05-08
I tried to use Wine, but unfortunately, I didn't get good results..
I would rather suggest VirtualBox!

---

### Post by ibuclaw on 2009-05-08
> **merkourio said:**
> I tried to use Wine, but unfortunately, I didn't get good results..
I would rather suggest VirtualBox!

Only if you have a system that can handle the heavy duty efficiently.

Also, there is no 3D support in Virtual Machines...

---

### Post by surfed on 2009-05-08
> **tinivole said:**
> Only if you have a system that can handle the heavy duty efficiently.

Also, there is no 3D support in Virtual Machines...

There is OpenGl support but no DirectX.

---


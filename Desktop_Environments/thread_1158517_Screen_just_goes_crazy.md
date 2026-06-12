---
title: "Screen just goes crazy"
date: 2009-05-13
forum: Desktop Environments
---

### Post by kaotik2003 on 2009-05-13
Sometimes my screen, usually with firefox, openoffice, amsn, and specially Gimp goes crazy all black flickering, mouse pointer stops and than it stays all messed up with most desktop and application black till I pass the mouse over.

What can I do to stop this, it is really anoying.

[IMG]http://img219.imageshack.us/img219/5301/capturaecraprefernciasd.png[/IMG]

I had firefox opened on gnome-look and was changing themes, so look how my desktop become.

---

### Post by pro003 on 2009-05-13
what video card you have and what driver you're using?

---

### Post by kaotik2003 on 2009-05-13
> **pro003 said:**
> what video card you have and what driver you're using?

01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)

---

### Post by pro003 on 2009-05-14
here you go, install this [driver]("http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip")

---

### Post by kaotik2003 on 2009-05-14
> **pro003 said:**
> here you go, install this [driver]("http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip")

Thanks unfortunately the driver does not install in my ubuntu jaunty because of kernel

```
====== VIA UniChrome (Pro) Family Display Driver for Ubuntu 7.10 ======
====== Installation Program ======
Error:
  This driver package is only support the default kernel
  "2.6.22-14-generic" for Ubuntu 7.10
```

---

### Post by kaotik2003 on 2009-05-20
I still haven't found the solution to my problem.

I start to think it has something to do with my mouse controller, since last time it happened my mouse froze.

Sometimes mouse starts to get very slow, I'm still not sure what cause this, it happens specially in office applications, like Open Office and GIMP, amsn too.

I leave you another pic of what happens, sometimes all 10 seconds, forcing me to change desktops so tha I'm able to see it again.

If this coninues I will be forced to go back to windows unfortunatly, sinc I can't work like this. 

[IMG]http://img219.imageshack.us/img219/5909/capturaecra1.png[/IMG]

---

### Post by kaotik2003 on 2009-05-26
Well, I found the solution to my problem.

After installing the biggest virus in the Computer World, with Windows as a name, after 3 days I went back to Ubuntu, BUT, this time with Intrepid IBEX.

My screen problems are off, so I can only assume that there are bugs with Jaunty 9.04.

My brother, with a Intel Chipset and an Intel GPU, has also a problem with Jaunty, anytime he watches a movie, the image slowdowns, and almost stops, he will to downgrade to 8.10.

---

### Post by kaotik2003 on 2009-05-29
For who may want it:

> **I have redraw mistakes on the desktop and in various applications. Lines, icons, and sliders disappear; sometimes they reappear when I move the mouse over it or when I move a window over it and back.** 
The redraw-issues can be worked around by trying "True", "False", "On", "Off" as values of the "EnableAGPDMA" option of the "Device" section in /etc/xorg.conf 
    ```
Section "Device"
        Driver    "openchrome"
        Option    "EnableAGPDMA"    "True"
    EndSection
```

---


---
title: "Feisty: Where is my spinning cube desktop?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by jrusso2 on 2007-04-20
I installed Feisty.  Enabled the nvidia driver and desktops effects.  I got the floppy windows and no spinning cube?

How do I get my spinning cube?  I tried switching desktops but nothing happens I can't even switch desktops.

Also I don't even have floppy windows in KDE just gnome.

Thanks

Jeanette

---

### Post by Fillibuster on 2007-04-20
A ton of people had this problem, myself included.  Go to a terminal and open your gconfig.  Then go to apps>compiz>general>screen0>and set your hsize to 4...hope this helps!

---

### Post by Rizlaw on 2007-04-20
I posted the same problem. You can find your answer here:

[http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html](http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html)

Also, make sure you install "gnome-compiz-manager" using the Synaptic Package Manager. After installing, go to SYSTEM > PREFERENCES > GL DESKTOP > WORKSPACES and make "Number of Viewports" = 4.:)

---

### Post by emrextreme on 2007-04-21
> **Rizlaw said:**
> I posted the same problem. You can find your answer here:

[http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html](http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html)

Also, make sure you install "gnome-compiz-manager" using the Synaptic Package Manager. After installing, go to SYSTEM > PREFERENCES > GL DESKTOP > WORKSPACES and make "Number of Viewports" = 4.:)

That did solve the problem. Tnx.

---

### Post by braveerudite on 2007-04-21
> **Rizlaw said:**
> I posted the same problem. You can find your answer here:

[http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html](http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html)

Also, make sure you install "gnome-compiz-manager" using the Synaptic Package Manager. After installing, go to SYSTEM > PREFERENCES > GL DESKTOP > WORKSPACES and make "Number of Viewports" = 4.:)

That guide is confusing, and is for Debian

---

### Post by orange2k on 2007-04-21
Its actually quite simple...

I found the answer here: [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)

---

### Post by jrusso2 on 2007-04-23
> **orange2k said:**
> Its actually quite simple...

I found the answer here: [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)


That works thanks for the help.

Jeanette

---


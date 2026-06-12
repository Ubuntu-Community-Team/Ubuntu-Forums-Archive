---
title: "Eclipse not working"
date: 2009-03-07
forum: General Help
---

### Post by mavix on 2009-03-07
I recently downloaded Eclipse, because after working for a few days in Netbeans' GUI editor I got so frustrated I that I was ready to kick my computer quite a few times. So I got the tar.gz archive, downloaded it, extracted it and ran it. It displayed it's splash screen and asked me where I wanted it to save it's workspace. After that, it loads again for a few seconds, then the splash screen disappears and I am presented with... an empty dialog box!
No text, and no buttons. If I try to close the window nothing happens. So I re-ran eclipse through the terminal, and this is what it shows when the dialog box appears:

```
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkMessageDialog::use-separator' of type `gboolean' from rc file value "((GString*) 0x80c1c30)" of type `GString'
```

I searched for it on Google, but it couldn't find anything. I have tried it on both the Sun JDK and the OpenJDK, and they both show the same message.

Any ideas?

---

### Post by Xiong Chiamiov on 2009-03-07
Install it [from the repos](http://www.psychocats.net/ubuntu/installingsoftware) instead of from their site.

---

### Post by kaivalagi on 2009-03-07
The one in the repos is too old...and slow

Did you download the correct architecture version?

Ganymede is working fine on 8.10 for me, I had to mess about with my java settings but they should have any effect like you're seeing...

Alternatively, you could try the OLD repo version, following this guide: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by mavix on 2009-03-07
> **Xiong Chiamiov said:**
> Install it [from the repos](http://www.psychocats.net/ubuntu/installingsoftware) instead of from their site.

No can do. I don't have ADSL on my PC, so I downloaded the archive from a different one.

---


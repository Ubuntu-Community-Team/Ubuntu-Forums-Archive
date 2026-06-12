---
title: "something installed konqueror; How to uninstall it?"
date: 2009-12-30
forum: Desktop Environments
---

### Post by dr_alejandro on 2009-12-30
Somehow I have konqueror installed in my machine (I'm running Ubuntu 9.10 32 bit on a D610 Dell laptop). I did not put it there intentionally. I suspect it was when I installed showFoto from the Ubuntu Software Center. I was simply looking for an alternative to the GIMP, but I decided to take out showFoto and stick to the GIMP.

After I installed showFoto several other things were installed as well (Dolphin, digiKam, Konqueror and I think Kipi Plugins). I was able to go back to Ubuntu Software Center and uninstall showFoto, Dolphin, digiKam and Kipi Plugins, but Konqueror is not listed. So I can't take it out using Ubuntu Software Center.

Is there anything else that showFoto installed that i don't know of? I don't need Konqueror, it is not causing any problems but I don't want it in the machine, how can I uninstall it?

---

### Post by 3Miro on 2009-12-30
Sounds like you installed kubuntu desktop somehow. Anything that is no listed in Ubuntu Software Center is listed in Synaptic Package Manager (System -> Administration -> Synaptic Package Manager).

Also, you have a lot of QT libraries installed that are the underlying framework of KDE, you probably do not need many of those, but it is hard to say which ones.

---

### Post by dr_alejandro on 2009-12-30
Thank you, I removed Konqueror using Synaptic Package Manager, then I ran Computer Janitor and it showed all the files that were unused and took them out Computer Janitor rocks! So far no problems (it was 5 min ago though, so hopefully nothing will crash).

Is there a way to see what was installed when and by what?

I was looking at Log File Viewer but I did not understand anything there.

---


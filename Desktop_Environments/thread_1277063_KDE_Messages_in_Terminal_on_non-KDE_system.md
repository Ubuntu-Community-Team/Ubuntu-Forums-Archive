---
title: "KDE Messages in Terminal on non-KDE system"
date: 2009-09-27
forum: Desktop Environments
---

### Post by Mhoram on 2009-09-27
I'm running compiz and xfce on Xubuntu, so I don't have the full KDE suite installed, but now and then I run a KDE-based app like k9copy.  They run fine, but after I close the app, I get a message like this every minute or so in the terminal I ran the app in:

    init4: preparing to launch /usr/bin/kbuildsycoca4                  <unknown program name>(14402)/ KStartupInfo::createNewStartupId: creating:  "bannor;1254102568;423500;14402_TIME0" : "unnamed app"
                   kbuildsycoca4 running...

The only way I've found to stop them is to kill kded4 and kdeinit4.  Is there anything I can do to get these processes to shut down gracefully when the app is done using them, or at least get them to stop telling me what they're doing?

Thanks!

---

### Post by clonne4crw on 2009-09-27
You're running a KDE app, with installed the minimal KDE enviroment file and programs with it. If you want to keep running your KDE program, leave these alone and understand that its not their fault that they're KDE apps trapped in a XFCE envoriment. They're just trying to do what they're supposed to do. 

:popcorn:

---

### Post by Mhoram on 2009-09-28
I'm not blaming KDE; I realize those programs are necessary to support KDE apps.  I'd just like to get rid of the repeating console messages, or find a way to get those programs to shut back down when I'm done with them, since I might not need them again for days or weeks and they do take some resources.

I could run k9copy from a script wrapper that does 'killall kded4 kdeinit4' at the end, but that seems a little harsh.

---

### Post by clonne4crw on 2009-09-28
> **Mhoram said:**
> I could run k9copy from a script wrapper that does 'killall kded4 kdeinit4' at the end, but that seems a little harsh.

But it will work.

---


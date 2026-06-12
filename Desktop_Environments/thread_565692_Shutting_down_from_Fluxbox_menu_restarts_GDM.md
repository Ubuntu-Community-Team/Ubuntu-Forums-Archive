---
title: "Shutting down from Fluxbox menu restarts GDM"
date: 2007-10-02
forum: Desktop Environments
---

### Post by justinjacobs on 2007-10-02
Hi everyone! Last night, I tried setting up Fluxbox on my Ubuntu Feisty installation. So far, I really like it. But I've run into one problem. I've added an entry for **sudo shutdown -h now** to my Fluxbox menu. When I run this from the menu, it behaves normally, terminating my open applications. However, the system DOESN'T shut down. It just restarts Xorg and shows the GDM login screen.

I think the reason I'm having this problem is because the shutdown process is a child of Fluxbox, and therefore Xorg, so it kills itself before it can finish. If this is the case, is there anyway to execute the shutdown command as a process separate from Fluxbox?

I should also note that when I run Xterm from the Fluxbox menu, and then enter the shutdown command in that Xterm window, it works perfectly.

---

### Post by RedSquirrel on 2007-10-02
Have a look at the menu HOWTO in my signature. I have a section in it that describes how to shutdown/reboot from the menu. It might help you.

---

### Post by justinjacobs on 2007-10-02
> **RedSquirrel said:**
> Have a look at the menu HOWTO in my signature. I have a section in it that describes how to shutdown/reboot from the menu. It might help you.

I actually followed your guide while I was setting up Fluxbox. I think all I have to do is get the shutdown command to not run as a child process of Fluxbox.

---

### Post by justinjacobs on 2007-10-02
Nevermind, I just found a solution! I just needed to start it as a background process. So the line is now:
```
[exec] (Shutdown) {sudo /sbin/shutdown -h now &}
```

Now I can enjoy me some Fluxbox! \\:D/

---


---
title: "Gnome Taskbar Crash"
date: 2006-12-08
forum: Desktop Environments
---

### Post by studiesrule on 2006-12-08
The Gnome taskbar spontaneously crashes on startup. It opens the bug buddy popup, and displays a lot of log (which I'm not able to comprehend). It basically says its a gtk error. The taskbars don't work. On closing the bug-buddy window, it refreshes the screen and then the taskbar crashes again. I'm using Edgy with the latest updates. I didn't face any problems on upgrading, and I don't think that that is the problem.
I believe the error originated when I was using PyPE (python editor, uses scintilla and gtk). I ran a particular script, and due to some internal problem with the editor, it failed to run (as in didn't even start running), and went into a loop. I force quit the window, and the taskbar crashed.

I'd like to ask if there is any 'reinstall' feature, because I have a lot of important data in my home dir. I don't want to reinstall because of it. I also don't really have enough extra space to back it up (well, linux hasn't ever crashed on me. This really doesn't count). I'm using my windows now (ugh...), and I'd like to know if there is any good tool to access my ext3 partions from windows?

---

### Post by temcat on 2006-12-08
You could try deleting the following directories from your home directory:

.gconf
.gconfd
.gnome
.gnome2
.gnome2_private

You will lose your Gnome settings, as well as settings for some other programs that use GConf, but at least you will not have to reinstall the entire system.

---

### Post by temcat on 2006-12-08
<Deleted by me>

---

### Post by studiesrule on 2006-12-09
Ok, I tried that, It didn't work. For the heck of it I installed Kubuntu, and now am fine. Thanks for the help though

---


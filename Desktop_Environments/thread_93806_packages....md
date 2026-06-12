---
title: "packages..."
date: 2005-11-22
forum: Desktop Environments
---

### Post by xelink on 2005-11-22
every so often when I try to do something it requests that I have packages. I have none. Any suggestions? I only used one defualt disc(they mailed it), shoudl I have DLed another and used it during install? anythign I can/should do?

---

### Post by wylfing on 2005-11-22
I am not entirely sure what your problem is, but I am going to assume it's this: [COLOR="SlateGray"]you want to install something but you can't find it in synaptic[/COLOR]. Is that right?

---

### Post by xelink on 2005-11-22
pretty much... can't install wine... that's the main thing I want right now.

---

### Post by dodongo on 2005-11-22
Go [here]("http://ubuntuforums.org/showthread.php?t=40291")
 and add the appropriate lines to sources.list -- make sure to choose the appropriate version of Ubuntu.  After you "refresh" in Synaptic, you should be able to grab the latest, greatest Wine release!

---

### Post by xelink on 2005-11-22
tried all that and just ran the stuff Wine told me to in sysnapse and it seems to have worked. I may have doen something wrong before. THank you all so very much.

nwo to see fi I can get counter strike running.

---

### Post by aysiu on 2005-11-22
Once you've installed Wine, it doesn't have a launcher because it's not an independent program. It's a program that launches other programs. For example, if I want to launch Filezilla, I use the command ```
wine "z:\home\username\.wine\c_drive\Program Files\Filezilla\Filezilla.exe"
``` Actually, I don't type that command--I made it into a launcher and a keyboard shortcut. I could also navigate to the Filezilla.exe and double-click it. That will launch Wine, too.

---

